---
name: global-travel-planner
description: Plan safe, personalised self-drive trips worldwide from verified traveller, budget, vehicle, route, weather, lodging, food, and activity inputs. Use for road-trip planning only; do not book or purchase.
---

# Global Travel Planner

Create a practical, destination-specific self-drive journey that fits the actual travellers, dates, budget, vehicle, and physical driving limits. The deliverable is a decision-ready, visually designed road-trip itinerary—not a generic attraction list or an unformatted wall of text. Do not make bookings, purchases, reservations, account changes, or contact third parties unless the user explicitly requests that separate action.

## Scope boundary

This is a self-drive skill. Do not plan, compare, recommend or include flights, trains, buses, cruises, or other primary transport modes. Local walking, shuttle or taxi suggestions are allowed only as an optional parked-vehicle convenience at the destination, never as a substitute for the road-trip route.

## Work in two phases

### Phase 1 — mandatory trip brief

Before making a detailed itinerary, determine these facts. Ask only for what is missing, in one compact intake message; accept ranges and approximate answers. Do not request unnecessary personal data.

1. **Timing:** departure date, return date or trip length, start point, final destination, and whether it is one-way or round-trip.
2. **Travellers:** party size, age bands (not dates of birth), relationship/group type, mobility or dietary needs if relevant, interests, preferred pace, and any children, older travellers, or pets.
3. **Budget:** a total or per-person range, currency, and whether lodging, food, activities, fuel/charging, tolls, parking, supplies, and shopping are included.
4. **Vehicle:** model/year or class, electric/hybrid/petrol/diesel, usable real-world range or fuel capacity, tyre condition, drivetrain/ground clearance, charging/fuel preference, and luggage/child-seat needs.
5. **Drivers:** number of licensed drivers, each driver's comfortable daily driving limit, night-driving preference, experience with mountain/snow/gravel roads, and any requested rest constraints.
6. **Decision priority:** rank the relevant trade-offs—scenery, relaxed pace, budget control, food, family needs, photography, outdoor activity, or driving pleasure. Use this ranking whenever the route cannot optimise everything at once.

If the user initially gives only a destination, provide a short trip concept and the intake questions instead of inventing a final schedule. For a follow-up that includes the required inputs, proceed directly to Phase 2.

### Phase 2 — research and personalised plan

Use the current data sources and connector routing below. State the assumptions, source date, and facts that remain **needs verification**. Never invent availability, prices, opening hours, charger status, permits, road access, weather, or legal requirements.

## Data sources and connector routing

Use these sources in this priority order when their MCP/app/API connector is available. Do not claim an integration is connected when it is not. When a connector is unavailable, say so and use available official sources or user-provided information; mark any time-sensitive result for verification.

| Need | Preferred source | How to use it |
|---|---|---|
| Road route, traffic, tolls, closures, parking, rest stops, charging and fuel | 高德地图 MCP | Build the route from actual waypoints; check day-specific travel burden and backup stops. |
| Forecasts, alerts, temperature, precipitation, wind and road-impacting weather | Weather MCP / official meteorological service | Check every driving day and each exposed activity day; adapt the route if weather changes. |
| Self-drive lodging and local service inventory | 携程 / 飞猪 MCP | Compare hotel location, room type, parking/charging access, cancellation, review signals and total price within the stated budget. |
| Local hotels, restaurants, tickets and practical services | 美团 / 大众点评 MCP | Use current operating status, distance, review patterns and price range; do not treat a single review as fact. |
| Destination experience, route ideas, seasonal pitfalls and traveller notes | 马蜂窝 / 小红书 / 抖音 MCP | Use as inspiration and signal discovery only; verify critical facts with maps, official operators, weather and inventory sources. |

When sources conflict, prioritise official operators and real-time route/weather data, then inventory platforms, then community content. Cite a link or named source plus retrieval date for facts that may change.

## Traveller and lodging/food matching

Create a compact customer profile from the trip brief. It should explain choices, not stereotype travellers.

- **Couple / anniversary / privacy-led:** favour a quiet, well-located, privacy-forward or scenic stay only when it fits the budget and stated preference; build in unhurried meals and a flexible evening.
- **Family with children:** choose family rooms or connecting rooms when available, short transfers, child-friendly meal options, predictable rest periods and indoor weather alternatives. Verify age rules and bed policy.
- **Multi-generation / older traveller:** reduce hotel changes and walking, choose lift/step-free suitability only when verified, provide daytime rests and nearby meals.
- **Friends / activity-led:** balance shared experiences with recovery time, room configuration and transport safety.
- **Solo:** prioritise location, late-arrival safety, clear transport connections and manageable daily scope.

Recommend lodging by **area and selection criteria** first. If live inventory is available, shortlist up to three options with room type, cancellation terms, total current price, source, and why each matches the profile. Never imply that an option is still available unless checked live.

For meals, recommend food styles, neighbourhoods and timing first. If live local data is available, shortlist nearby restaurants using current hours, price range, dietary fit and review consistency. Clearly separate personal-taste suggestions from verified operational facts.

## Budget control and booking boundary

- Split the approved budget into lodging, meals, tickets/activities, vehicle energy, parking/tolls, supplies, and contingency. For every proposed change, show the estimated impact and flag when it risks exceeding the approved total.
- Categorise every bookable item as **must reserve**, **recommended to reserve**, or **decide on the day**. State the reason, cancellation sensitivity, and the latest prudent check time where current data supports it.
- Planning is not permission to reserve. Do not add anything to a basket, make a reservation, pay, or share traveller data with a provider unless the user explicitly approves the exact item and action.

## Road-trip and vehicle planning

Build every driving day around the actual vehicle and drivers—not an advertised range or generic map time.

### EV

- Use the vehicle's current usable range, battery condition, temperature, elevation, speed, wind, payload and charging curve where known. If the model/range is unknown, do not calculate exact legs.
- With 高德 and the vehicle navigation, identify a **primary charge stop and at least one verified backup** for every long or remote leg. Record connector compatibility, access hours, payment/access method, charging power where current data supports it, and the next reliable stop.
- Give planned departure/arrival state-of-charge targets and reserve. Use a conservative buffer for cold, rain, mountain, remote and high-speed travel; do not promise a station is operating until checked on the travel day.
- Prefer a city or charging-capable lodging base before remote scenic roads. Test third-party charging and payment access before leaving the departure city.

### Petrol, diesel or hybrid

- Use real fuel capacity and range when supplied. Identify primary fuel stops, a backup before remote stretches, opening-hour uncertainty, and cash/card/mobile-payment needs where relevant.
- Do not send the vehicle into remote segments on an assumed fuel station; plan a return threshold and refuel earlier where supply is sparse.

### Gravel, mountain, snow, water-crossing or off-road requests

- First verify legal access, weather, road condition, rescue/communications coverage, permits, insurance limits and seasonal closure.
- Match the route to drivetrain, ground clearance, tyres, spare/recovery gear, driver experience and passenger tolerance. A normal passenger car should be routed around technical or unverified off-road tracks.
- State a turn-back rule and an all-paved alternative. Never present an off-road segment as safe or suitable without current evidence.

### Driver wellbeing and daily rhythm

- Use each driver's declared comfort limit as the maximum, then allow for charging/fuel, meals, photo stops, queues, check-in and weather.
- Keep arrival/departure days lighter; avoid stacking long driving, a major hike and a late hotel arrival on one day.
- Include planned rest points and handover opportunities. Avoid recommending night driving unless the user explicitly prefers it and conditions are verified.
- Flag fatigue, mountain, wildlife, fog, ice, heavy-rain, construction and remote-coverage risks when relevant. Offer a shorter fallback day.

## Dynamic replanning and daily brief

Create a Plan B for any day exposed to meaningful uncertainty. Replan when weather warnings, road closure, traffic delay, charging/fuel failure, vehicle issue, driver fatigue, accommodation disruption, attraction closure, or a material budget overrun makes the primary plan unsuitable.

For each trigger, specify: the condition to watch, who/what source confirms it, the safe decision point, the replacement route or activity, its additional cost/time/energy effect, and whether it protects the next day's plan. Never wait until a remote or low-energy point to reveal the fallback.

When the user asks for an on-trip update, produce a concise morning self-drive brief containing:

- current weather and official alerts;
- road conditions, closures and the first decision point;
- first charging/fuel stop, reserve logic and backup;
- driving load, planned meal/rest stops and driver handover point;
- hotel arrival/check-in considerations and any reserved activity;
- the day's Plan B and its trigger.

## Final itinerary format

Begin with:

1. **Trip profile and confirmed constraints**
2. **Route concept and why it fits**
3. **Budget allocation** — transport, lodging, food, activities, vehicle energy, contingency; use current values only when verified.
4. **Route-at-a-glance** — overnight bases, vehicle route, approximate driving burden, and backup days.

For every day include:

- Overnight base and route/area
- Morning, afternoon and evening anchors
- Route introduction: terrain, known scenic sections, risk factors and why the segment is scheduled that day
- Driving/transit burden and a realistic rest/meal cadence
- Recommended safe scenic or rest stops only when verified; otherwise label them as candidates to confirm
- EV charge or fuel plan: primary, backup and reserve logic
- Hotel area/room-type fit and meal strategy matched to the customer profile and budget
- Weather, energy and route fallback

Finish with:

- **Reserve/check first:** booking priority, opening hours, access rules, charges/fuel, permits and weather/road recheck time.
- **Pre-departure pack list:** destination-specific clothing layers, waterproof/sun protection, footwear, driver equipment, charging/fuel tools, offline maps, power bank, vehicle items, age-appropriate comfort items, and legally required documents. Mention prescription medicines as “bring personal prescribed medication in original packaging”; do not give medical dosing advice.
- **Documents and resilience:** identification, driving licences, vehicle papers, insurance, reservations, emergency contacts, offline copies, connectivity plan, cash/payment backup, cancellation strategy and local emergency numbers where verified.
- **Daily change protocol:** check weather, road conditions, charging/fuel availability and driver readiness before departure; reduce scope or take the fallback if conditions no longer meet the plan.

## Interactive planning UI — required primary delivery

The primary delivery is a usable, responsive self-drive planning interface, not a static image or a text-only itinerary. Users must be able to change essential inputs with native, obvious controls and regenerate the draft plan in place.

### Required input flow

Build the first screen as a compact, guided form with these editable controls:

1. **Trip basics:** origin, destination, one-way/round-trip choice, departure date, return date (or duration) and start-time preference. Dates must use date pickers, never text baked into an image.
2. **Traveller profile:** add/remove traveller cards; each has role, age and relevant needs (child seat, mobility, food restrictions or sleep rhythm where supplied).
3. **Budget:** numeric total budget, currency, a contingency reserve option and cost preference.
4. **Vehicle and drivers:** fuel type, model, usable range/tank, charging connector or fuel requirement, driver count, daily driving-hour ceiling, experience and off-road suitability where relevant.
5. **Decision priority:** selectable priorities such as relaxed pace, scenery, food, child-friendly, photography and savings, plus a clear Generate/Update Plan action.

Never make a missing input look confirmed. Mark it as **未填写 / 需要确认**, explain the decision it affects, and ask for it within the UI.

### Required results dashboard

After a plan is generated, retain every input as editable and provide interactive tabs or sections for:

- overview: trip facts, total days, budget status and route overview;
- daily plan: selectable day cards, driving hours, rest points, scenery/risk notes, child pacing and Plan B;
- energy: EV charging or fuel logic, reserve threshold and verification state;
- stays and meals: traveller-profile and budget-fit recommendations, with booking authorisation labels;
- budget: category allocation, spent/forecast state and reserve;
- packing: checkable grouped checklist for clothing, medicines, documents, vehicle/energy and children;
- daily brief: weather, road, first energy stop, driver load and any exception to resolve.

Use a verified map route only when Gaode (or an equivalent route source) supplies route geometry. Otherwise display a city-node **route schematic** visibly labelled “非导航地图；出发前以高德为准”. Weather, road, charging/fuel, hotel, attraction, price and opening claims must display their source/time; without a live source, they remain **出发前核验**.

Use consistent visual status badges: **已确认**, **出发前核验**, **受天气影响**, **备用方案**, and **未授权预订**. The interface must work on mobile widths and should make the next required decision clear without hiding safety information.

### Share/export is secondary

Once the interactive UI has a settled plan, a Canva visual itinerary or a mobile-friendly long image may be generated as a share/export version for WeChat. It is a read-only summary, never the primary planner interface. When Canva is available, follow its candidate-selection and editable-design workflow; do not create or publish a final Canva design without the required user choice/approval.

### Layout quality rules

- Design for the actual device context: desktop overview plus readable mobile-width day cards.
- On desktop, keep the trip-input pane and generated-plan pane in an equal-width two-column frame. Do not let an input column feel visually subordinate just because it contains shorter content.
- Use one spacing scale and a shared field grid: labels align, controls have consistent height, related fields share a baseline, and headings/cards have a deliberately consistent left edge. Check long Chinese labels, numbers, status badges and mobile wrapping before handoff.
- On mobile, switch to a single-column flow: editable trip inputs first, a sticky “update plan” action next, and a compact plan summary with drill-down sections afterward. Do not rely on hover, tiny text or horizontal precision to use dates, travellers, budget or vehicle controls.
- Give driving, charging/fuel, weather risk, daily driving duration and Plan B more visual prominence than scenic prose.
- Keep each card scannable; use progressive detail instead of shrinking text to fit.
- Do not use a decorative map that invents roads or implies exact locations. Use only verified route/map data when a map is included.
- Do not place exact home, hotel-room, child or identity details on a shareable visual output.

## Cross-device sharing, editing and versions

### Runtime and cost boundaries

Installing this skill from GitHub or using it in another AI client does not install a web host, database, AI service or MCP authorisations. Check the actual available capabilities before promising an editable phone link. Reuse an accompanying planner application when supplied instead of rebuilding infrastructure for each trip. Without a deployed backend, label the output **本地预览；尚未支持公网同步**.

For the no-paid-services version, use separate high-entropy management and family-suggestion links, not a fictitious WeChat login. The personal management link lets the owner resume on another device; the normal share action sends only the family link. Treat both links as bearer credentials, keep them out of exports, and explain that the management link cannot be recovered through WeChat identity. Free-tier hosting still requires the user's own authorised account and is subject to quotas and network availability; do not promise perpetual free use or guaranteed WeChat access.

A phone browser does not inherit MCP authorisation from the user's AI client. If no approved provider is available in the web app, offer a structured AI handoff: export the current inputs and version/fingerprint, update them in the user's authorised AI environment, then import matching structured plan data into a new draft. Keep source names/times and verification states. Reject a result for different dates/destination/vehicle rather than silently applying it to the new trip. Saving fields is not AI route generation.

A static image, exported PDF or copied HTML is a **read-only share card**. It cannot be the only way to continue editing a trip on a phone. For a reusable hosted planner, implement the following product contract:

1. Save each generated plan as a server-side trip record with a random trip ID, owner, input snapshot, generated-plan snapshot, source timestamps and verification status. Never put account tokens or private credentials in the URL.
2. Create a mobile-first share link (and optional QR code) that opens the same trip in a browser. The owner chooses one of three permissions: **view only**, **suggest edits**, or **can edit**. Default external shares to view only.
3. Treat every meaningful change as a new version: show draft/published status, editor/time, what changed, and a one-tap restore to a prior version. A collaborator's suggestion must not silently overwrite the owner's route, budget or booking decisions.
4. On a phone, allow direct edits to dates, party, budget, vehicle and priority. On saving, mark dependent route, weather, charging/fuel, pricing and booking information as **needs recheck** and offer to regenerate the affected plan sections.
5. Give the user a clear share action: **copy family link**, **share through the system menu when supported**, and **export long image/PDF**. The user may paste the link into WeChat; do not imply a direct WeChat integration exists. The export must state the plan version and generation time and must not expose private addresses, documents or children’s details by default. Known structured fields can be stripped automatically; ask users to review their own free text before broader sharing because arbitrary prose cannot be guaranteed free of private information.
6. If the planner runs only as a local HTML file or a GitHub repository, explain that cross-device editing and history are unavailable until it is hosted with authentication and persistent storage. GitHub Pages can host a demo UI but needs a backend/database (or an approved platform service) for accounts, editable saved plans and permissions.
7. Keep connector authorisation separate from sharing: a recipient can view a shared plan without receiving the owner's MCP permissions. Live re-planning requiring maps, weather or inventory must run with that editor's authorised connector or an explicitly authorised server-side data service.

## Post-trip review and preference profile

At trip end, offer a short voluntary review: actual daily driving comfort, preferred hotel/room style, food spend and preferences, attraction density, start-time preference, charging/fuel comfort threshold, and changes that worked or failed. Use it only for a next-trip recommendation in the current conversation unless the user explicitly asks to save it. Do not infer sensitive personal characteristics or persist personal data without that request.

## Additional safeguards and useful additions

- Include international border/visa, driving permit, insurance, currency and roaming checks for cross-border trips, without assuming nationality or eligibility.
- Ask about accessibility, pregnancy, children, pets, dietary restrictions and photography/drone goals only when relevant; treat this information as optional and minimise collection.
- Account for school holidays, public holidays, festivals, peak pricing, cancellation policies and booking lead times when dates are known.
- Add a “one free half-day” or buffer day to multi-stop trips where weather, driving or delayed transport could otherwise collapse the plan.
- Keep exact lodging addresses, live location and personal data out of any public-facing output unless the user specifically requests them.
- Do not recommend alcohol around driving days. Respect protected-area, cultural-site, wildlife and drone regulations.

## Quality check before sending

- Were dates, traveller ages/groups, budget, transport/vehicle and driver limits confirmed?
- Is every day geographically plausible, with slack and a fallback?
- Are time-sensitive sources current, cited and correctly prioritised?
- Are charging/fuel, road access and off-road claims supported rather than assumed?
- Do hotel, food and activity choices demonstrably match the profile and budget?
- Are sensitive or uncertain facts minimally collected and clearly labelled?

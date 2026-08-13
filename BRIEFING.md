# Data center cooling: discharge and chemicals
### A short reference for the questions coming in at MCEA

Companion to the Cooling Atlas 3D exhibit. Every figure below is sourced; the exhibit's
info panels carry the same numbers with clickable citations. Where the evidence is thin,
this says so.

---

## 1. The question that decides every other question: which cooling type?

Public discussion routinely treats "data center cooling" as one thing. It is at least
four things with completely different water behavior. Nearly every confused claim traces
back to applying one type's facts to another.

| System | Water consumed | Liquid discharge | How often |
|---|---|---|---|
| **Open evaporative tower** | High — the working water itself evaporates | Blowdown, continuous | Every day, all day |
| **Closed-circuit (fluid) cooler** | Moderate — a separate spray circuit evaporates | Blowdown from the spray sump only | Continuous while spraying |
| **Adiabatic** | Low — water wets pads to pre-cool *air* | Little or none | Pad flush only; seasonal |
| **Dry cooler / air-cooled** | None | None | — |
| **Closed loop (direct-to-chip, immersion)** | Effectively none in operation | Episodic: commissioning flush, repairs | Years apart |

The distinction that matters most: in an **open tower**, the water being cooled is itself
exposed to the air, evaporates, and concentrates its dissolved minerals — which is *why*
it must be bled off continuously. In an **adiabatic** unit, the process fluid stays sealed
inside a coil; water only wets the incoming air. Same "evaporative cooling" label in
casual usage; entirely different discharge consequences.

**Adiabatic vs. hybrid — are they the same thing?** No, and they aren't opposites either;
they describe different axes.

- **Adiabatic** names a *mechanism*: evaporating water into the incoming airstream
  (through wetted pads or a fine spray) to lower its temperature before it reaches a dry
  coil. The process fluid never touches the water.
- **Hybrid** names a *control strategy or configuration*: a unit that runs fully dry when
  ambient conditions allow and switches to wetted operation for hot hours — or one casing
  containing both a dry coil section and an evaporative section (e.g. BAC HXV-class
  closed-circuit coolers).

Most adiabatic coolers in service are operated as hybrids: dry all winter, pads wetted
only during summer peaks. But a hybrid need not be adiabatic — a dry-plus-evaporative
closed-circuit cooler is a hybrid whose wet section sprays a coil, not the air. Switchover
setpoints (commonly somewhere around 24–30 °C dry bulb) are site-configured; there is no
universal number. Bay 3 of the exhibit shows this directly: the adiabatic unit cycles
between wet and dry mode on a visible seasonal loop, next to a purely dry cooler that never
uses water at all.

---

## 2. "How often are closed-loop systems discharged?"

**Short answer: episodically, not on a schedule — and the volumes are small.**

A properly built closed loop is filled once and holds a fixed inventory:

- **Once at commissioning.** New piping is flushed and chemically cleaned. That flush
  water — one to a few loop volumes — is disposed of as wastewater. This is the single
  largest routine discharge event in the loop's life.
- **Essentially nothing during normal operation.** A tight loop loses less than 5% of its
  volume per year. Makeup is added after a leak or a repair, not on a cycle.
- **Repairs drain only the isolated section**, years apart. Maintenance practice is
  explicitly built to *avoid* draining: inhibitors are re-dosed, not replaced with the
  water. One institutional protocol (University of Michigan) requires lab analysis with
  three weeks' lead time before a loop drain may go to sewer, and captures emergency
  repair water in totes for return to the loop.
- **Full drains** are reserved for major contamination, retrofit, or decommissioning.

**The scale contrast is the actual answer.** A 1 MW direct-to-chip CDU loop holds roughly
21–31 gallons. Facility loops run to thousands or tens of thousands of gallons (estimate —
rule-of-thumb, not a sourced figure). Meanwhile a single 1,000-ton cooling tower at three
cycles of concentration discharges **20,000–40,000 gallons of blowdown per day, every
day.** A closed loop's entire lifetime discharge is on the order of days' worth of one
evaporative campus's routine blowdown.

**Caveat worth stating plainly:** no authoritative "every N years" statistic for drain
frequency exists. Primary sources — vendor O&M documentation, the Veolia water treatment
handbook, NIH facilities bulletins — agree on the episodic pattern, but nobody publishes
a frequency distribution. If someone quotes you a specific interval, ask for the source.

*Sources: Veolia Water Treatment Handbook ch. 32; NIH ORF closed-loop technical bulletin;
UMich EHS discharge standards; LiquidStack CDU-1MW datasheet; RPM Water blowdown figures.*

---

## 3. What is actually in cooling tower blowdown

Two categories: concentrated source-water minerals, and treatment-chemical residues.

**Minerals.** Whatever came in with the makeup water, multiplied by the cycles of
concentration. At 3–8 cycles on typical municipal water, blowdown TDS commonly lands near
1,000–3,000+ mg/L (estimate), with proportionally concentrated chlorides, sulfate,
calcium, magnesium, and silica.

**Chemicals**, at typical residual concentrations:

- Free chlorine ~0.5–1 ppm (continuous hypochlorite or bromine dosing)
- Non-oxidizing biocides — isothiazolinone, glutaraldehyde, DBNPA — periodic slug doses
- Phosphonate scale inhibitors (HEDP/PBTC) ~1.5–5 ppm
- Azole copper inhibitors (benzotriazole/tolyltriazole) ~1–5 ppm
- Orthophosphate ~5–15 mg/L
- Polymer dispersants, ppm range

Hexavalent chromate inhibitors were banned from comfort cooling towers in 1990 and are
not in use.

**Where it legally goes** — one of three places: sanitary sewer under an industrial
pretreatment program; surface water under an NPDES permit with limits on residual
chlorine, metals, pH, and temperature; or on-site treatment and reuse. Real permitted
volumes are substantial: one Virginia data center permit allows up to 460,000 gal/day.
Quincy, Washington treats blowdown for industrial reuse, saving ~380 million gal/year of
potable water.

**A regulatory gap worth noting:** the organic treatment chemicals are usually not
individually limited in U.S. discharge permits. Control is indirect — residual-oxidant
limits, metals limits, and whole-effluent toxicity testing where applied.

---

## 4. PFAS — proportionate answer

**Where PFAS genuinely is in a data center:**

1. **Two-phase immersion fluids.** Fluoroketones (3M Novec, Fluorinert) *are* PFAS — the
   coolant itself. But this is a niche: two-phase immersion is well under 1% of data
   center cooling. 3M announced its exit from PFAS manufacturing in December 2022 and
   completed it at the end of 2025; LiquidStack, the leading two-phase vendor, pivoted to
   single-phase. No hydrocarbon two-phase fluid had qualified at data-center scale as of
   mid-2026.
2. **FK-5-1-12 clean-agent fire suppressant** (Novec 1230). Also a PFAS. Episodic air
   release on discharge, not a water pathway.
3. **Refrigerants, definitionally.** HFOs like R-1234yf degrade in the atmosphere to TFA,
   which is a PFAS under the OECD definition but not under current U.S. EPA working
   definitions. This is a fugitive air emission from sealed equipment — not a site water
   discharge pathway.

**Where PFAS is not:** no PFAS identified in the chemical families used in standard water
and glycol closed-loop coolants, or in mainstream cooling tower treatment programs. A
product-level SDS review remains the definitive check for any specific site.

**The key finding, stated carefully:** *no measured PFAS detection in data center cooling
discharge has been documented.* We searched for enforcement actions, permit records, and
reporting; none exist. But discharge permits generally do not require PFAS testing —
Virginia's data center permits contain none — so the absence of detections partly
reflects an absence of monitoring. Both halves of that sentence matter. The accurate
framing is a monitoring gap, not a clean bill of health, and not evidence of a problem.

Also frequently conflated but distinct: AFFF firefighting foam is not used in server
spaces; diesel generator emissions are an air-quality question with no PFAS connection.

---

## 5. Minnesota specifics

- **HF16 (2025, 1st Special Session)** created a DNR preapplication evaluation for data
  centers anticipated to use more than **100 million gallons per year** (~274,000 gal/day
  average), with aquifer testing where the commissioner requires it. Critics (CURE) have
  characterized the review as procedurally weak.
- **Discharge jurisdiction:** direct discharge to surface or ground water requires an MPCA
  permit. In the Twin Cities metro, discharges to the regional sanitary system go through
  Metropolitan Council Environmental Services industrial pretreatment permits.
- **Every Minnesota hyperscale proposal that has disclosed a cooling design is closed-loop
  or dry.** Meta's Rosemount project was estimated by the city at roughly 100,000 gal/day
  at peak — an order of magnitude below an evaporative equivalent. In Farmington, the city
  agreement allows Tract up to **2.93 million gal/day** while the developer states an
  expected average near **137,000 gal/day** with non-evaporative cooling. The gap between
  permitted maximum and claimed average is the substance of the public controversy.
- **Implication:** in Minnesota, the discharge story is mostly episodic closed-loop events
  plus domestic sewage — not continuous blowdown. Cold-climate economics point the same
  direction as the disclosures.

---

## 6. The tradeoff nobody gets to avoid

Dry cooling saves roughly 2–4 L/kWh of water at a cooling-energy penalty in the range of
25–35% (contested — Microsoft claims "nominal" penalty when paired with warm-water chip
cooling, which changes the arithmetic). Water and electricity are substitutes here. A
facility that eliminates evaporation has moved its impact to the grid, and the honest
comparison depends on what that grid burns.

Warm-water direct-to-chip cooling is what makes this trade favorable: chips that tolerate
30–45 °C coolant can reject heat to dry coolers in most climates without a chiller, which
is why new AI-era builds increasingly close the water loop entirely.

---

*Prepared 2026-08-11. Full source list with URLs: `research/` directory (three files,
~170 sources) and the exhibit's Sources panel. Figures marked (est.) are rule-of-thumb
values flagged as such in the underlying research.*

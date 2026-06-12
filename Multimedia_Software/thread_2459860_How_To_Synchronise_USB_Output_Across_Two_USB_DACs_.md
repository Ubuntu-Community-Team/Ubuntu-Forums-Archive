---
title: "How To Synchronise USB Output Across Two USB DACs - For Active Speakers"
date: 2021-03-28
forum: Multimedia Software
---

### Post by redger on 2021-03-28
I've been considering an active speaker project, motivated by the advent of low cost high quality amplifiers (TDA32xx)
I'm coming up against the challenge of low cost computer output to multiple amps

In an ideal world I would use
[LIST=1]
[*]Source = AMLogic S9xx or Pi or Nuc, running some flavour ofLinux
[*]DSP = CamillaDSP or BruteFIR or similar running on source computer
[*]DAC = USB DACs eg. Topping E30 * n
[*]Amplifier = TPA325n * 2-3
[*]Speaker = 2-3 Way without crossover (handling by computer)
[/LIST]

Most of those elements are low cost, "good quality"  and sufficiently capable

The Problem
[INDENT]USB is a negotiated link, so there can be significant timing variance between transmissions and between devices. This will probably be an audible problem when "sound" timing needs to be coordinated across multiple devices ie. the DACs when one is feeding left speaker an another DAC feeding right speaker, say[/INDENT]

The Question
[INDENT]Is there a way to guarantee trasmission coordination across multiple USB devices ? Has anyone succeeded in making this kind of setup work ?[/INDENT]

It's possible to purchase additional equipment to achieve this outcome (but these add to the cost and add points of failure) eg.
[LIST]
8 Channel DAC like the Octo or DIYinHK units
Intermediate processor like the Motu 8A or Auverdion Aurora/Infinitas
MiniDSP UDIO8[/LIST]

Is there a way to achieve this outcome or am I misunderstanding or looking in the wrong place

Any advice / guidance gratefully accepted

---


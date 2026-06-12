---
title: "Unity &amp; Global Menu Not Present"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2011-04-03
Hi all,
I updated from 10.10 to 11.04 on a test machine, just to see how that whole process went and to seek out problems. It upgraded, but Unity is nowhere to be found (I'm logged in in Ubuntu mode, not Ubuntu "classic." Also, the global menu is not present. Everything looks as it did in 10.10, save the minor changes in the wallpaper. 
Is this a bug, or is this because something is not "turned on" somewhere?

---

### Post by Dutch70 on 2011-04-03
Try installing Unity 2D from software center.

---

### Post by uRock on 2011-04-03
Moved to NNT&D where testing and discussion of Natty is usually conversed.

Have you installed graphics drivers?

---

### Post by teejay17 on 2011-04-03
> **uRock said:**
> Moved to NNT&D where testing and discussion of Natty is usually conversed.

Have you installed graphics drivers?
It's a Thinkpad T41, so there are no extra drivers that are usually required. I can understand the 3D not working--perhaps the machine is too old--but the global menu not working indicates that there may be something else that isn't right.

---

### Post by uRock on 2011-04-03
Intel or nVidia? I installed the experimental nVidia driver and all is working great.

---

### Post by cariboo on 2011-04-03
> **teejay17 said:**
> It's a Thinkpad T41, so there are no extra drivers that are usually required. I can understand the 3D not working--perhaps the machine is too old--but the global menu not working indicates that there may be something else that isn't right.

What intel chipset does your system use?

---

### Post by teejay17 on 2011-04-03
> **cariboo907 said:**
> What intel chipset does your system use?
                                           
                                         

                                      [COLOR=#0044dd]Processor[/COLOR]
                                         [COLOR=#000000]Processor[/COLOR]
                                         [COLOR=#000000]Name[/COLOR]
                               [COLOR=#505050]Intel(R) Pentium(R) M processor 1400MHz[/COLOR]
                                         [COLOR=#000000]Family,             model, stepping[/COLOR]
                               [COLOR=#505050]6, 9, 5 (Pentium M)[/COLOR]
                                         [COLOR=#000000]Vendor[/COLOR]
                               [COLOR=#505050]Intel[/COLOR]
                                         [COLOR=#000000]Configuration[/COLOR]
                                         [COLOR=#000000]Cache             Size[/COLOR]
                               [COLOR=#505050]1024kb[/COLOR]
                                         [COLOR=#000000]Frequency[/COLOR]
                               [COLOR=#505050]1400.00MHz[/COLOR]
                                         [COLOR=#000000]BogoMIPS[/COLOR]
                               [COLOR=#505050]2790.47[/COLOR]
                                         [COLOR=#000000]Byte             Order[/COLOR]
                               [COLOR=#505050]Little Endian[/COLOR]
                                         [COLOR=#000000]Features[/COLOR]
                                         [COLOR=#000000]FDIV             Bug[/COLOR]
                               [COLOR=#505050]no[/COLOR]
                                         [COLOR=#000000]HLT             Bug[/COLOR]
                               [COLOR=#505050]no[/COLOR]
                                         [COLOR=#000000]F00F             Bug[/COLOR]
                               [COLOR=#505050]no[/COLOR]
                                         [COLOR=#000000]Coma             Bug[/COLOR]
                               [COLOR=#505050]no[/COLOR]
                                         [COLOR=#000000]Has             FPU[/COLOR]
                               [COLOR=#505050]yes[/COLOR]
                                         [COLOR=#000000]Cache[/COLOR]
                                         [COLOR=#000000]Cache             information not available[/COLOR]
                  
                               [COLOR=#000000]Capabilities[/COLOR]
                                         [COLOR=#000000]fpu[/COLOR]
                               [COLOR=#505050]Floating Point Unit[/COLOR]
                                         [COLOR=#000000]vme[/COLOR]
                               [COLOR=#505050]Virtual 86 Mode Extension[/COLOR]
                                         [COLOR=#000000]de[/COLOR]
                               [COLOR=#505050]Debug Extensions - I/O breakpoints[/COLOR]
                                         [COLOR=#000000]pse[/COLOR]
                               [COLOR=#505050]Page Size Extensions (4MB pages)[/COLOR]
                                         [COLOR=#000000]tsc[/COLOR]
                               [COLOR=#505050]Time Stamp Counter and RDTSC instruction[/COLOR]
                                         [COLOR=#000000]msr[/COLOR]
                               [COLOR=#505050]Model Specific Registers[/COLOR]
                                         [COLOR=#000000]mce[/COLOR]
                               [COLOR=#505050]Machine Check Architeture[/COLOR]
                                         [COLOR=#000000]cx8[/COLOR]
                               [COLOR=#505050]CMPXCHG8 instruction[/COLOR]
                                         [COLOR=#000000]mtrr[/COLOR]
                               [COLOR=#505050]Memory Type Range Registers[/COLOR]
                                         [COLOR=#000000]pge[/COLOR]
                               [COLOR=#505050]Page Global Enable[/COLOR]
                                         [COLOR=#000000]mca[/COLOR]
                               [COLOR=#505050]Machine Check Architecture[/COLOR]
                                         [COLOR=#000000]cmov[/COLOR]
                               [COLOR=#505050]Conditional Move instruction[/COLOR]
                                         [COLOR=#000000]clflush[/COLOR]
                               [COLOR=#505050]Cache Line Flush instruction[/COLOR]
                                         [COLOR=#000000]dts[/COLOR]
                               [COLOR=#505050]Debug Store[/COLOR]
                                         [COLOR=#000000]acpi[/COLOR]
                               [COLOR=#505050]Thermal Monitor and Software Controlled             Clock[/COLOR]
                                         [COLOR=#000000]mmx[/COLOR]
                               [COLOR=#505050]MMX technology[/COLOR]
                                         [COLOR=#000000]fxsr[/COLOR]
                               [COLOR=#505050]FXSAVE and FXRSTOR instructions[/COLOR]
                                         [COLOR=#000000]sse[/COLOR]
                               [COLOR=#505050]SSE instructions[/COLOR]
                                         [COLOR=#000000]sse2[/COLOR]
                               [COLOR=#505050]SSE2 (WNI) instructions[/COLOR]
                                         [COLOR=#000000]tm[/COLOR]
                               [COLOR=#505050]Thermal Monitor[/COLOR]
                                         [COLOR=#000000]pbe[/COLOR]
                               [COLOR=#505050]Pending Break Enable[/COLOR]
                                         [COLOR=#000000]up[/COLOR]
                               [COLOR=#505050]smp kernel running on up[/COLOR]
                                         [COLOR=#000000]bts[/COLOR]
                               [COLOR=#505050]Branch Trace Store[/COLOR]
                                         [COLOR=#000000]est[/COLOR]
                               [COLOR=#505050]Enhanced SpeedStep[/COLOR]
                                         [COLOR=#000000]tm2[/COLOR]
                               [COLOR=#505050]Thermal Monitor 2[/COLOR]

---

### Post by cariboo on 2011-04-04
Sorry I should have said graphics chipset, type:

```
lspci | grep VGA
```

in a terminal.

---

### Post by teejay17 on 2011-04-04
Well I re-installed from scratch. The global menu works, Unity, unfortunately does not. My test machine must be too old. 
Looks like there is a problem updating from 10.10 to 11.04, however, with regards to the gnome panels. Essentially, the global menu should have updated, but did not and looked the same as it did in 10.10. Must be a bug in the system somewhere.

---


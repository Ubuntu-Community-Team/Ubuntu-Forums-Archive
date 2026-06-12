---
title: "How to reduce latency on impactVCB 166."
date: 2012-05-09
forum: Multimedia Software
---

### Post by Temporary_Resident on 2012-05-09
[COLOR=#3a3a3a]Hi  Guys,[/COLOR]
[COLOR=#3a3a3a]
I am developing a  real-time surgical system which involves the real-time processing of video feeds with the impactVCB 166[/COLOR][COLOR=#3a3a3a] on Kubuntu 11.10 (although the problem is identical under K10.04LTS).

The total  cycle-time (camera to display) of the system is approximately 240ms.  This is too  great a delay for a surgical system, the danger being that you cannot accurately  control the surgical device you are using, plus surgeons have reported headaches  and dizziness from using systems with long latencies.  Ideally the cycle-time  will be 50ms or less.[/COLOR] [COLOR=#3a3a3a]The test system is as  follows:[/COLOR]
 
[LIST]
[*][COLOR=#3a3a3a]Sony CyberShot DSC-P150  set to 1 megapixel to emulate the real endoscope[/COLOR]
[*][COLOR=#3a3a3a]BNC cable[/COLOR]
[*][COLOR=#3a3a3a]impactVCB 166 video  capture card.[/COLOR]
[*][COLOR=#3a3a3a]Gigabyte H61M-DS2  Motherboard[/COLOR]
[*][COLOR=#3a3a3a]4GB  Memory[/COLOR]
[*][COLOR=#3a3a3a]Intel i5-2500 @ 3.3  GHz[/COLOR]
[*][COLOR=#3a3a3a]1 TB hard  disk[/COLOR]
[*][COLOR=#3a3a3a]GStreamer processing  software [/COLOR]
[*][COLOR=#3a3a3a]LG Flatron w1642S  monitor[/COLOR]
[*][COLOR=#3a3a3a]Kubuntu 11.10 operating  system[/COLOR]
[/LIST]
 [COLOR=#3a3a3a]Using a stopwatch timer I can measure the round trip at 240ms +/- 20 ms.[/COLOR]
 [COLOR=#3a3a3a]I have tried the following and they have no  impact on the cycle time:[/COLOR]
 
[LIST]
[*][COLOR=#3a3a3a]Changing the processor to  AMD II running at 2.6 GHz with 2GB or memory [/COLOR]
[*][COLOR=#3a3a3a]Substantially changing  the GStreamer pipeline to reduce the fps and remove filesave.[/COLOR]
[*][COLOR=#3a3a3a]Changing the monitor to a  Samsung S22A300B (I haven't tried a cathode-ray VDU).  I imagine the display  contributes about 30ms to the cycle time.[/COLOR]
[/LIST]
 [COLOR=#3a3a3a]However,  [/COLOR]
 
[LIST]
[*][COLOR=#3a3a3a]Switching to a generic  USB webcam more than halves the cycle time to 100ms +/- 20  ms.[/COLOR]
[/LIST]
 [COLOR=#3a3a3a]Is there some way I can  configure the impactVCB 166 not to perform any processing on-board and speed up  the cycle time?[/COLOR]


[COLOR=#3a3a3a]Regards
[/COLOR]

[COLOR=#3a3a3a]Steve[/COLOR]

---


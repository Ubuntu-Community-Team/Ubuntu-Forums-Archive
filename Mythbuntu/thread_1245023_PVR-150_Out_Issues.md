---
title: "PVR-150 Out Issues"
date: 2009-08-20
forum: Mythbuntu
---

### Post by sharkmaul on 2009-08-20
I used to run Knoppmyth a year or two ago and it ran fine. I decided that this time around I'd give Mythbuntu a go. I spent about 5 hours banging my head against a wall after installation. I can get everything to work except TV out. I've chosen it as an MPEG2 card w/ dev en0. I tried a quick test and the card still works (installed knoppmyth and it worked fine). Also when I reboot it gives me the blue screen like nothing is plugged into the port but the screen goes black once the unit is powered on. I really want the ease of use of mythbuntu but this is a HUGE hurdle for me. If you have any ideas let me know (I'm pretty much a  linux noob).



Ryan

---

### Post by xinix on 2009-08-20
I'm pretty sure the PVR-150 does not have tv-out.  At least mine doesn't.  The PVR-350 does but that is different than the 150.  Your video card is what you'll want to use to connect to your tv/monitor

---

### Post by sharkmaul on 2009-08-20
No it has a TV out. I've used it on my previous install. It has a port for a cable to plugin that has regular RCA and S-video. And I know the hardware works because I got it to work w/ Knoppmyth yesterday I just would like the functionality of Mythbuntu, but it won't do me any good if TV out doesn't work.

---

### Post by tgm4883 on 2009-08-20
> **sharkmaul said:**
> No it has a TV out. I've used it on my previous install. It has a port for a cable to plugin that has regular RCA and S-video. And I know the hardware works because I got it to work w/ Knoppmyth yesterday I just would like the functionality of Mythbuntu, but it won't do me any good if TV out doesn't work.

No, no it does not. You may be thinking of the PVR-350, as that has TV out capabilities. The PVR-150 does not though.

---

### Post by xinix on 2009-08-21
Please post the results from this command:
```
dmesg | grep ivtv
```

This way we can figure out exactly which card you have.

---


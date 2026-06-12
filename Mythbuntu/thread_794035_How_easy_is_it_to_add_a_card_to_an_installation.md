---
title: "How easy is it to add a card to an installation?"
date: 2008-05-14
forum: Mythbuntu
---

### Post by jimmyfergus on 2008-05-14
What is involved in adding a tuner card (PVR-350, no TV-out required) to an existing installation?  Will it be auto-detected and drivers set up?  

Obviously I'll have to configure the new source in MythTV - that's easy.

Sorry if this is covered somewhere, but I failed to find the info.

I'm trying Mythbuntu, coming from Knoppmyth, and have the luxury of a separate new machine to install it on.  I want to get everything set up properly (recordings, media and schedules etc transferred) before doing a final replacement, transferring the PVR-350, hopefully with minimal disruption and maximum WAF.  I also have a HDHomeRun, which I have configured in advance because the two setups can share it.

---

### Post by klc5555 on 2008-05-14
I found with a PVR 150 that it was not autodetected when added to an established (7.10) system that had no other ivtv cards. For whatever reason, my installation seemed to lack the ivtv drivers.

But within 5 minutes, after a quick search for ivtv-related packages in synaptic, installation of same, and a restart, the card was detected, alive, and ready to configure in the mythtv backend setup. 

The wiki entry for your PVR-350 card is:

[http://mythtv.org/wiki/index.php/Hauppauge_PVR-350](http://mythtv.org/wiki/index.php/Hauppauge_PVR-350)

---

### Post by superm1 on 2008-05-14
The PVR-350 should have all drivers shipped with all installs.  The drivers come with the default kernel in 2.6.24 (kernel with 8.04)

---


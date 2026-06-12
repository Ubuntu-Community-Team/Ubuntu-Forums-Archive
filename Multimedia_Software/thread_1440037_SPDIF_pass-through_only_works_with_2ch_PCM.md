---
title: "SPDIF pass-through only works with 2ch PCM"
date: 2010-03-27
forum: Multimedia Software
---

### Post by cdekter on 2010-03-27
I'm trying to get AC3/DTS passthrough working with my HTPC in which I'm using the onboard sound from an nForce 4-based motherboard. I've tested it in Win7 to check that all the connections etc are set up correctly and it works perfectly there. However under Kubuntu I can only get 2ch PCM sound to work through the SPDIF connection. Any DTS/DD sources just result in silence.

If I go into Multimedia settings in the System Settings panel, the SPDIF device that shows up there (once I enable advanced devices) produces no sound with the Test button. I can hear a click as the device is activated but no sound is produced. I can also see that a digital signal is making it to my receiver as it has an icon which lights up when it locks onto a signal.

Has anyone had success with SPDIF passthrough in 9.10? I've tried twiddling all the settings in Kmix relate to IEC and also tried following the Alsa wiki on digital passthrough without any success. Unfortunately this is a dealbreaker for me - I need digital sound working or I'll have to revert to Win7 with WMC... which I'd really rather not do as I was just starting to really like XBMC with Tvheadend.

---

### Post by AKADAP on 2010-03-27
Try running "sudo /etc/init.d/alsa-utils restart" from a terminal just before your start one of the videos that is having trouble.
I have to do that every time before I watch a show with MythTV.

---

### Post by cdekter on 2010-03-28
Thanks... I tried that and alsa-utils reset [cardname] as well... no luck

---


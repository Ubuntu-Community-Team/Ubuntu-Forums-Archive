---
title: "Disable AP Scanning when connected"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by jfm on 2010-03-04
Hi all

I'm running on 9.10. Is there any way to disable automatic accesspoint scanning when once connected.

Or even better. Is it possible to disable automatic scanning on some channels/frequencies.

I'm asking because when Ubuntu does an AP scan it sometimes interferes with my wireless Sony Television. I've tracked that down to problems with some wireless channels which are both being used by 802.11a and the television

As my access point at home runs on a 802.11g I really don't need to have it scan for other access points when connected.

Anyway, is there any suggestions how to achieve this?

Cheers
Jesper

---

### Post by jfm on 2010-03-09
After more investigation, I found that I could disable 802.11n in the iwlagn driver (which is what I'm using), but it seems you can't disable 802.11a (which is what I really need)

Does anyone know if that is possible?

I have tried doing modinfo iwlagn, but came up short.

I've also been trying to find a way to contact the developer(s) if the iwlagn module to file a bug/feature request, but was not able to find any information on who actually develops the module, nor any mailing lists etc. If someone has any pointer, that would be much appreciated.

Cheers
Jesper

---


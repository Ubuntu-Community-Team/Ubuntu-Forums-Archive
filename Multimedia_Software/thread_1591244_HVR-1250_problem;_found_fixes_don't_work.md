---
title: "HVR-1250 problem; found fixes don't work"
date: 2010-10-09
forum: Multimedia Software
---

### Post by drewciferpike on 2010-10-09
I am really confused/frustrated/exhausted, now. I bought a HVR-1250 for a PVR and music/media HTPC that I just built, and installed Mythtv last night. The  backend continues to report it as "failed to open" in the capture card  section.

Having read through all of the recent information I could find (mostly forums), I've tried card=3, 7, 12, 18, 19, 20, and 21 options in the new cx23885.conf  file, and the card's still not recognized in Mythtv. 
dmesg shows me the  same info from most recent screen captures (other forums, too), and  lspci still reports it as a 1250 rev. 04. (Before I made the new conf file, the card was listed with device code 0070:2259... I don't know if that helps)

I'm new to all things linux, and I have  no idea where else to look, or what else to do. I'd prefer to not use Win Media Player, as I've heard it has more playback issues (skips, jerks, etc.) with recorded high-def OTA programs. If I'm wrong, I have no problem with switching OSes, as I just want to be able to record high-def TV and watch it when the baby is asleep...

Is there something I'm forgetting, or am I just screwed, for some reason I don't understand?

Thanks in advance (I hope!).

-Drew

---

### Post by drewciferpike on 2010-10-10
I returned the card to Amazon, and picked up another 1250 from the local  Frys. This one gave different info (not 0070:2259) when thrown through  dmesg and lspci, and it works like a charm, despite being another rev.  04 card.

I have no idea what the difference was between the two cards, but the new one works.

---


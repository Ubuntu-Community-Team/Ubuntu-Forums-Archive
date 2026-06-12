---
title: "Speed Issues on C3 front end"
date: 2007-10-08
forum: Mythbuntu
---

### Post by jpwilson on 2007-10-08
Having found mythbuntu and installed a backend very easily on a low power 4400 x2, i need a wife accepting silent front end for the bedroom. I have no cat 5 to there so its wireless im afraid. I have a wireless card that seems to work (still on the wired) but while the thing boots and installs fine to a 4gig usb key, its playback is very choppy. This i assume is due to the vesa driver. The case is an MSI Axis 700 with
1Gig Via C3 embedded
Unichrome Pro Graphics
CN700 VT8237R+ Chipset

yes the thing is quiet very quiet (only fan is on the psu) but it needs to work lol

I have tried the openchrome drivers via synaptic and selected via xconf and it breaks x.

Any clues people?

James

---

### Post by superm1 on 2007-10-08
> **jpwilson said:**
> Having found mythbuntu and installed a backend very easily on a low power 4400 x2, i need a wife accepting silent front end for the bedroom. I have no cat 5 to there so its wireless im afraid. I have a wireless card that seems to work (still on the wired) but while the thing boots and installs fine to a 4gig usb key, its playback is very choppy. This i assume is due to the vesa driver. The case is an MSI Axis 700 with
1Gig Via C3 embedded
Unichrome Pro Graphics
CN700 VT8237R+ Chipset

yes the thing is quiet very quiet (only fan is on the psu) but it needs to work lol

I have tried the openchrome drivers via synaptic and selected via xconf and it breaks x.

Any clues people?

James
When you say that openchrome breaks X, what do you mean?

It literally won't start?  Look at /var/log/Xorg.0.log and /var/log/Xorg.0.log.old.  Is it because your card isn't supported by openchrome?  If that's the case, then you can install xserver-xorg-video-via or xserver-xorg.video-unichrome still too.

---

### Post by jpwilson on 2007-10-09
no it wont start.
I am in the process f reinstalling should i pass any option or select a different driver during setup?

---


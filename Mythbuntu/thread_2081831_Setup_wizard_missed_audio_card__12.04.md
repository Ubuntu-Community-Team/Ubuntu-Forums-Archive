---
title: "Setup wizard missed audio card  12.04"
date: 2012-11-07
forum: Mythbuntu
---

### Post by Panhead Bill on 2012-11-07
The first time, the wizard detected the onboard audio and the creative labs card.  The card worked in one configuration, but then the front end crashed when I tried the audio test with a blank in the number of speakers bar.  After rebooting the wizard will only detect the onboard audio chip.

Until I hit the crash I was impressed with the wizard.  It seems to help set up the audio better than the older method (When it works anyway).

Any way to force the detection of my PCI audio card?

---

### Post by nickrout on 2012-11-07
> **Panhead Bill said:**
> The first time, the wizard detected the onboard audio and the creative labs card.  The card worked in one configuration, but then the front end crashed when I tried the audio test with a blank in the number of speakers bar.  After rebooting the wizard will only detect the onboard audio chip.

Until I hit the crash I was impressed with the wizard.  It seems to help set up the audio better than the older method (When it works anyway).

Any way to force the detection of my PCI audio card?I am pretty sure the wizard uses the same detection method as was there in the previous version. So if your card is in /proc/asound it should be detected.

If it is not in /proc/asound you have a deeper problem...

---

### Post by Panhead Bill on 2012-11-08
This pc is my secondary backend and main frontend.  It hangs when I tried to load 12.04 and 11.10.  Only by starting with 11.04 and upgrading was I able to get this far.  No doubt it has some software issues.

The fact that the wizard detected the Xfi card the first time but not since has me stumped.  Oh well back to the basement to try some APT commands.

---


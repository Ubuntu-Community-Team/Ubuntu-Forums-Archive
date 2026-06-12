---
title: "I have to boot in recovery mode every time"
date: 2012-01-07
forum: Mythbuntu
---

### Post by Meph1st0 on 2012-01-07
So...my computer is quiet hosed.  I recently upgraded from 10.10 to 11.10 by doing a clean install of 11.10.  I initially had to use the nomodeset option to get into the installer and get it installed.  After reboot it didn't work anymore and I tried several different workarounds that I read online but none worked.  So I decided to upgrade my video card with one that (was supposed to) work out of the box.  Apparently I didn't research that part very well because I bought an ATI Radeon 5450.  This card is also giving me trouble.  The open source driver works just fine except I can't get HDMI audio.

So in order to fix the HDMI audio issue I disabled the onboard audio (so as not to confuse myself with multiple audio devices) and I installed the proprietary catalyst drivers direct from ATI.  Now it won't boot to the GUI unless I boot in recovery mode first and select Resume.  But the good thing is I have HDMI audio now.  If I choose not to boot in recovery mode it hangs after displaying the following:

"Check for running unattended-upgrades"

Also, additional information:

When I play a video in mythfrontend it plays in super speed.  In VLC it plays at regular speed.

If I run fglrxinfo it shows that I do in fact have the ATI drivers installed.

I installed the mythbuntu PPAs and I believe I'm running on 0.24-fixes.

I know there's alot of information here but it's only because I've tried my hardest to fix it on my own without begging for help on here.

So in the end there's two problems I want to fix.  I'd like to boot up directly without having to select recovery mode everytime and I'd like the videos to play at normal speed with audio.  Anyone out there willing to help me tackle this?

---


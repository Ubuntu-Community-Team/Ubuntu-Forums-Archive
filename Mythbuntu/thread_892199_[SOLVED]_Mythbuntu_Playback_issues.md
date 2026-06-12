---
title: "[SOLVED] Mythbuntu Playback issues"
date: 2008-08-16
forum: Mythbuntu
---

### Post by toddk111 on 2008-08-16
I have an AMD64x2 4200+ with 3gb RAM, onboard nVidia 6150SE video, and Ubuntu 8.04 with all the latest updates.  I have 2 DVICO FusionHDTV5 USB Gold and an Silicondust HDHomerun.  I have successfully scanned for ATSC QAM channels.  I also set a manual timer and did a test recording using one of the DVICO units.  My problem is that MythTV won't play live TV or playback the file I recorded.  I was able to playback the test recording in Windows and even checked it for errors using VideoRedo.  Where do I start to troubleshoot this issue?

Thanks,
Todd

---

### Post by newlinux on 2008-08-17
play with your playback profiles:

Setup->TV Settings->Playback

Tru CPU++ to start. I have similar hardware (x2 4200, 2GB RAM, 6150) and that was a good starting point for me.

Also what happens when you aren't able to play back anything? do you get any errors? Have you looked at your frontend logs for clues?

---

### Post by toddk111 on 2008-08-17
I made the change you suggested and it worked...but was still a little choppy.  I decided to try to play the file outside of Myth using Totem Player.  It had me download a couple of Gstreamer plug-ins in order to play the file.  That did the trick...now everything works in MythTV without lockup.

Thanks for your help!!!  Now on to the customizing.

---


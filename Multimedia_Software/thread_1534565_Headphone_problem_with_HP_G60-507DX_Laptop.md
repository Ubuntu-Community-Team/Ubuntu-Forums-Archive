---
title: "Headphone problem with HP G60-507DX Laptop"
date: 2010-07-19
forum: Multimedia Software
---

### Post by wallphoenix on 2010-07-19
I solved this, but the relevant helps were a bit scattered, so I'm going to try and consolidate the process here.

Using: HP G60-507DX laptop with the Conexant CX20583 and/or Intel G45 DEVCTG sound card (I'm not real clear on what those two involve overall, but hopefully with both numbers in there, it will help whoever's looking for help).

Originally, the speakers worked fine, but when the headphones were plugged in, the speakers wouldn't mute.

I first used:

SoundCheck's Alsa Upgrade Script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

The first post has a lot of helpful text (including instructions on using the downloadable script) and you can find a link to download the script at the end of that first post. It's called: [AlsaUpgrade-1.0.23-2.tar]("http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001")

The only thing that seemed to result after this update was that now my headphones stopped working at all, but the speakers still worked fine. I'm not entirely sure this will be necessary for you, but it's one of the steps I ended up following.

I then followed these steps, posted at [http://ubuntuforums.org/showthread.php?t=1467218&highlight=g60&page=2](http://ubuntuforums.org/showthread.php?t=1467218&highlight=g60&page=2) by jjjjeremy, reprinted here with a slight modification I had to use:

Steps 1-4 were unnecessary in my case.
5. Open Terminal > type: sudo apt-get install  linux-backports-modules-alsa-lucid-generic  (installs alsa backports)
6. Password
7. Select Y (yes)
8. type: cd /etc/modeprobe.d  (just changes the folder you're working  in)
9. type: sudo cp alsa-base.conf alsa-base-backup.conf (creates a backup  of the file you are about to edit. To revert, delete alsa-base.conf and  rename alsa-base-backup.conf to alsa-base.conf)
10. Password (if needed)
11. type: gksudo gedit alsa-base.conf (opens alsa-base.conf for editing)
12. add the line " options snd-hda-intel model=dell-vostro " (without  quotation marks) to the end of the file
13. Save
14. Reboot
15. Test

Whereupon my speakers and headphones work great. The internal mic still seems to not be working (at least with Sound Recorder). I'll edit this if I find the fix for that.

P.S. Thanks to lidex, who suggested using the "model=dell-vostro" to someone else with a G60 laptop. If he hadn't I wouldn't have thought to try that.

---


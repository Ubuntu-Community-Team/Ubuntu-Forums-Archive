---
title: "Empty text boxes"
date: 2009-04-27
forum: Mythbuntu
---

### Post by alavena on 2009-04-27
I have a Gateway 7422GX as a media center. Its specs are: Athlon 64 3400+ CPU, 1gb Ram, Ati Mobility Radeon 9550 (a downgraded 9600), 40gb HD (was 80 when new). Also an Audigy 2 ZS Notebook soundcard. It's wired to a PAL TV via S-Video.

The laptop has run on Windows XP, Vista RC and finals, Ubuntu since 6.something and even Solaris and OSX. As a Media Center it's been running XP or XP/MCE with MediaPortal. For some reason, XBMC froze every time I tried to run it.

I've downloaded the latest version of Mythbuntu. It went through the install process flawlessly until the moment I had to configure the Myth frontend. Then I was presented with boxes and frames that had no text in them. It responded to the enter key and got me out of the installer, rebooting the PC. I'm sure there was supposed to be text in the boxes. Upon reboot, something was wrong with the video drivers and the resolution was wrong.
I decided to fire up the Live mode, booting again from the CD. It worked, but the Myth frontend brought again the same frames and boxes that responded to the remote control and the keyboard by highlighting, but no text at all.

What can it be? I'd love to test Myth.

Thanks

---

### Post by superm1 on 2009-04-27
This is a bug that is mentioned in the release notes.  

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898)

There are two workarounds:

1) Launch mythtv with an environment variable, mentioned in that bug
2) Disable DRI on the X server.

---

### Post by ktmom on 2009-04-27
My problem is exactly what is being described in the  Bug #341898 - ATI graphics, AMD processor aggrevated by the fact that I am a newb.  

When the fonts don't display, I don't understand how to edit the xorg.conf to turn off DRI.  I also haven't tried the other solution, the mesa build from Mario Limonciello's PPA.  Again I don't understand how to install this.  I've done something similar in Ubuntu, but I can't see anything after the install is completed.

---

### Post by ktmom on 2009-04-28
Duh... I booted to a live disk and edited the xorg.conf then rebooted.  It fixed my problem.

---


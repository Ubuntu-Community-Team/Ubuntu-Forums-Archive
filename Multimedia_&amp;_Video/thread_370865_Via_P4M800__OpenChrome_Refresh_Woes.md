---
title: "Via P4M800 / OpenChrome Refresh Woes"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by Alterscape on 2007-02-26
Hi all, first post on Ubuntuforums!

I'm trying to install Ubuntu Edgy (6.10) from the i386 CD ISO onto a budget barebones PC.  No, the hardware was not my choice.

Anyway, the mainboard is a MachSpeed P4M800-D2, which uses Via's S3 Unichrome PM800 onboard video chipset.  When I first booted Edgy from the livecd, it defaulted to 1600x1200 @ 60hz.  Any attempt to change the display resolution resulted in a brief flash of the new display res, followed by xorg restarting (I think, anyway -- black screen for a second or so then back to a blank desktop). The only refresh rate in the dropdown box is 60Hz.

I found the OpenChrome install tutorial at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) and followed those directions to download, compile, and install the latest OpenChrome, and set it up as the xorg display driver.  I have not touched the second half of the tutorial on enabling 3d support yet.

After completing the first half of the tutorial and restarting xorg, I am able to successfully select other screen resolutions. I've tested 1024x768 and 1280x1024, but the only refresh rate options available here are 60Hz and 56Hz.  I know this monitor supports better -- my primary system runs KUbuntu at 1600x1200@80Hz with an ATI video card.  I suppose it is possible that the PM800 only supports 60hz refresh, but I really don't want to ponder that too much.

How do I convince xorg/gnome's screen resolution configuration applet to let me set a higher refresh rate before this monitor kills my eyes?

---

### Post by firfin on 2007-04-04
I am experiencing the same problem (although I am using the 'via' driver instead of openchrome. ) HAve tried setting the  "UseEdidFreqs" "No" in the monitor section?
This is a setting for nvidia I believe (that is probably why it did not work for me), but maybe this works for you.
Or maybe someone else knows what this setting is called for the via or the openchrome driver?

---


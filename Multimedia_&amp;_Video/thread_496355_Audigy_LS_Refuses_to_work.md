---
title: "Audigy LS Refuses to work"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by Marantz on 2007-07-09
Edit- I'm using Fiesty.

I can't even get broken audio out of it...

lspci returns

veldren@jesse:/usr/src/modules$ lspci
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
veldren@jesse:/usr/src/modules$ 

I have tried compiling ALSA from source

I have tried packages

I have tried just about everything I can find on the forums...


I could really use some help on this, first time using Ubuntu on an Intel system and I'm having nothing but headaches and problems.

---

### Post by RomeReactor on 2007-07-09
Hi. I have that card also. Did you install it after installing Feisty? Try right-clicking the Volume Applet in the top panel, select "Preferences", make sure the driver it's using is **CA0106**, and choose **Analog Front** as the track to control. In the terminal, enter **alsamixer**, and make sure the Analog Front channel isn't muted (left/right arrows scroll through channels, up/down changes volume, **m** mutes or un-mutes, **ESC** twice exits alsamixer). You can also try disabling your on-board audio card in BIOS. If you disable the on-board card, next time you do a fresh install Ubuntu should automatically pick up your SoundBlaster and enable it (that is, if you *did* install the card *after* installing Feisty. I'm not saying you should re-install just for this, though).

---

### Post by bkwraith on 2008-06-14
I used [this]("http://ubuntuforums.org/showthread.php?t=205449") thread to get the audio working, however now my front panel doesn't automatically stop playback through the rear.  I have all but the front panel muted, tried a few different configurations in *alsamixer* and now I'm kind of stumped.  I am a newb at this, so any advice would be nice.

---


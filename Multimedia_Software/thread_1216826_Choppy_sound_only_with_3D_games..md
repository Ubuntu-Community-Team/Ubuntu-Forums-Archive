---
title: "Choppy sound only with 3D games."
date: 2009-07-18
forum: Multimedia Software
---

### Post by Whydoe on 2009-07-18
I'm using a fresh install of Jaunty 9.04.  Everything works fine except for audio when playing any 3D accelerated games.  One in particular is Chromium B.S.U.  My system is a Dell 4700 with an ATI X300 card.  Originally I had the issue with the on-board audio.  I added a SB!Live card and disabled the on-board audio in the bios.  Same thing.  Audio works fine for MP3s, WAV, and AVI files, and all other games.  I haven't tried getting the binary ATI X.org driver since I've heard that ATI are not supporting the X300 version anymore.  Anyway, this is my pci layout.

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
03:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
03:01.0 Communication controller: ESS Technology ES2898 Modem (rev 02)


I also get this when I start gstreamer-properties

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

I've used gstreamer-properties to disable Xv.  Doesn't help.  
I've installed gnome-alsamixer, and pulseaudio.  It's weird because I've tried to make changes to System/Preferences/Sound choosing different drivers (oss, pulse, alsa) and once in a while I can load up the game and the sound is spot on.  I can quit, load it in again, and it still works.  Maybe after the 3rd try, it's back to choppy audio.  I had an issue like this before when I used an nvidia card.  I fixed that with an updated nvidia driver I believe.  Am I missing drivers?  Or plugins?  It does sound like a glx ati driver issue.  Any suggestions?  I've already checked :
Here - [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
here - [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
Didn't help.

[Edited to add] - Just installed Assualt Cube.  Same thing happened - only the choppy sound (and graphics) went away during gameplay.  And, just running the game again - it seems fine.  Strange.

---


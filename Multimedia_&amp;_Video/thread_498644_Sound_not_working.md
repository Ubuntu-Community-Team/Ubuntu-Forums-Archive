---
title: "Sound not working"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by russianboy1313 on 2007-07-11
I have a pretty old computer and I decided to start getting into linux

I have installed Ubuntu perfectly fine, but have a huge problem, I cannot find the sound card device/driver. 

Followed this great guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) but got stuck at a certain point. 
First of all i have the onboard sound card enabled in BIOS

1.I ran lspci and got this:
alex@Black:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

This is kinda where I got stuck, couldn't find the sound card...
I was pretty positive it was this: Intel Corporation 440BX
But when I want to ALSA and found a driver for it (intel8x0) and typed in:
sudo modprobe snd-intel8x0

It didn't do anything...
This computer is pretty old, but hope you guys will help me out.

Thanks a lot,
Alex

---

### Post by russianboy1313 on 2007-07-11
My other solution is to find an old sound card and install it, at least it won't be an onboard and see how that would work.

But still really hoping that you guys will help me out

---

### Post by NilsE on 2007-07-11
Try this:

In a terminal run: asoundconf list

That should return a list of cards.  


In a terminal run: asoundconf set-default-card xxxxx

Then again with sudo: sudo asoundconf set-default-card  xxxxx

Where xxxxx = the exact name of the card asoundconf list returns.

---

### Post by russianboy1313 on 2007-07-11
To my disappointment, when i ran asoundconf it printed:

List of sound cards:______ <-blank

No list of sound cards...
and my idea of finding another sound card didn't work.

By the way thanks for helping out but the problem still exists

Any other ideas?

Thanks a lot
Alex

---

### Post by russianboy1313 on 2007-07-11
WOOOHOOO finaly got it to work by typing:
sudo modprobe snd-cs4236 
^^^^

FINAL question do u guys know what is the cs4236 driver to since i thought my sound card is pentium?

---

### Post by davidsrsb on 2007-07-11
cs is crystal semiconducter, the sound chip maker.

The Intel 440BX is a motherboard chipset from the Pentium 2 era.

---

### Post by russianboy1313 on 2007-07-11
On the top right corner where the sound control is even as music playing, mute sign is still on (at least i think its a mute sign its a red square with an x through it)

Any ideas?

Another question, when i typed in "sudo modprobe snd-cs4236" is that all I have to do to get it working? Like should I type something else? Sorry if it sounds confusing more used to windows click and done rather than linux type and hope u don't get an error message

---

### Post by fredj on 2007-07-12
Double click on the loudspeaker icon in the system tray to open the alsa mixer. Check that your
soundcard is selected in the File -> Change Device menu. Then use the Edit ->Preferences menu to 
add all the needed volume controls and switches for playback and and record. Make sure they are
unmuted (no red crosses) and set volume levels. Then reboot and see if your sound works. 
Try the tests in System->Preferences->Sound on the taskbar.

---


---
title: "HP dv4-1222nr no sound with 9.04 (really can't get sound, really need advice)"
date: 2009-04-29
forum: Multimedia Software
---

### Post by nickfrazier1 on 2009-04-29
I just bought a HPdv4-122nr and I didn't receive sound upon installation of 8.10 or now that I've installed 9.04.

I've also updated 9.04 today since downloading but no luck.

My volume settings are listed as on, however my keyboard volume light stays set to mute.

It runs on an AMD Turion X2 64 bit with a ATI Radeon graphics card.
Listed are some of my hardware settings, if you know of any command(s) that may be of assistance I greatly appreciate your help.



01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
Subsystem: ATI Technologies Inc RS780 Azalia controller
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel


**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by nickfrazier1 on 2009-05-01
The following solved my sound problem for the HP dv4-1222nr.
I could not get sound AT ALL upon installation of ubuntu 8.10 or 9.04.

1.) Open a terminal and type in:

sudo getit /etc/modprobe.d/alsa-base

2.) This will open a new window, type in the following to the new window:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model= dell-m4-1

3.) Hit the save button on the new window to save this code.

4.) Go back to your terminal window and restart your computer by typing:

sudo reboot

5.) You computer should shut down and restart with functioning sound upon rebooting!


I would like to thank NAPLESBILL on this fix!!!!:popcorn:

---

### Post by sotoj159 on 2009-11-13
U know, i had the same problem on my 1222nr, but when i upgraded to Ubuntu 9.10, the problem went away.....i'm pretty sure that's wat fixed it

---

### Post by hulkeypoo on 2010-03-26
from the ubuntu audio trouble shooter page 
these commands worked to fix audio on 9.10 for a dv4-2145dx 
Also had to download the FGLRX video driver from ATI to get the Video control pannel - hope this helps  - Now have a great ubuntu laptop w/o the imperial entanglements present with other OS's:

cd ~
mkdir src
cd src
mkdir alsa
cd alsa
wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)
tar -xvpf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure
sudo make
sudo make install-modules

---


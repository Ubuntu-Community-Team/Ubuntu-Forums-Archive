---
title: "There is still no sound"
date: 2008-09-26
forum: Multimedia Software
---

### Post by CraztHorse07 on 2008-09-26
Hello everibody,

One more sound issue...

I finally decide to free from microsoft for ubuntu 8.04

But I have a big problem with sound : there is no sound at all. I just hear crrrrshhh crshhh when the drums should play. When I try to listen mp3 with Rhytmbox, it doesn't work.

I bought a Terratec Aureon 5.1 PCI, with the hope that it will better work than my incorporated Realtek. It doesn't...

On the french forum ('cause I live in this country), I tried to explain my problem, but nobody help me.

So I explain what I've already done :

fabien@CrazyHorse:~$ lspci -v
...
05:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
    Subsystem: TERRATEC Electronic GmbH Aureon 5.1
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 17
    I/O ports at d000 [size=256]
    Capabilities: <access denied>
...

Then :

fabien@CrazyHorse:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: CMI8738 [C-Media CMI8738], périphérique 0 : CMI8738-MC6 [C-Media PCI DAC/ADC]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: CMI8738 [C-Media CMI8738], périphérique 1 : CMI8738-MC6 [C-Media PCI 2nd DAC]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: CMI8738 [C-Media CMI8738], périphérique 2 : CMI8738-MC6 [C-Media PCI IEC958]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

Following a tutorial, I tried this :

fabien@CrazyHorse:~$ sudo modprobe snd-cmipci
fabien@CrazyHorse:~$ sudo gedit /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
snd-cmipci

(cmipci is the driver needed for my soundcard)

I saved this and reboot my computer. Still no sound...

Well. So I tried to compile alsa drivers :

sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

fabien@CrazyHorse:~$ sudo dpkg-reconfigure alsa-source

I choose cmipci, then pess Enter.

sudo module-assistant a-i alsa-source

OK. Reboot. There is still no sound. 

I begin to be quite anger. I decide to reinstall the drivers.

fabien@CrazyHorse:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 

Then :

fabien@CrazyHorse:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils 

Reboot. It still doesn't work.

Do somebody have an idea ?

---

### Post by markbuntu on 2008-09-26
That card should work out of the box. The C-Media chips are well supported. You can look in my guide here. It starts with the very basic troubleshooting:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---


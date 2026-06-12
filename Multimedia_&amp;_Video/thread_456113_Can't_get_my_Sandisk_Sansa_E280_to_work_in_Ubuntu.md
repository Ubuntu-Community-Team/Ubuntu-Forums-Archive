---
title: "Can't get my Sandisk Sansa E280 to work in Ubuntu"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by mrgod on 2007-05-27
Hi :)

I'm running Ubuntu 7.04, with Gnome. My goal is to mount the Sandisk Sansa E280 mp3-player as a normal disk mount and get Amarok to connect to the player. I can't get any of those to work

I have tried both MSC and MTP on my mp3-player, but there is no detection at all when I connect the player. I got an USB-HDD and ubuntu detects that one perfectly. I have also tried an another USB-port, but no detection happened.

lsusb shows:
Bus 003 Device 004: ID 0781:7421 SanDisk Corp.
Bus 003 Device 003: ID 152d:2338
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c03f Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

dmesg shows:
[ 6253.056461] usb 3-4: new high speed USB device using ehci_hcd and address 4
[ 6255.910920] usb 3-4: device descriptor read/64, error -110
[ 6261.144037] usb 3-4: unable to read config index 0 descriptor/start
[ 6261.144047] usb 3-4: chopping to 0 config(s)
[ 6271.138544] usb 3-4: string descriptor 0 read error: -110
[ 6281.132925] usb 3-4: string descriptor 0 read error: -110
[ 6291.127431] usb 3-4: string descriptor 0 read error: -110
[ 6291.127556] usb 3-4: no configuration chosen from 0 choices

As you see, the Sandisk is there, but the autodetect seems to fail...
Please, I really need help on this one...

Thanx for all help ! :)

---

### Post by darrglud1 on 2007-05-27
Is it a plays for sure device, and in Windoze does it show up as a Mass Storage Device? It detects my iPod without difficulty in ubuntu (well at least as a data drive).

Try leaving it plugged in and reboot, and try another usb port.

---

### Post by mrgod on 2007-05-27
> **darrglud1 said:**
> Is it a plays for sure device, and in Windoze does it show up as a Mass Storage Device? It detects my iPod without difficulty in ubuntu (well at least as a data drive).

Try leaving it plugged in and reboot, and try another usb port.


Yes, in windoze the player works fine in borh modus selections. I tried to reboot now, but still, nothing is happening...

---

### Post by darrglud1 on 2007-05-27
That's odd... Hmm... well you could google search the device followed by your distro.

---

### Post by mrgod on 2007-05-27
yes, indeed. I tried google for some hours now..and the forum..
It could be the firmware on the player, but since it works in win....
Pretty stuck right now... :(

---

### Post by mrgod on 2007-05-27
Is there any other part of this forum  that I should post this?

---

### Post by Zwack on 2007-05-29
Which firmware version are you using?  I know that certain firmware versions broke Mac compatibility, but I haven't had any issues (yet) with Linux and my version.

Z.

---

### Post by mrgod on 2007-06-08
> **Zwack said:**
> Which firmware version are you using?  I know that certain firmware versions broke Mac compatibility, but I haven't had any issues (yet) with Linux and my version.

Z.

I resently updated it to 01.02.18F. Quite interesting... what do happen when you connect your device? is it working in both MSC and MTP-mode?

Thanx for helping me out :)

---

### Post by nametaken on 2007-07-23
Found this surfin' the web, might help:

[http://wiki.freespire.org/index.php/Using_the_Sandisk_Sansa_E280_MP3_player](http://wiki.freespire.org/index.php/Using_the_Sandisk_Sansa_E280_MP3_player)

---


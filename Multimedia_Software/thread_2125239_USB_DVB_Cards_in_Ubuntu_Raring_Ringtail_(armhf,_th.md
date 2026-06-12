---
title: "USB DVB Cards in Ubuntu Raring Ringtail (armhf, through OTG)"
date: 2013-03-13
forum: Multimedia Software
---

### Post by zorglubinvader on 2013-03-13
Do we have support for USB DVB Cards in Ubuntu Raring  Ringtail (armhf) ? WinTV-Nova-T Stick is supported  (linux-firmware-nonfree) but nothing happens (no smsusb probing done)  when I plug it in my Nexus 7 (through OTG)...

[   93.090033] usb 2-1: new high speed USB device number 3 using tegra-ehci 
[   93.120587] usb 2-1: New USB device found, idVendor=2040, idProduct=c000 
[   93.120599] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[   93.120608] usb 2-1: Product: WinTV MiniStick 
[   93.120615] usb 2-1: Manufacturer: Hauppauge Computer Works 
[   93.120622] usb 2-1: SerialNumber: 4034184716

me@me-nexus:/lib/firmware$ uname -v
#27-Ubuntu SMP PREEMPT Tue Feb 19 17:43:44 UTC 2013 
me@me-nexus:/lib/firmware$ cat /etc/lsb-release
 DISTRIB_ID=Ubuntu DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"

---

### Post by zorglubinvader on 2013-03-13
Well, got some results as follows: I've installed the linux-headers packets. I did install a few modules after I built them (from [git.linuxtv.org/media_build.git]("http://git.linuxtv.org/media_build.git"))  Then I used MeTV (don't install vlc*)* to scan for the channels.  I could only tune and view the 1st channel on the list. Admittedly it was a bit laggy/glitchy and crashed quite often, but it worked in the end and I can watch tv w/ my Nexus 7 tablet   running Ubuntu! Hopefully the problems I encountered should get smoothed out anytime soon. ;D

---


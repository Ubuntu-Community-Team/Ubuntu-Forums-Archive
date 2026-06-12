---
title: "DVB-T AF9015 QT1010 Problems"
date: 2010-10-29
forum: Multimedia Software
---

### Post by simplybob on 2010-10-29
Hey guys,

My device is the PEAK 203244AGPK DVB-T USB Stick, and at the moment I'm trying to get it working in Ubuntu 10.10. It uses AF9015 and QT1010, and according to dmesg its set up properly, but for some reason I keep having problems.

I've managed to get it working fine in ME-TV, however some command line tools such as dvbtune dvbscan and w_scan will not work, and its these command line tools I need to use.

If anyone could help me out that would be great!

Thanks.

---

### Post by jjrp78 on 2011-01-05
it's hard to help without knowing what the problem is. What error messages are you getting?

a shot in the dark..are you sure that at the moment of trying to use those command line tool me-tv is closed? (not just the window but the application)

---

### Post by Jarvo on 2011-01-08
Hi Can anybody help? I have just bought a  PEAK 102569AGPK DVB-T Digital TV USB Stick. and Ubuntu 10.10 isnt seeing it... Digital TV set says ... Device not found....  Yet Windows XP sees it straight away so I know it works.

---

### Post by ginner on 2011-01-19
I have the same tuner and I am trying to get it working with Myth TV on Ubuntu. The USB has ID 1b80:d395

There is a guy [here]("http://aur.archlinux.org/packages.php?ID=36746") who appears to have got it working with scanning

> Comment by: Malcolm on Sat, 13 Nov 2010 12:11:00 +0000
I also had the problem where scanning found no channels. However after poking round a bit I found some newer source at [http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/dvb-usb-rtl2832u-1.4.2-3.2.src.rpm](http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/dvb-usb-rtl2832u-1.4.2-3.2.src.rpm). After extracting dvb-usb-rtl2832u-1.4.2-3.2.tar.bz2 (using rpmextract.sh), this built and worked perfectly including channel scanning. The only change I had to make was for my USB stick (Peak 102569AGPK) with USB ID 1b80:d395. I added #define USB_PID_KWORLD_WARM_5 0xD395 to rtl2832u.h and
{ USB_DEVICE(USB_VID_KWORLD_1ST, USB_PID_KWORLD_WARM_5) }, to rtl2832u.c. If anyone knows how to contact the upstream maintainer jvroosmalen, so that this new device can be added, I'd be grateful for the info (or better still if you are in contact with hiim anyway, please let him know). 

- but I'm new to linux and don't know what to do with .rpm files.

---


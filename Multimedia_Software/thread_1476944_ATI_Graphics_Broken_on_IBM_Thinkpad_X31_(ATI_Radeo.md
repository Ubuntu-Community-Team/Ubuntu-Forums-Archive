---
title: "ATI Graphics Broken on IBM Thinkpad X31 (ATI Radeon Mobility M6 -- that means old)"
date: 2010-05-08
forum: Multimedia Software
---

### Post by altonbr on 2010-05-08
I can seem to log in fine, but any game I launch has this error:

```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14

```It just seems like the graphics aren't setup properly. What can I do?

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
02:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

``````
$ cat /var/log/Xorg.0.log | grep vendor
(II) Module extmod: vendor="X.Org Foundation"
(II) Module dbe: vendor="X.Org Foundation"
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
(II) Module record: vendor="X.Org Foundation"
(II) Module dri: vendor="X.Org Foundation"
(II) Module dri2: vendor="X.Org Foundation"
(II) Module ati: vendor="X.Org Foundation"
(II) Module radeon: vendor="X.Org Foundation"
(II) Module vesa: vendor="X.Org Foundation"
(II) Module fbdev: vendor="X.Org Foundation"
(II) Module fbdevhw: vendor="X.Org Foundation"
(II) Module vgahw: vendor="X.Org Foundation"
(II) Module int10: vendor="X.Org Foundation"
(II) Module fb: vendor="X.Org Foundation"
(II) Module xaa: vendor="X.Org Foundation"
(II) Module theatre_detect: vendor="X.Org Foundation"
(II) Module evdev: vendor="X.Org Foundation"
``````
$ lsmod | grep -i fgl
``````
$ dmesg | grep fgl
``````
$ glxinfo
name of display: :0.0
Segmentation fault
``````
$ glxgears
Segmentation fault
```
```
$ uname -a; lsb_release -a
Linux pico-love 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
```

---

### Post by psychoelf on 2010-05-23
Same exact error here trying to run Neverwinter Nights.  Ran fine on Lucid 32bit, but not on 64bit.
```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14
```

Running Lucid 64bit with an ATI2600 mobility.

Catalyst 10.4 installed from ATI's website.

Any luck?


Edit:  Also tried reinstalling driver to no avail.  Cannot run Glxinfo or Glxgears, keep getting segmentation fault.

---

### Post by psychoelf on 2010-05-24
After some research, we don't have the same issue.  Mine was fixed by un-installing the catalyst driver from ATI's website and using the fglrx driver in the repos.

It looks like you have a Radeon 7000, which is old as you put it.  You can only use the open source driver [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver").

So if you are running the fglrx driver (ATI) then you need to uninstall it and just use the open source one (just follow the instructions on the page).

Hope that helps!

PS - I'm no expert, so double check and read the instructions on that page! :)

BTW this is where I found out about the M6
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000]("http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000")

---


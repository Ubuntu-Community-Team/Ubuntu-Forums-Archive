---
title: "EDUP Ralink Wireless USB issues with ndiswrapper"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by roadwarriormark on 2010-03-24
System specs:

compaq@compaq-desktop:~$ uname -a
Linux compaq-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

I made sure the system had all the latest updates on it, as of March 24


I followed this web page for what I describe below:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


I put the EDUP Wireless USB Adapter 54M in the ubuntu enabled machine, and it gets recognized:

compaq@compaq-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I check for support and find one for the USB Bus ID: 148f:2570, which is close to 148f:2070:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Ralink_USB_2.0_802.11g](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Ralink_USB_2.0_802.11g)


I install ndiswrapper per: 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


The installation cd came with XP drivers for the card, I tested the hardware and the drivers on XP, and then installed the XP drivers on ubuntu via System->Administration->Windows Wireless Drivers->Install new driver
Install on XP was painless.


I verify that the driver is being recognized by ndiswrapper:

compaq@compaq-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netr28u : driver installed
    device (148F:2070) present (alternate driver: rt2800usb)


I find that this means that there is an alternate driver which I need to blacklist from here, and adapt to use .conf file on ubuntu, so I blacklist and reboot, but the command gives the same output.  I check if it is in the file, and it is.  I also make sure netr28u is not blacklisted, just in case.

I also try removing that module and get this:
compaq@compaq-desktop:~$ rmmod rt2800usb
ERROR: Module rt2800usb does not exist in /proc/modules


I check that there are no errors loading the module:

compaq@compaq-desktop:~$ sudo depmode -a
[sudo] password for compaq: 
sudo: depmode: command not found
compaq@compaq-desktop:~$ sudo depmod -a
compaq@compaq-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
compaq@compaq-desktop:~$ tail /var/log/messages
Mar 24 16:28:01 compaq-desktop kernel: [   26.504264] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Mar 24 16:28:01 compaq-desktop kernel: [   26.504292] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Mar 24 16:28:01 compaq-desktop kernel: [   26.504299] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Mar 24 16:28:01 compaq-desktop kernel: [   26.504360] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Mar 24 16:28:10 compaq-desktop kernel: [   35.587469] UDF-fs: No VRS found
Mar 24 16:28:10 compaq-desktop kernel: [   35.587479] UDF-fs: No partition found (1)
Mar 24 16:29:51 compaq-desktop kernel: [  137.327321] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Mar 24 16:29:51 compaq-desktop kernel: [  137.327671] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 24 16:32:32 compaq-desktop pulseaudio[1585]: ratelimit.c: 5 events suppressed
Mar 24 16:43:23 compaq-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="707" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
compaq@compaq-desktop:~$ date
Wed Mar 24 16:50:31 PDT 2010


I try System->Administration->Windows wireless drivers and get:
Unable to see if hardware is present (popup window), then
Currently installed Windows Drivers:
netr28u Hardware present: Yes

I disabled the free drivers, b43 and ssb per blacklist instructions.



At one point I decided to try to compile the linux drivers supplied with the USB, and ran into several compilation errors involving packages which had been removed, so I think sticking with ndiswrapper is probably a simpler option for now.

The frustrating thing is that at one point I actually got the icon on the top right tray with the ethernet cable to show Wireless networks instead of just Wired networks, but it still wasn't working so I rebooted, but I never got it working that far again.

I'd appreciate a second set of eyes to see if I missed something,

Much appreciated,

Mark

EDIT: I got a bit further here with the help of this post:  [http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)

The card is now regonized and the light is blinking, and it can detect the various wireless networks that are around by name.

I still haven't managed to get it to connect yet though, but I think the driver issues are resolved.

---


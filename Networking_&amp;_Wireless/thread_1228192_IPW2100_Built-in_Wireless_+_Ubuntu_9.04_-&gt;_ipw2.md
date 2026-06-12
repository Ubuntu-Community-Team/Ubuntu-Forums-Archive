---
title: "IPW2100 Built-in Wireless + Ubuntu 9.04 -&gt; ipw2100-1.3.fw fails to load"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by cognos1 on 2009-07-31
Description of problem:
====================
By default, we installed 9.04 and the built in wireless card would not work.  I conducted the necessary debugging steps to diagnose what the problem was.  Based on my research, the default IPW and IEEE drivers/fw are the exact same as available on Source Forge (SF).  So, I followed the steps on the SF wiki (IEEE, IPW2100 - intel).  Found here:

IPW 2100 : [http://ipw2100.sourceforge.net/firmware.php](http://ipw2100.sourceforge.net/firmware.php)
IEEE80211:[http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)

Workaround attempts:
====================
1. Debug the issue with the default IPW 2100 drivers and fw include with 9.04.  I also searched for this problem using google and ubuntu forums but no solution matched my problem.
2. Compile from source - this failed with a tone of errors.  Seems that the kernel source was causing incompatibilities with the IPW2100 + IEEE80211 source.  I did some research on this in google but didn't come up with much ([http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1067](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1067)).

Since the compile from source failed, I was then forced to accept the fact that I couldn't use my wireless.  I am now just trying to help the others by following up on my issues and seeing if the community can help.

Please let me know if you require any further information/logs/debugging and I will be happy to do it.

Technical information from my laptop:
=================================
Laptop make: Toshiba Tecra M2

System logs:
------------------

sudo lshw -C network:
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=34 mingnt=2
  *-network:1
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 03
       serial: 00:0e:7b:49:05:06
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=9.24.165.72 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:7f:67:8a:91:68
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

lsmod:
mickey@isha:~$ lsmod | grep -i ipw
ipw2100                79536  0 
ieee80211              38344  1 ipw2100

 dmesg | grep ipw
[   12.312873] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   12.312877] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   12.382158] ipw2100 0000:02:05.0: found PCI INT A -> IRQ 11
[   12.382170] ipw2100 0000:02:05.0: sharing IRQ 11 with 0000:00:1d.2
[   12.382181] ipw2100 0000:02:05.0: sharing IRQ 11 with 0000:00:1f.1
[   12.382772] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   12.382787] ipw2100 0000:02:05.0: firmware: requesting ipw2100-1.3.fw
[   12.482940] ipw2100: eth1: Error initializing Symbol
[   12.483009] ipw2100: eth1: Error loading microcode: -5
[   12.483080] ipw2100: eth1: Failed to power on the adapter.
[   12.483147] ipw2100: eth1: Failed to start the firmware.
[   12.483210] ipw2100Error calling register_netdev.
[   12.483457] ipw2100: probe of 0000:02:05.0 failed with error -5


lspci -v:
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
    Subsystem: Intel Corporation Device 2580
    Flags: medium devsel, IRQ 11
    Memory at fceff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
    Kernel modules: ipw2100

uname -a:
Linux isha 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


Thank you for looking at this post.

---

### Post by tydie1 on 2009-08-01
I have the same problem.

---

### Post by figosound on 2009-10-25
BUMP!

I got the same problem either... On an Acer aspire 2001 wlci: lshw give me this:

*-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1
                version: 04
                serial: 00:04:23:8d:3a:35
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated

The card picks up signal from other routers, but not from mine, i think because of a wpa problem; also, kernel see my wireless card as eth1 instead of wlan0...

PLease, any help will be much appreciated :-)

---


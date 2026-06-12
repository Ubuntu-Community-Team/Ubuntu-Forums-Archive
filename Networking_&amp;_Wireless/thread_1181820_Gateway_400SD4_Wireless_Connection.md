---
title: "Gateway 400SD4 Wireless Connection"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Vaxon on 2009-06-08
This is the laptop I'm running

[http://support.gateway.com/s/Mobile/Gateway/400SD4/3501309nv.shtml](http://support.gateway.com/s/Mobile/Gateway/400SD4/3501309nv.shtml)

my wireless is not working

lspci

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)


[FONT=monospace]ls[/FONT]usb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:4f:51:e8  
          inet addr:68.117.243.25  Bcast:68.117.243.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe4f:51e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65531485 (65.5 MB)  TX bytes:3930526 (3.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.



lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:e0:b8:4f:51:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=68.117.243.25 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:a4:dd:a5:91:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


pleading to you upon my kness I beg for help

---

### Post by Vaxon on 2009-06-08
bump?
I would really appreciate help

---

### Post by Flash3780 on 2010-10-18
Has a solution to this issue been found? I recently got my hands on an identical laptop and it's having similar problems - unable to resolve a DHCP connection. Upon pouring through every forum posting that I could find on the subject, I'm not making much progress (I'm a bit of a Linux newbie).
I understand this laptop comes equipped with a Lucent/Agere (*ORiNOCO*) wireless card, which I don't think it supported by ndsiwrapper.
Research tells me that previous releases of Fedora (and I assume Ubuntu) "just worked" with the 400SD4 wireless, so perhaps something broke between releases. I'm suspecting a driver problem, but who knows...
Anyhow, any input on the subject would be much appreciated.

---

### Post by Flash3780 on 2010-10-19
Tried this:
[http://ubuntuforums.org/showthread.php?t=1593250&page=3](http://ubuntuforums.org/showthread.php?t=1593250&page=3)
To no avail. However, I was able to plug in a Netgear wireless card and everything works swimmingly.

I suppose that this isn't exactly a fix, though.

---


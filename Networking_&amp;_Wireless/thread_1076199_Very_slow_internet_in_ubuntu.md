---
title: "Very slow internet in ubuntu"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by MrNatewood on 2009-02-21
On the same machine in windows XP with same DHCP setting Internet is fine and smooth 
and downloads are fast.
In my newly installed ubuntu 8.10 internet is very very slow if it's working at all, and downloads never reach 20 kb/sec(in windows it reaches around 190 kb/sec)
this is the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:e0:18:b0 b:51  
          inet addr:192.168.1.217  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:2711 errors:824 dropped:0 overruns:0 frame:1305
          TX packets:2843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1312579 (1.3 MB)  TX bytes:315941 (315.9 KB)
          Interrupt:19 Base address:0x9800 
```

I have searched this forum for solutions and tried disabling ipv6 and rebooted, which did not help

---

### Post by Kevbert on 2009-02-21
Please post the output of
```
ifconfig
iwconfig
```
It may be a signal strength problem (just co-incidence that it's better in Windows) or it may be a driver problem. How did you get your wireless adapter to work and what make and model is it ? You can get the make/model info with
```
lspci
```
or if it's usb
```
lsusb
```
(list pci and list usb devices).

---

### Post by MrNatewood on 2009-02-21
Sorry I didn't mention it,
It is a _wired_ connection.
lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
00:0e.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

```
Edit: Also tried fiddling with the MTU, didn't help either.

---

### Post by superprash2003 on 2009-02-21
did you successfully make the change?? post ifconfig after making the MTU change.. you could also try opendns servers - 208.67.222.222 and 208.67.220.220 .. also try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by MrNatewood on 2009-02-22
> **superprash2003 said:**
> did you successfully make the change?? post ifconfig after making the MTU change.. you could also try opendns servers - 208.67.222.222 and 208.67.220.220 .. also try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

Yes, I ran ifconfig afterwards and the mtu changed successfully. Also tried opendns and disabling ipv6(ran "ip a | grep inet6" from terminal and no output). This is all on a friend's computer so I can't give the outputs at the moment.

None of this helped.

I also tried the opensuse and mandriva livecds to see if the problem persists and it does. Internet is incredibly slow on all 3 distributions(i did not actually install suse and mandriva, just used the livecd)

---

### Post by MrNatewood on 2009-02-25
bump. anyone?

---

### Post by ChrisBlizzard on 2010-02-16
Ok so SiS may well be the least Linux-unfriendly company ever, but...

Why, with so many geeky minds using Linux can NO ONE come up with decent solutions to those unfortunate enough to have their components in our laptops?

My internet is sooooooo slow through Ubuntu

I guess its a choice between speed and security once again.

Can anyone help?

---

### Post by northd_tech on 2010-02-20
You might want to check these threads about disabling IPv6 and OpenDNS:

[http://ubuntuforums.org/showthread.php?t=1410595](http://ubuntuforums.org/showthread.php?t=1410595)

[http://ubuntuforums.org/showthread.php?t=1405129](http://ubuntuforums.org/showthread.php?t=1405129)

---


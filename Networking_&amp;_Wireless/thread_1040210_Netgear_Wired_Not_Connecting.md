---
title: "Netgear Wired Not Connecting"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by xx.canes.rites on 2009-01-15
Ok I have a Netgear modem that I received from Time Warner Cable which the internet was working fine on my XP setup. I installed Ubuntu 8.10, finally got tired of windows, yet my internet will not connect even though my computer in the other room which is still using windows can. 

On my network configuration, it says eth0 | Never, I have no clue what that is. My MAC Address seems to be okay, because I deleted my interfaces file then rebooted and it reset to original coding.

I'm trying to get my internet up and working so I can install world of warcraft through wine and start playing on my Unbuntu, hopefully getting better frame rates. So if anyone could help me out, I would appreciate it. 

```
eth0      Link encap:Ethernet  HWaddr 00:16:76:6d:76:d0  
          inet6 addr: fe80::216:76ff:fe6d:76d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Maybe I can just manually enter my information so I may connect. Could someone post me the commands I can enter to get the information needed so I may manually setup my network configuration(i.e. DNS info, MAC addr, IP, etc). Thank you in advance, I'll be near the comp for replies :)

---

### Post by superprash2003 on 2009-01-15
this should help you setup ip manually [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html) .. but if DHCP is on in your modem/router.. then typing sudo dhclient eth0 should fix the issue

---

### Post by xx.canes.rites on 2009-01-15
> **superprash2003 said:**
> this should help you setup ip manually [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html) .. but if DHCP is on in your modem/router.. then typing sudo dhclient eth0 should fix the issue

Neither options worked. On dhclient it just said no dhcp leases offered. eth0:avahi is what's available on my network which i can't even edit for some reason and networking restart didn't even apply the new connection i setup manually. :( I dunno what's going on.

---

### Post by xx.canes.rites on 2009-01-15
> **superprash2003 said:**
> this should help you setup ip manually [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html) .. but if DHCP is on in your modem/router.. then typing sudo dhclient eth0 should fix the issue

```
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port

00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600GT (rev a1)

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
  *-network               

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 2

       bus info: pci@0000:02:02.0

       logical name: eth0

       version: 10

       serial: 00:16:76:6d:76:d0

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 86:8e:32:05:34:06

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Also eth0:avahi on my network is getting an error. It says cannot find information on etho:avahi on /proc/net/dev

---

### Post by xx.canes.rites on 2009-01-15
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10):::Those drivers seem to be just plain s*it on ubuntu, so I just installed a new Eth card I had and it works fine now. Im marking as solved. Solution=Get rid of pos HW

---

### Post by superprash2003 on 2009-01-16
glad you got it to work.. the THREAD SOLVED and THANKYOU feature is currently disabled.. so you wont be able to mark this thread as SOLVED as of now.!!

---

### Post by xx.canes.rites on 2009-01-17
yea I was wondering why I couldn't mark as solved, haha. I was like, O man someone's gonna be pissed lOL. Haha thanks for letting me know!

---


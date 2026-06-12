---
title: "Network and Sound Stopped Working"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by JasonSilver on 2010-08-02
Last night I was trying to get my printer working, and when I rebooted, I lost networking and sound.

I am currently booting on a live CD, and sound and networking are fine-- so it can't be a hardware issue (obviously). I must have inadvertently broken something, but I can't figure it out.

I have tried restarting networking, but it doesn't respond-- it says stop/waiting or something like that.

I can't access the sound preferences-- it says waiting for sound to respond (or something like that).

When I reboot, sometimes I see a terminal window with the same line scrolling very, very quickly-- something about waiting for USB.

Additionally, the system is very slow to respond-- clicking a menu item can take a long time for it to appear, etc.

What could have occurred, and how might I troubleshoot it?

Thanks,
Jason Silver

---

### Post by JasonSilver on 2010-08-02
Does this belong in another forum?

---

### Post by JasonSilver on 2010-08-02
Some more information.

The systems is so unresponsive because pulseaudio is trying to connect or something.... if I try to kill a pulseaudio process, it says process not found, and there's a new PID for it already... it uses a crazy amount of processor (200% apparently) at times.

If I kill Xorg, I get a stream of messages similar to this:

12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
... on down the screen ...

lsusb is:
```

ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0461:0a00 Primax Electronics, Ltd Micro Innovations Web Cam 320
Bus 005 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 005 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0d8d:0105 Promotion & Display Technology, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I'm not sure what's wrong with the networking, I'm trying to connect with wireless, so maybe it's a USB issue as well?

ALSO I tried the previous kernel, and that didn't get me anywhere.

Anyone give me any direction at all? Where should I look next?

Thanks!
Jason

---

### Post by Iowan on 2010-08-02
Not to interrupt a "private" conversation (;)), but check (from a terminal - Applications>Accessories>Terminal): **ifconfig -a**.  If no IP addresses show up for wireless or eth0, check **sudo lshw -C network ** (post if possible).

---

### Post by JasonSilver on 2010-08-02
> **Iowan said:**
> Not to interrupt a "private" conversation (;)), but check (from a terminal - Applications>Accessories>Terminal): **ifconfig -a**.  If no IP addresses show up for wireless or eth0, check **sudo lshw -C network ** (post if possible).

Thanks! Finally a response.

```

~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1e:68:1f:4e:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16330 (16.3 KB)  TX bytes:16330 (16.3 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:37:94:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

~$ sudo lshw -C network
[sudo] password for jasonsilver: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:1f:4e:a2
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:37:94:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f0200000-f0201fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by JasonSilver on 2010-08-03
bump

---

### Post by dineshs on 2010-08-04
Please run ```
sudo dhclient eth0
``` and see if you are getting IP
Note:Your lshw output says>  product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
and the driver loaded is
> driver=r8169
Will it be a problem?
[http://ubuntuforums.org/archive/index.php/t-1054480.html](http://ubuntuforums.org/archive/index.php/t-1054480.html)

---

### Post by JasonSilver on 2010-08-04
Thanks so much for replying!

I am currently connected via the Live USB using this very hardware-- so it isn't a hardware issue but a software issue.

Somehow or another, networking has been turned off and doesn't want to turn back on. I don't understand why it's so hard to figure out the problem.

Anyone else? please?? :)

---

### Post by JasonSilver on 2010-08-05
bump

---

### Post by Iowan on 2010-08-05
I haven't done virtual, so the **vboxnet0** info under **ifconfig -a** leaves me cold. Was it there before? 
What's in */etc/network/interfaces*? Ordinarily, it's just a couple of lines defining "lo".

---

### Post by JasonSilver on 2010-08-05
That's just so when I start up my XP virtual box inside ubuntu, I can connect to the network-- it isn't connected to the problem, afaik.

Jason

---


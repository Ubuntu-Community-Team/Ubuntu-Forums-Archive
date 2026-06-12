---
title: "Linksys router - won't connect"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by UmlautBanana on 2010-08-11
I have a linksys router, and internet doesn't work on Ubuntu 9.10 and above for me. I think I need a driver, but I don't know where to find it. I'm sure someone here will know what my problem is; someone on the IRC told me to type sudo apt-get install in the terminal and pastebin the output.

---

### Post by Iowan on 2010-08-11
Anything behind the "sudo apt-get install"? (program name?) 
Is problem with wired, wireless, or both?

---

### Post by keithclark on 2010-08-11
> **UmlautBanana said:**
> I have a linksys router, and internet doesn't work on Ubuntu 9.10 and above for me. I think I need a driver, but I don't know where to find it. I'm sure someone here will know what my problem is; someone on the IRC told me to type sudo apt-get install in the terminal and pastebin the output.

Which router?  Wired or wireless?  Have you tried both?

Keith

---

### Post by UmlautBanana on 2010-08-11
Hm, well I haven't tried with wired before. I'll try that tomorrow when I get a chance.

---

### Post by UmlautBanana on 2010-08-12
Okay, I tried, and it doesn't work with wired either.

Offtopic: why are all the forum levels based on coffee?

---

### Post by UmlautBanana on 2010-08-13
bump.

---

### Post by Iowan on 2010-08-13
> **UmlautBanana said:**
> Okay, I tried, and it doesn't work with wired either.

Offtopic: why are all the forum levels based on coffee?

There's a nice, informative [post]("http://ubuntuforums.org/showthread.php?t=1006656") around here somewhere that explains that...

In the meantime - post results of **ifconfig -a** and **sudo lshw -C network**. :)

---

### Post by UmlautBanana on 2010-08-16
Hm, well, Notepad didn't show the line breaks, but make out of this what you will.

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:a7:23:ab
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:0c:a1:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```Oh, the line breaks show here. Odd... anyway, that output was from sudo lshw -C network. This is from ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr a4:ba:db:a7:23:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:0c:a1:7e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Hope you can make something of  that, 'cause I sure can't.

---

### Post by UmlautBanana on 2010-08-16
Hm, well, Notepad didn't show the line breaks, but make out of this what you will.

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:a7:23:ab
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:0c:a1:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```Oh, the line breaks show here. Odd... anyway, that output was from sudo lshw -C network. This is from ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr a4:ba:db:a7:23:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:0c:a1:7e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Hope you can make something of  that, 'cause I sure can't.

---

### Post by UmlautBanana on 2010-08-16
Hm, well, Notepad didn't show the line breaks, but make out of this what you will.

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:a7:23:ab
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:0c:a1:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE  802.11bg
```Oh, the line breaks show here. Odd... anyway, that output  was from sudo lshw -C network. This is from ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr a4:ba:db:a7:23:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:0c:a1:7e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Hope you can make something of  that, 'cause I sure can't.

---

### Post by UmlautBanana on 2010-08-16
Hm, well, Notepad didn't show the line breaks, but make out of this what you will.

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:a7:23:ab
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:0c:a1:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE  802.11bg
```Oh, the line breaks show here. Odd... anyway, that output  was from sudo lshw -C network. This is from ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr a4:ba:db:a7:23:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:0c:a1:7e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Hope you can make something of  that, 'cause I sure can't.

---

### Post by UmlautBanana on 2010-08-16
This used to be a double post because of connection problems. Since I don't see a delete button, I figured this made more sense than making it a triple post to say "Sorry for double post".

...Okay, there was like a quintuple post. I got a 502 error after a long wait after Submit Reply, and I thought it didn't post my reply... sorry.

---

### Post by UmlautBanana on 2010-08-17
bump

---

### Post by UmlautBanana on 2010-08-17
Okay, it works on wired. Turns out I was connecting the wrong cable. I installed a driver and now sudo lshw -C network says UNCLAIMED. There's another driver available, but when I try to download it it says "installArchives() failed".

---

### Post by UmlautBanana on 2010-08-17
Okay, the drivers both installed fine. My network, however, isn't detected automatically, and when I try to enter its name, it tries to connect for a few minutes, then fails.

---

### Post by UmlautBanana on 2010-08-17
bump

---

### Post by UmlautBanana on 2010-08-17
bump, partly because I want help and partly because I hate the number 13.

---

### Post by Iowan on 2010-08-17
#13 was 4 posts ago... ;)
Once/day is considered "polite" for bumping.
> **UmlautBanana said:**
> ... My network, however, isn't detected automatically.... Is this the wired or wireless network?

---

### Post by UmlautBanana on 2010-08-18
Oh, okay. That's the wireless network; the wired network works fine.

---

### Post by UmlautBanana on 2010-08-19
bump

---

### Post by UmlautBanana on 2010-08-20
bump..

---

### Post by UmlautBanana on 2010-08-21
aghthisisstartingtogetonmynervesbump.

---

### Post by UmlautBanana on 2010-08-23
bump, does anyone care anymore?

---

### Post by 10snoopy1 on 2010-08-23
> **UmlautBanana said:**
> bump, does anyone care anymore?

I am assuming you are using wireless. Did it work in 9.04?

I am assuming you have internet access. Try this:

Go to System -> Administration -> Software Sources

Select the pre-release updates and unsupported updates. Reload package data. 

System -> Administration -> Hardware Drivers

Check for a driver there.

Is this on a laptop, desktop, or netbook?

Install any updates that come up as they may help you.

---

### Post by UmlautBanana on 2010-08-23
Yeah, it worked in 9.04. Maybe I'll just get that until I get this problem sorted out.

It works with a wired connection, so when I get the chance I'll look for updates and drivers. It's on a laptop.

---

### Post by UmlautBanana on 2010-08-24
bump fer today.

---

### Post by 10snoopy1 on 2010-08-24
> **UmlautBanana said:**
> Yeah, it worked in 9.04. Maybe I'll just get that until I get this problem sorted out.

It works with a wired connection, so when I get the chance I'll look for updates and drivers. It's on a laptop.



I know some laptops have suffered with the new releases... Use 9.04 until 10.10 comes out... Or even better (unless this is a production machine and you don't make backups) is to use 10.10 alpha 3

---

### Post by UmlautBanana on 2010-08-26
Thanks! Where do I get 10.10 alpha 3?

---

### Post by 10snoopy1 on 2010-08-26
> **UmlautBanana said:**
> Thanks! Where do I get 10.10 alpha 3?

You can get it here:
[http://cdimage.ubuntu.com/releases/10.10/alpha-3/](http://cdimage.ubuntu.com/releases/10.10/alpha-3/)
Choose the desktop one. If you know what operating system it came with (Windows 64 bit or 32 bit) then you can choose the right type. Otherwise, I would go with the x86 (32 bit) one which usually works better.

---

### Post by 10snoopy1 on 2010-08-26
You will have to use a CD and burn the image to it though... Use 1/2 or 3/4 of the speed the disc says it can support and that should work well... 

To put it onto a flash drive, have a 1GB or larger flash drive and boot off of a live disc and use the USB startup disc creator. This is required for installing on netbooks. Optional for laptops and desktops if you have the disc handy

---

### Post by mathia on 2010-09-16
Hi,
please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---


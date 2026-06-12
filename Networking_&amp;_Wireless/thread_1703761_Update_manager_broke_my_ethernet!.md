---
title: "Update manager broke my ethernet?!?"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by whein on 2011-03-09
Writing this from a 9.10 LiveCD, so I know that my hardware is working fine.

My system is running 10.10 normally.  Last night, the update manager popped up, as it frequently does, and said I had some packages that could be updated.  So I let it update after which it said I needed to reboot.  So I did, and now it doesn't recognize my network connection, and even the blinky lights on the port itself stay dark.  HELP!!!

I don't know a lot about networking or stuff under the hood, but I can work a console and/or text editor if someone can tell me where to look and what to type.

My hardware is (from "lspci | grep -i eth"):
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

The packages that have a modified date of last night are:
ubuntuone-client-gnome_1.4.6-0ubuntu2_amd64.deb
python-ubuntuone-client_1.4.6-0ubuntu2_all.deb
libsyncdaemon-1.0-1_1.4.6-0ubuntu2_amd64
ubuntuone-client_1.4.6-0ubuntu2_all.deb
python-aptdaemon-gtk_0.31+bzr506-0ubuntu6.2_all.deb
python-aptdaemon_0.31+bzr506-0ubuntu6.2_all.deb
aptdaemon_0.31+bzr506-0ubuntu6.2_all.deb
tzdata-java_2011c-0ubuntu0.10.10_all.deb
tzdata_2011c-0ubuntu0.10.10_all.deb
gnome-screensaver_2.30.0-1ubuntu1.1_amd64.deb

Anyone able to point me in the right direction?

-Will

---

### Post by Iowan on 2011-03-09
What are results (from a terminal) of **sudo lshw -C network**?
Does **ifconfig -a** show the interface active?

I'll need to review some old links I have which were about networking issues on suspend/hibernate. I think I have one about networking getting disabled, too...

---

### Post by whein on 2011-03-09
So, for the (broken) 10.10 system I got
```
whein@HappyDrive01:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:0e:1b:a2
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:e800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:febe0000-febfffff
whein@HappyDrive01:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:0e:1b:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:0e:1b:a2  
          inet addr:169.254.6.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2109 (2.1 KB)  TX bytes:2109 (2.1 KB)

whein@HappyDrive01:~$
```

and for the working 9.10 LiveCD system I got
```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:0e:1b:a2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.8 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6ff8000-f6ffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:0e:1b:a2  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe0e:1ba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1887622 (1.8 MB)  TX bytes:172829 (172.8 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8693 (8.6 KB)  TX bytes:8693 (8.6 KB)

ubuntu@ubuntu:~$ 
```
I notice one of the differences between the two is the eth0:avahi section in the broken one.  I remember the update manager having a lot of entries about avahi this and that.  How do I fix/remove it?

-Will

---

### Post by chili555 on 2011-03-09
Does this system dual-boot with Windows?

---

### Post by whein on 2011-03-09
> **chili555 said:**
> Does this system dual-boot with Windows?

*Shudder.*  Nope, been MS-free for several years now.  I don't even have any of the original hardware from that system, although I suppose the infection could have passed along as I upgraded a piece at a time and not the whole system in one go.

But seriously, I have wiped, reformatted, and reinstalled ONLY Ubuntu at least a handful of times on this system so there is no way that Windows is lurking anywhere.  This was purely a Linux snafu, sadly.

-Will

---

### Post by Iowan on 2011-03-09
For whatever reason (:confused:), I notice the 10.10 is running half-duplex @10MB/s whereas the 9.10 LiveCD is full-duplex @100MB/s

---

### Post by matt_symes on 2011-03-09
Hi

The interface is up so that is good.

Your Ethernet card does not have an Ethernet address assigned to it. Do you normally use DHCP to assign an address or do you use a static address ?

Assuming DHCP, what is the output of (from a terminal)

```
sudo dhclient eth0
```

Avahi is used for discovery on a network. 

[http://avahi.org/](http://avahi.org/)

Kind regards

---

### Post by chili555 on 2011-03-09
Most important, in my opinion; from the hard-drive install:> duplex=half latency=0 [COLOR="Red"]link=no[/COLOR] From the live CD:> duplex=full ip=192.168.0.8 latency=0 [COLOR="Red"]link=yes[/COLOR]If there is no link, the issue of half- or full-duplex is trivial. How to fix it? Not quite sure, yet. Googling......> *Shudder.* Nope, been MS-free for several years nowA man, woman or alien being after my own heart!!!

---

### Post by chili555 on 2011-03-09
Here is an interesting idea: [http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem](http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem)

Since we don't typically use /etc/network/interfaces, you might try dropping this line into /etc/rc.local above exit 0:```
ethtool -s eth0 autoneg off
```If it doesn't come up at 100Mb/s, you could add another line following:```
ethtool -s eth0 speed 100
```Of course, if it's not already installed, you'll need to install ethtool.

---

### Post by chili555 on 2011-03-09
Another approach; it ought to work just as well: [http://fedoraforum.org/forum/showthread.php?p=1401944](http://fedoraforum.org/forum/showthread.php?p=1401944)

---

### Post by Iowan on 2011-03-09
> **chili555 said:**
> If there is no link, the issue of half- or full-duplex is trivial. I noticed that, too - didn't know if link was cause or effect ;)

---

### Post by matt_symes on 2011-03-09
Hi

> **Iowan said:**
> I noticed that, too - didn't know if link was cause or effect ;)

Hell, well i didn't notice that at all. Gold stars to both of you :KS
Must be daylight where you guys are. :D

Kind regards

---

### Post by whein on 2011-03-10
> **chili555 said:**
> Here is an interesting idea: [http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem](http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem)

Since we don't typically use /etc/network/interfaces, you might try dropping this line into /etc/rc.local above exit 0:```
ethtool -s eth0 autoneg off
```If it doesn't come up at 100Mb/s, you could add another line following:```
ethtool -s eth0 speed 100
```Of course, if it's not already installed, you'll need to install ethtool.

So adding the first line made me able to access the network again from 10.10, but I am still curious what the updates did that took a previously working system and made it not work without this line?  

One of my big complaints against Microsoft has always been that installing a patch or an update might really break something and you have little or no warning or options.  I know this is an isolated incident but I really hope Ubuntu is not going down this road...  If I hadn't had a LiveCD sitting around and known about the forums I would have essentially bricked my computer and had to reinstall from scratch (and then not updated ANYTHING!)  Jeebus help the newbie convert from Windows who has the same problem.

That said, major thanks to the forum posters who helped me.  :)

-Will

---


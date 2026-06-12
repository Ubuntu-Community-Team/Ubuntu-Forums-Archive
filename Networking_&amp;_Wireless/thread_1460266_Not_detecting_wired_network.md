---
title: "Not detecting wired network"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by aeriph on 2010-04-22
My installation has stopped detecting my wired network. Another computer connects fine with the same cable to the same access point. As far as I can tell it is simply behaving as if there was no network available from that cable but obviously there is. It was working a couple of hours ago, and I didn't install or uninstall anything, just shut down and booted up again. I can only guess that a security update was automatically installed and broke something?

LAN is enabled in the BIOS

ifconfig does display eth0

ifup eth0 returns "Ignoring unknown interface eth0=eth0"

in the output from dmesg:
"ADDRCONF(NETDEV_UP): eth0: link is not ready"

network appears in lshw and is not listed as disabled


what other information would be useful for diagnosing this problem?

---

### Post by Iowan on 2010-04-22
I presume **ifconfig -a** shows no IP address for eth0. If possible, post results of **sudo lshw -C network**.

---

### Post by bowarwick on 2010-04-23
I'm having the exact same problem. My wireless works great-- but ubuntu's not detecting any wired connections.

I had this problem a week ago and it  fixed itself the next day! But now it's broken AGAIN, and I don't know what to do. I'd rather not pray and just wait...

Last time I had this problem someone mentioned that it looked like my wireless got set as eth0 some how. Also, notice how it says that my ethernet interface is disabled. I wonder what that's about?

Here's something for you gurus to look at:

```
bo@bigfoot:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:19:7e:d3:02:ba  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fed3:2ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2585 errors:0 dropped:0 overruns:0 frame:167
          TX packets:2398 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2793727 (2.7 MB)  TX bytes:438294 (438.2 KB)
          Interrupt:17 Base address:0xc000 

eth1_rename Link encap:Ethernet  HWaddr 00:1c:23:87:c6:77  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

bo@bigfoot:~$ **sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 01
       serial: 00:19:7e:d3:02:ba
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.14 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1_rename
       version: 02
       serial: 00:1c:23:87:c6:77
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:f9bfe000-f9bfffff

```Thanks for any help you can give.

---

### Post by hayleymae on 2010-04-25
omg i'm having the exact same issue too

at first i thought my ethernet cable got damaged but when i plugged it into my moms computer, it worked fine. 

so then i thought maybe it was jaunty so i booted into xp and it doesn't work there either and xp says there's nothing wrong with my network card or the drivers


so i have no idea what to do. the only reason i'm connected to the internet now is because my neightbors have wireless

---

### Post by legatek on 2010-04-29
I was struggling with this issue on a new install of 10.4 beta for a couple of days, and none of the fixes in the forums worked. Finally I blacklisted IPV6 and the wired connection is stable.

Add the following line to /etc/modprobe.d/blacklist.conf:

blacklist ipv6

---

### Post by aeriph on 2010-04-29
I know this isn't helpful, but after cutting mains power to my PC (not just shutting down) and then restoring it, everything worked again. Seems a bit magicky, but it worked after that for me.

---

### Post by nur fadilah on 2010-06-01
lolz..i'm also got the same problem.

---

### Post by jpeery on 2010-06-01
Same here, neither wired or wireless is working <grumble> good thing I've got my MAC (zipping up flame retardent suit)

So any fix?

---

### Post by surfh2o on 2010-06-07
I was having the same issue after my machine had been off all weekend.  It's possible that we had a power issue here.  Anyways after trying a few things and then reading this.  I took the advice to kill main power.  I pulled the plug from the back, reseated and rebooted and it worked.

---

### Post by Iowan on 2010-06-07
Folks:
If the "pull the plug" advice worked for you, feel free to acknowledge. If you're still having similar problems, please start a new thread so you can receive user-specific advice. It also makes it easier to mark the problem [SOLVED] when/if that happens. :)

---

### Post by airdao on 2010-07-18
> **Iowan said:**
> Folks:
If the "pull the plug" advice worked for you, feel free to acknowledge. If you're still having similar problems, please start a new thread so you can receive user-specific advice. It also makes it easier to mark the problem [SOLVED] when/if that happens. :)


OK, It seems that the problem is happening after the PC/laptop comes back from hibernation or any "power saver" option. you can see it after you run the 

ipconfig -a 

the wired link will displayed as "eth1_rename Link encap"

Turning the computer completely off and unplugging it (take batteries off if laptop) seems to resolve the issue.

Don't know why, but it looks to be specific to Ubuntu Lucid

---


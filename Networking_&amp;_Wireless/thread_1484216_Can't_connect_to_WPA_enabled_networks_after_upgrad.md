---
title: "Can't connect to WPA enabled networks after upgrading to Lucid Lynx/ Ubuntu 10.04"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2010-05-15
I decided to upgrade to Ubuntu 10.04 a few days ago. My internet then stopped working. It's a few days later and I think I've been able to pinpoint the problem but still don't have a solution.

I changed the security for my network to WEP (instead of WPA) and I'm able to connect to it just fine after seeing a possible fix here.

[http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html)

The guide is for Ralink RT2860 chipsets but I'm using a RT2800 chipset and I can't find a driver for it here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)


Is there another way around this problem or can I just download another driver? I do not intend to stick with a WEP secured network.

Just in case:

```
$ sudo lshw -C network
[sudo] password for ****: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:b5:70:ba
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:c000(size=256) memory:e7010000-e7010fff(prefetchable) memory:e7000000-e700ffff(prefetchable) memory:e7020000-e702ffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 24
       serial: 00:10:4b:6d:16:c7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:d000(size=128) memory:e5000000-e500007f memory:80400000-8041ffff(prefetchable)
  [COLOR="Red"]*-network:1
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:3b:14:08
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.189 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:e6000000-e600ffff[/COLOR]
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: ham0
       serial: 86:08:3a:c1:4a:b2
       size: 10MB/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=5.219.57.164 link=yes multicast=yes port=twisted pair speed=10MB/s

```

---

### Post by tixetsal on 2010-05-15
Same problem here.  10.04 amd64, rt2800 wireless, wpa2 can't connect.  Hardware is not at fault.

---

### Post by tixetsal on 2010-05-15
In my set of circumstances, I was able to solve this problem with an unexpected workaround.  I kept noticing that other folks were using WPA2 Personal Mixed, which is what I was doing.  

I changed the settings in my (dd-wrt) router to use WPA2 Personal ONLY, instead of WPA2 Personal Mixed.  At this point in my troubleshooting, my ability to establish a wireless connection increased somewhat, but the success rate was still unacceptable.

I then changed my WPA Algorithm from TKIP+AES to just AES and rebooted my router.  I have been able to reconnect almost 10x in a row, after reboots, etc, which has been impossible for the last 24 hours since switching to WPA2 from WEP.

I was in the process of looking at methods of building a new driver for the card, but this is suitable for my needs and was much easier.

I hope this helps someone...

---

### Post by -jay- on 2010-05-15
i use wpa personal 2 with out any problems i wouldnt use wep not really secured

---

### Post by CrazedKeebler on 2010-06-04
Hello all,

I have been using my Eee PC with lucid to configure a wireless access point installation, and is connects only when the access point is set to WEP or WPA2 with only aes. In mixed WPA/WPA2 it fails to connect repeatedly.

Anyone figure out a solution???

---

### Post by mrashley on 2010-06-24
I'm also having this problem. I have an HP laptop that doesn't mind, but my EeePC won't connect to the network. :(

---

### Post by mahasmb on 2010-07-14
I JUST HAD THIS PROBLEM AGAIN!

It's seems the first time I didn't bother to come back to verify that I had found a solution. Which really cost me this time... as it's taken me forever to resolve the same problem.

But the first thread had the solution in its entirety. I was even able to use the rt2860 drivers. I am going to upload the exact file I used to compile from source with the [instructions listed]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html") in the first post for anyone's else's use.

Things to note:
- This problem started up recently for me again; right after rebooting after downloading and installing some updates.
- I may be very wrong in this, but I'm thinking the cause of this problem are kernel upgrades.
- I HAD to recompile from source just as the instructions tell you to and move the rt2860.ko file to the new kernel folder (which for me was /lib/modules/2.6.32-23-generic/kernel/drivers/staging/rt2860).
- It was NOT fixed by changing versions of WICD (which I tried to do time and time again)
- It was NOT fixed by switching from WICD to network-manager.
- Unsecured networks connected just fine (I'm not sure about WEP secured networks), but WPA secured networks connected maybe 1 out of 10 times.
- Errors I received while trying to connect to my WPA2 network with various WICD versions included ```
[COLOR="Red"]**Connection Failed: Unable to get IP address**[/COLOR]
``` and ```
[COLOR="Red"]**Connection Failed: Bad Password**[/COLOR]
```
- I had to switch from a **wlan0** wireless interface to the **ra0** wireless interface. (This can be changed by opening up WICD, clicking on "Preferences" at the top, selecting the "General Settings" tab and entering the new wireless interface right beside "wireless interface:")

I'm going to mark this thread as solved. I hope my hours of ceaseless and tiring frustrations will at least benefit one other person.

---


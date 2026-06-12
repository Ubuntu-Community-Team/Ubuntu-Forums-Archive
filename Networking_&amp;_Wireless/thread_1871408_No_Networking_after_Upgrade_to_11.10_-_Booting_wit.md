---
title: "No Networking after Upgrade to 11.10 - Booting without full network configuration"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by jaguare22 on 2011-10-28
Hello all!  Since I ran the upgrade I have no wired or wireless network (not worried about wireless). At boot time my system, HP DV100, sits a couple of minutes saying, "Waiting for network configuration".  After a while it says, "Booting without full network configuration".  After boot network manager is all grayed out.  I can't access wired (or wireless) network connections in the network manager.  My interfaces file appears to be correct.  lo is right, and eth0 is set as it should be. 

I can't list lspci right now but my card is a realtech inc. If anyone could give me any ideas or a place to start I'd appreciate it.  Seems to be a problem with network manager, is it possible to download WICD from another machine and install?

Thanks

---

### Post by poolet on 2011-10-29
Hello, open up a new terminal and type:

```
lshw -C network 
```

and print the output here....

---

### Post by jaguare22 on 2011-10-29
> **poolet said:**
> Hello, open up a new terminal and type:

```
lshw -C network 
```

and print the output here....

Okay, I am switching back and forth on a dual boot.  Thanks for the help.

*-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth0
version: 10
serial: 00:c0:9f:d3:5e:89
size: 100Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.5 latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
resources: irq:16 ioport:3000(size=256) memory:b0106000-b01060ff
*-network:1 DISABLED
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 6
bus info: pci@0000:06:06.0
logical name: eth1
version: 05
serial: 00:15:00:1a:7b:a8
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.2.7 latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
resources: irq:18 memory:b0107000-b0107fff

---

### Post by poolet on 2011-10-29
Well it's seems that we find your problem!!!! RTL drivers may not be recognize with 11.10 version, so the best thing that you can do is to follow the following link... I have searching of the net for same problems but unfortunately I didn't find anything since 10.11 is a new release... So try to load it with **ndiswrapper **  to see what it will happened and if your problem isn't fixed we will try some tricks with broadcom..... Hope that helps you!!!!


[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by jaguare22 on 2011-10-29
Thanks very much.  I think I have had to use ndiswrapper on another system.  I will work through the tutorial.  Funny thing is it was working in Natty.

Did you happen to see anything that would help getting the wireless working?  I wasn't turned on at the time I ran lshw.  It would help to have connectivity while working through this.

Thanks again.

---

### Post by jaguare22 on 2011-10-29
Well this is turning out to be over my head.  Not to mention very difficult considering I have no internet connectivity at all when in the Ubuntu config.  Now that I think of it, the NIC connection broke when I upgraded to Natty as well.  I was able to get through it with the help of the forum but I think I am done with upgrades.  Is there something weird about my system hardware? Should something as basic as wired networking be lost after an upgrade?  I don't know.  Very frustrating though.

About the wireless...the Intel 2200 has native drivers right?  Could someone help me get that working? 

Thanks

---

### Post by poolet on 2011-10-30
Ok. To understand.. before you upgrade to 11.10 with Natty was working and now after ndiswrapper isn't work??... Ok lets take your problem from the beginning... It's semms like your loading mod that isn't correct... Please take your time and post the output of the following (note: make it separate for each one): 

```
 lspci 
lsusb
``` 

```
lspci -nn | grep 'wireless brand (if you know or try Realtek or Intel )
``` 

```
lsmod 
```

```
dmesg
```

```
lsb_release -d
```

```
uname -mr 
```

at the end try to make a network restart to see what is happening...

```
sudo /etc/init.d/networking restart
```

**NOTE:: **make the restart first and after post the rest of them!!!!

---


---
title: "MAC Address for Wireless and Eth Interfaces"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by masoud77 on 2012-11-15
Hi,

I would like to figure out the MAC Address of the Ethernet and the Wireless Interfaces on my laptop. I have used the below commands with the following outputs.

```

$ ifconfig -a | grep HWaddr
eth0      Link encap:Ethernet  HWaddr 38:59:f9:10:12:13

```

```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 38:59:f9:10:12:13  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3a59:f9ff:fe10:1213/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:7
          TX packets:139 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30782 (30.7 KB)  TX bytes:20338 (20.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2226 (2.2 KB)  TX bytes:2226 (2.2 KB)

```

```

$ sudo lshw -C network
[sudo] password for masoud: 
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 38:59:f9:10:12:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.3 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

```

I am currently connected using my wireless connection and I also have an ethernet port that I don't use. The above commands only provide me the MAC Address of the wireless connection. Is there a way to get the MAC Address of the ethernet connection without actually being connected through the ethernet LAN port?

Any pointers will be much appreciated.

Thanks in advance,
Masoud A R

---

### Post by carl4926 on 2012-11-15
```
/sbin/ifconfig
```

You should see both 
eth0 and wlan0

Your eth0 looks to be
eth0      Link encap:Ethernet  HWaddr **38:59:f9:10:12:13  **

---

### Post by varunendra on 2012-11-15
> **carl4926 said:**
> You should see both 
eth0 and wlan0
Actually he has no wlan0. It is his wireless interface listed as eth0 -
> **masoud77 said:**
> ```

$ sudo lshw -C network
[sudo] password for masoud: 
  *-network               
       description: **Wireless interface**
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       **logical name:** [COLOR=Red]**eth0**[/COLOR]
```It is not very uncommon, although I don't know why it happens whenever it happens.


@masoud77,
What is your objective ?
From what I can see, you won't get the mac address even if you try to connect the LAN port, because it doesn't have a driver associated yet -
> **masoud77 said:**
> ```
 *-**network [COLOR=Red]UNCLAIMED[/COLOR]**
       description: Ethernet controller
       product: **AR8162** Fast Ethernet

```So it won't connect unless a driver 'claims' it. And when it gets a driver, you won't need to connect, ifconfig will give you the mac address.

If you are interested in enabling it (by installing appropriate driver),follow this thread - [http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)

---

### Post by masoud77 on 2012-11-16
Thanks, Varun.

The reason to figure out the MAC Address is an embarrsing one. My earlier laptop was stolen and the police said had I know the MAC Address of the laptop, the cyber police could assist out. So when I purchased a new one, I thought I will jot down the MAC Address. :D

Anyways, shall try out by installing the driver once I reach home and update the thread.

Thanks,
Masoud A R.

---

### Post by varunendra on 2012-11-16
Hmm.. interesting reason :)
> **masoud77 said:**
> the police said had I know the MAC Address of the laptop, the cyber police could assist out.
I hate to say this, but as far as I know [COLOR=Red](and I may be wrong)[/COLOR], it is practically impossible to track a computer over internet using its mac address.

Computers sit behind a router or modem, and these devices 'Hide' the mac IDs of computers and other devices connected to them on LAN side. The Internet can only 'see' the mac ID of the last device which is directly connected to it - that is - the routers/firewalls of the ISPs and web-servers.

Even if the laptop 'directly' connects to its ISP via a cable connection [COLOR=DarkSlateGray]*(an ethernet cable directly coming from the ISP and plugged into the computer itself)*[/COLOR], the only chance to track its mac id is when you are also connected to not only the 'same' ISP, but also the 'same' exchange station, plus, the ISP is willing to cooperate.

Once the traffic is 'passed' through a single router, there is no hope, since the other ISP or the 'cyber-police' can only see the mac id of the last router connected to the internet, not that of devices behind it.

There are, however, a few very limited alternatives [COLOR=DarkSlateGray]*(which can be easily disabled/circumvented and/or *blocked* if the thief is smart enough)*[/COLOR] which offer different kind of tracking methods. Search for it and you will find both the options, and maybe also, how they can be circumvented.

For a starting point, this discussion maybe interesting for you - [http://compnetworking.about.com/b/2008/06/09/can-you-trace-the-mac-address-of-a-stolen-computer-discuss.htm](http://compnetworking.about.com/b/2008/06/09/can-you-trace-the-mac-address-of-a-stolen-computer-discuss.htm)

Sorry to diminish your hopes, but the only security you can trust is your own awareness and alertness. All other types of security promises are nothing but illusions.

---

### Post by masoud77 on 2013-09-30
Thanks a lot, Varun.

I was finally able to connect using my ethernet connection. I had to have an alx driver installed and am able to see my MAC address for the ethernet port now. Not sure if the police will be able to help me as you said :D. Anyways, part of my problem is solved. Please find the below post that helped me with a detailed step-by-step instructions.

[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)

Regards,
Masoud A R

---


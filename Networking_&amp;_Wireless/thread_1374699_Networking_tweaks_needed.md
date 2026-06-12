---
title: "Networking tweaks needed"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by kirbys on 2010-01-07
I have just installed Ubuntu for the first time, and I installed sucessfully World of Warcraft, but I'm noticing some networking issues where my whole network connection seems to pause for about 5-10 seconds at a time, which I finally realized when I played WoW. So i was curious where the settings are that I can change to possible eliminate that, or what others have done to increase their network throughput on their cards.

I'm running Unbuntu 9.10 64bit with the latest version of Wine from the Synaptic Package Manager. The router is a Linksys[COLOR=Black]WRT54G3G-ST [/COLOR]and my wireless network card I think is something made from MSI I don't see where to find out what drivers are installed on it I'm probably just looking in the wrong place or I'd give more information on the card.

---

### Post by H3LlIoN on 2010-01-07
running commands lspci -nn and lshw -C in terminal will output both current drivers, and current devices.  Copy/paste results here.  Also, you might poke around for a bit...there are a couple threads about wireless stuff timing out.  

Also...it's a little known fact that the world's greatest freak out was ACTUALLY over wireless card compatibility after a Ubuntu install...it had nothing to do with that kid's mom shutting down the interweb.  :-P Good luck.

---

### Post by kirbys on 2010-01-07
> **H3LlIoN said:**
> running commands lspci -nn and lshw -C in terminal will output both current drivers, and current devices.  Copy/paste results here.  Also, you might poke around for a bit...there are a couple threads about wireless stuff timing out.  

Also...it's a little known fact that the world's greatest freak out was ACTUALLY over wireless card compatibility after a Ubuntu install...it had nothing to do with that kid's mom shutting down the interweb.  :-P Good luck.
> 
00:0a.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)


and the lshw -C command did this:

> 
$ lshw -c
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)


---

### Post by H3LlIoN on 2010-01-07
applications/accessories/terminal


sry, don't know keystroke

---

### Post by kirbys on 2010-01-07
> **H3LlIoN said:**
> applications/accessories/terminal


sry, don't know keystroke
yeah sorry about that i was bein dumb lol looked at it atleast 4x before i realized what it was sorry about that.

---

### Post by kirbys on 2010-01-07
$ sudo lshw -C network
[sudo] password for login: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:4c:b3:37
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:1000(size=256) memory:d2215000-d22150ff memory:88000000-8801ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:0e:8e:08:3e:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.102 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:d2200000-d220ffff

---

### Post by H3LlIoN on 2010-01-07
well, your driver is ath5k, which looks to be correct, but you probably want to wait around for someone more experienced.  Internet is working, just lagging, yes?

---

### Post by kirbys on 2010-01-07
Yeah everything works i can get email download with little to no interruption etc, but when things need to be "live" I don't get disconnected it just hangs for 6-10 seconds.

---

### Post by H3LlIoN on 2010-01-07
which version of ubuntu are you running?

---

### Post by kirbys on 2010-01-07
9.10 64bit

---

### Post by H3LlIoN on 2010-01-07
eh i know nothing about 64 bit.  Better wait for someone else.  Sry and good luck

---

### Post by kirbys on 2010-01-07
Heres a tracert to the server I'm connecting to which is a typical report on my internet connection, and as everyone can see, its not that bad but when it lags the latency shoots up to around 9k

> 
Hop    Hostname    IP    Time 1    Time 2
1    kirbyscomp.local    192.168.0.102    0.240ms    
1    192.168.0.1    192.168.0.1    1.378ms    
1    192.168.0.1    192.168.0.1    1.458ms    
2    68.28.49.85    68.28.49.85    214.603ms    
3    68.28.49.91    68.28.49.91    319.000ms    
4    68.28.51.54    68.28.51.54    224.675ms    
5    68.28.55.1    68.28.55.1    211.512ms    
6    68.28.55.16    68.28.55.16    259.483ms    
7    68.28.53.69    68.28.53.69    234.947ms    
8    sl-gw10-bur-1-0-0.sprintlink.net    144.223.255.17    243.799ms    
9    sl-bb21-bur-10-0-0.sprintlink.net    144.232.0.70    156.238ms    
10    sl-crs1-ria-0-3-0-0.sprintlink.net    144.232.9.147    170.086ms    
11    sl-crs1-stk-0-2-3-0.sprintlink.net    144.232.9.153    178.591ms    
12    sl-crs2-sj-0-14-0-3.sprintlink.net    144.232.18.150    185.067ms    
13    sl-st21-sj-12-0-0.sprintlink.net    144.232.9.240    206.219ms    
14    144.232.18.26    144.232.18.26    392.149ms    
15    vlan99.csw4.SanJose1.Level3.net    4.68.18.254    237.050ms    
16    ae-92-92.ebr2.SanJose1.Level3.net    4.69.134.221    205.277ms    
17    ae-7.ebr1.seattle1.level3.net    4.69.132.50    208.247ms    
18    ae-11-51.car1.seattle1.level3.net    4.68.105.2    200.882ms    
19    mzima-netwo.car1.seattle1.level3.net    4.53.144.18    227.838ms    
20    72.37.232.218    72.37.232.218    250.830ms    


---

### Post by wojox on 2010-01-07
Try [Disable IPv6]("http://wojox.homelinux.net/?p=1")

---

### Post by kirbys on 2010-01-07
> **wojox said:**
> Try [Disable IPv6]("http://wojox.homelinux.net/?p=1")
Just disabled it

---

### Post by kirbys on 2010-01-07
bump

---

### Post by kirbys on 2010-01-07
bump

---


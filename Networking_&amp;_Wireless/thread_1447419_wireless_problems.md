---
title: "wireless problems"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by davexp on 2010-04-05
hi all i hope some one on here can help me out, i am new to linux mint and useing linux mint 7 at the moment but can't get my wireless to work ive also tried linux mint 5,6, and 8, ubuntu 9.04 and 9.10 with the same result when i try to connect using lan, it wont connect ether trys to then ether freezes or says i am now off line and wont connect. my wireless card is a intel pro wireless 2200BG my network manager says no devies available but my wireless light is on, ive tried various how to's off the net with no luck and also tried to load the windows driver inf file says hardware present yes but still wont work
 
thanks in advance

---

### Post by alexdelprogramador on 2010-04-05
> **davexp said:**
> hi all i hope some one on here can help me out, i am new to linux mint and useing linux mint 7 



hello!!

yea! its mint its a great operating system, it's a debian based distribution, really quick and complete.



> at the moment but can't get my wireless to work ive also tried linux mint 5,6, and 8, ubuntu 9.04 and 9.10 with the same result when i try to connect using lan, it wont connect ether trys to then ether freezes or says i am now off line and wont connect. my wireless card is a intel pro wireless 2200BG my network manager says no devies available but my wireless light is on, ive tried various how to's off the net with no luck and also tried to load the windows driver inf file says hardware present yes but still wont work
 
thanks in advanceok, so I have to check something.

enter with as a root user in the console:  

user: root
Password: "what you typed"

then type this:

```
lshw -C network
```copy and paste here... ;)

and then, type:

> iwconfigcopy and paste, and then:

> ifconfigwith that, we can see if you have up your wireless device, or if you have troubles with your wireless device.

bye

):P

---

### Post by alexdelprogramador on 2010-04-05
also, see that link, I think he had the same trouble:

[http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)

:popcorn:

---

### Post by davexp on 2010-04-05
hi thanks for the quick response here are the outputs from the commands
 
ishw -C network
 
*-network:0 
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:06:01.0
logical name: eth0
version: 10
serial: 00:16:d4:b0:a7:fc
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
*-network:1 UNCLAIMED
description: Network controller
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:06:02.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64 maxlatency=16 mingnt=3
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 42:fd:5d:1f:17:da
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 
 
ifconfig
eth0 Link encap:Ethernet HWaddr 00:16:d4:b0:a7:fc 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xa000 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:200 (200.0 B) TX bytes:200 (200.0 B)
 
iwconfig
 
lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions

---

### Post by alexdelprogramador on 2010-04-05
ok

Its true. In network1 you have

> 
*-network:1 UNCLAIMED
description: Network controller
product: PRO/Wireless 2200BG
so ¿did you read all the last post I sayed?

[http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)


but, in spite of the last post, I can see that you dont have recognized your wifi card when you type: iwconfig


The problem is that the module ipw2200  isn't probably loaded...

I could guess this module  because its supported under gnu/linux by this web page: [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

Um... to check it, you can type this code?

```

lsmod | grep ipw

```show me what happend ;)

---

### Post by davexp on 2010-04-05
hi there thanks for the reply the output of lsmod | grep ipw is as follows
 
ipw2200               150984  0 
ieee80211              38344  1 ipw2200
 
 
thanks

---


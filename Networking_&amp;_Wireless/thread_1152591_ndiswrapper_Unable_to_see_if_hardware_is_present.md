---
title: "ndiswrapper Unable to see if hardware is present"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by billyfd on 2009-05-07
I'm new to Ubuntu and currently using the 9.04 version. I'm having problems getting my wireless to work with ndiswrapper. I've blacklisted like other post say and got the .inf file.
I use the the windows wireless driver window. Every time i get the driver in the window to install I click install and it says "unable to see if hardware is present". When I click ok it says yes to hardware present. Can anyone help me? I dont know if there is a post already or not looking for help and direction

---

### Post by fleasbaby on 2009-05-18
Hi All,

I am having the same problem...After fiddling about trying to get my wireless to work I found out about NDISWrapper, gave it a go, and am having the same issues.

Any advice at all?

Bruce

---

### Post by rockfloyd on 2009-05-29
me too! jesus i hope this gets solved.

---

### Post by billyfd on 2009-06-01
Well i have been reading about another network manager, WICD, BUT have yet to try it, still running 8.10 with ndiswrapper. Hoping to solve it soon

---

### Post by iblis on 2009-06-02
I'm getting the same error message with Jaunty; while I can ignore it, and connect, once I reboot I need to uninstall and reinstall the driver.

I'll take a peek at ndisgtk once I get my notebook back in development order, since I know more than a tiny bit of python. :D

---

### Post by Jackp90 on 2009-06-05
I am assuming that most of you have recently upgraded like I have to ubuntu 9.04.  

In the past versions we had to use ndiswrapper because there wasn't a ubuntu driver for for our wireless cards, in my case a Broadcom STA wireless card, but odds are that there is now.  

To install it you can go system --> administration --> hardware drivers or type the following into a terminal or run application prompt:

```
jockey-gtk
``` 

From there, if you were as lucky as me, there is a wireless driver that shows up there.  To activate it you can select the drive from the list and then click on "activate" in the lower right hand corner above close.  

I have noticed that you may have to do an update for any of the drivers to show up.  It may take a few minutes to register any wireless networks, it did for me.  During that time I also restarted my computer and un-installed ndiswrapper.  Neither of these last two things should affect it in theory but if its not working for you after about five minutes I would give it a try.  Hope this helps you guys out.

---

### Post by billyfd on 2009-06-05
Well i thought that i had tried that before and it not work, but i did a fresh install and took your advice. I found that it worked! Thank you so much! After all that headache thats all I had to do

---

### Post by Mattaus on 2009-06-05
Argh!

I have used ndiswrapper to install the driver for my Netgear WPN311 card. When I run **ndiswrapper -l** it says the driver is installed and thats all.

When I run the windows wireless drivers utility, the driver is listed as installed but no hardware is present...despite it clearly been plugged in with the power L.E.D flashing it balls off.

There is no reference to the driver under *System -> Administration -> Hardware Drivers* either.

Any suggestions?

---

### Post by Jackp90 on 2009-06-06
> **Mattaus said:**
> 
There is no reference to the driver under *System -> Administration -> Hardware Drivers* either.

Any suggestions?

What release are you using . . . if the menu short cut does not work use the code that I gave you earlier . . . 

```
jockey-gtk
```

---

### Post by billyfd on 2009-06-06
if you still have not luck be sure you read the forum on the comprehensive guide to ndiswrapper. it is very detailed and cleared alot of my problems when i used 8.10

---

### Post by nowfocus on 2009-06-27
Hey all - I had a similar problem, found solution here:
[http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702)

---

### Post by Demented Maniac on 2009-07-01
Hi All, I'm having a similar problem.

After googling it to death, and following a bunch of threads, I have managed to get the lights blinking on the card. That's about it, not much more is working.

I'm running Jaunty on an old Dell Inspiron Laptop with a Netgear WG511 V2 card ( Made in Taiwan ) 

The only thing listed when I got to System>Administration>Hardware Drivers is "NVIDIA Accellerated Graphics driver" which I've Activated.

I've installed ndiswrapper, and loaded a driver from "ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip" which I downloaded from [http://www.4shared.com/file/73908328/b6c7bc3f/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.html](http://www.4shared.com/file/73908328/b6c7bc3f/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.html)

I've tried both the XP & W2K drivers in that package, both have the same effect, that is the lights come on on the card, but a message box comes up saying "Unable to see if hardware is present" each time I open System>Administration>Windows Wireless Drivers, although when I click OK on that message box, it says "Hardware present: yes" in the list.

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: eth0
       version: 08
       serial: 00:20:e0:6b:8e:05
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=10.1.1.11 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: 88W8300 802.11b Cardbus PC Card
       product: 83
       vendor: Marvell Semiconductor
       physical id: 0
       version: 01
       slot: Socket 1
       resources: irq:10
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 03
       serial: 00:0f:b5:0a:9b:d6
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8000c driverversion=1.53+Marvell,02/22/2005,3.1.1.7 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:20:7d:c5:2c:da
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I'm very new to Linux, and would greatly apreciate any help anyone is able to give me.

Thanks.

---

### Post by rwalker83 on 2009-07-14
I am been trying a failing to fix this for awhile please help.

  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:67:5b:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.10.192 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:78:d0:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.53+INPROCOMM,11/04/2004,3.03.1 latency=64 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:2d:98:2e:17:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Sorry ment for another thread

---


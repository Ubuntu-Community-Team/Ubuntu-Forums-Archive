---
title: "Cant enable wireless adapter"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by tropnevad on 2009-01-16
I Cant enable wireless adapter, on packard bell easynote

it is a friends computer who i am helping to setup ubuntu on, and i got everyhting working, just the wireless does not work.  It could be that the driver does not work, but i dont think this is the case.  The wifi is enables with a button on the pc, but this button does not work in ubuntu, and the wireless light is on untill i log in to ubuntu.  

So is there any way i can enable the wireless device in the terminal or anything?

Thanks in advance

---

### Post by hydo1 on 2009-05-06
what easynote device is it 
i am havin the same problem with mine

---

### Post by pastalavista on 2009-05-06
Have you tried connecting with an ethernet (wired) connection? 99 times out of 100 that will work. Then a simple update will usually find the driver you need for wireless.

---

### Post by kay-man on 2009-05-06
Please run the following commands from a terminal and post the output:

sudo ifconfig

sudo iwconfig

sudo lshw -class Network

So hopefully we'll get an idea of what's going on.

---

### Post by jbarden on 2009-05-06
I'm new on the forum and not sure this is where to ask this question.  I have Dell Inspiron 531 and I loaded U 9.04 and everything worked but the wireless card. I ran "sudo lshw C network" on the terminal and the wireless interface was indicated as "Disabled".  There is no hardware switch (to turn it back on) so I'm thinking this device is not supported by UBUNTU.  Can any help with this problem?  THANKS

The following is all the data I got when I ran "sudo lshw C network".

 *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:00:68:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:db:89:00:7a:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by kay-man on 2009-05-06
A quick search with google shows you don't have the easiest card to set up.

But it should be possible, here are some links you might find helpful:

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/#comment-37911]("http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/#comment-37911")

[http://ubuntuforums.org/showthread.php?t=525201]("http://ubuntuforums.org/showthread.php?t=525201")

Maybe you should check out the second link first.

Good luck!

---

### Post by MeatCleaver on 2010-08-13
I have an Atheros 5400 Wifi card but i want it to be set on by default on startup, is there any way i can do that

---


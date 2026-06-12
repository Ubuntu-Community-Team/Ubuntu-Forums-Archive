---
title: "Help...I can only -half- connect to my router!"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by mariane_08 on 2009-03-13
This all started yesterday when I had to change the WPA password for my WiFi Router. Before that everything worked fine. It also works fine right now if I use Windows. It's just in Ubuntu I'm having problems. 

What happens is this. I right click the wireless Icon up at the top and "enable wireless". I then left click and get the list of networks in range and select mine. Of course since its the first time it prompts for the password. (I deleted my old one by going to "edit wireless networks" and removing it).

I enter my password and the little circle thingy goes round and round and the bottom dot goes green but not the top. This goes on for a while and eventually prompts for the password again. And so on. 

Can someone tell me whats going on and how to resolve it? 

Thanks

Oh BTW I should point out if I take my laptop to a public unsecured WiFi location I can connect just fine. So its not a problem with my wireless as such. It seems to be something it accepting my password?

---

### Post by mariane_08 on 2009-03-13
Any ideas anyone? this is driving me nuts! I'm sure it must be something basic I dont understand.

Thanks

---

### Post by JerryI on 2009-03-13
Mariane:

Can't help you, but I have a similar problem.  Your remark that you can go to Starbucks or wherever and connect intrigues me.  Last night I installed a new HD and loaded dual-boot XP/Hardy on a laptop.  Like you, I cannot connect to my home network 2wire411 (from Hardy), but I can see it, select it, key in my wep key 0360663701 and watch the spinner for a few seconds until it asks for my wep key again.  This, in spite of the fact that the wep key works for computers in the house on Intrepid, XP (the dual-boot laptop with the problem), and Vista (the computer I'm typing on right now).  I haven't taken my laptop to Starbucks yet, so I don't know whether it works there, but it probably will.

Would you do me a favor, and report what you get when you query 
    sudo lshw -C network

This might be helpful to someone who might come to our rescue, but my experience is that once a thread gets a few hour old nobody pays attention to it.

Here's what I get (below);  the wireless network shows up in the last 6-7 lines.

Thanks:

Jerry Isaacs - Dallas TX

---------------------------------------------------

jerry@laptop:~$ sudo lshw -C network
[sudo] password for jerry:
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 10
serial: 00:c0:9f:86:5c:8e
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s


*-network
description: Wireless interface
physical id: 1
logical name: eth1
serial: 00:1e:37:f6:cc:c4
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
jerry@laptop:~$

---

### Post by linuxisevolution on 2009-03-13
This happened to me. I had to change my wireless security to 128 bits. Don't type your passphrase btw, use the keys.

---

### Post by JerryI on 2009-03-13
Mariane:

I have started a new thread that may draw some attention. You might want to check it out, in case it leads somewhere.

[http://ubuntuforums.org/showthread.php?p=6889667#post6889667](http://ubuntuforums.org/showthread.php?p=6889667#post6889667)

---

### Post by mariane_08 on 2009-03-13
> **JerryI said:**
> Mariane:

Can't help you, but I have a similar problem.  Your remark that you can go to Starbucks or wherever and connect intrigues me.  Last night I installed a new HD and loaded dual-boot XP/Hardy on a laptop.  Like you, I cannot connect to my home network 2wire411 (from Hardy), but I can see it, select it, key in my wep key 0360663701 and watch the spinner for a few seconds until it asks for my wep key again.  This, in spite of the fact that the wep key works for computers in the house on Intrepid, XP (the dual-boot laptop with the problem), and Vista (the computer I'm typing on right now).  I haven't taken my laptop to Starbucks yet, so I don't know whether it works there, but it probably will.

Would you do me a favor, and report what you get when you query 
    sudo lshw -C network



Jerry

I've just resolved it. Not quite sure why though. Near to me is a weak unsecured WiFi network. For some strange reason that was screwing up my access. Its not channel issue though because it worked before and does now again. I went to "edit wireless networks" and deleted the unsecured one. Then went and tried to connect to my router and entered the password prompt and in I went just fine. Now everythings fine again and I can use mine or for that matter the unsecured one of I really wanted too. I have no idea why this occured though?

dont know if this means anything now but here it is anyway:

mbdb@M2000:~$ sudo lshw -C network
[sudo] password for mbdb: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:f3:97:78
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:29:d2:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.4 multicast=yes wireless=IEEE 802.11g
mbdb@M2000:~$

---

### Post by JerryI on 2009-03-13
When you get to the box to type in your security entry, be sure to use the dropdown menu to select what you want to type in, e.g, password or wep key.  If you're trying to use a password and it is defaulting to WEP KEY that may be your whole problem.

---

### Post by JerryI on 2009-03-13
Just saw your post, so ignore my last.  Glad you resolved your problem.  You're way ahead of me now.

---


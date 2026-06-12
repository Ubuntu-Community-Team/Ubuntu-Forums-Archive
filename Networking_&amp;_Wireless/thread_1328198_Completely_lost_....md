---
title: "Completely lost ..."
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by judith_sw on 2009-11-16
Hi,
 
I am completely new to this, but the learning curve is steeper than expected!
 
I have an HP 2133 with SUSE and UNR (side-by-side). The installation of UNR seemed to go OK.
 
However, I cannot connect to the internet. I managed to by ethernet cable last night, but I tried plugging in the ethernet cable at work and nothing happened - no internet at all. I think I need to update the Broadcom drivers, but cannot, as the netbook needs access to the internet.
 
I also have a 3 dongle (Huawei E156G) but this is not recognised either.
 
I do not have a clue what to do - I've been googling furiously, but have gone past the point of rationalism :confused:
 
Any help genuinely appreciated.

---

### Post by dmizer on 2009-11-16
Please post the output of:
```
lshw -C network
```

It seems strange that you cannot get access at work via wired ethernet. Have you looked at the network settings in your Windows computer at work, or talked to your network admin? There may be special settings you need for your work connection.

---

### Post by judith_sw on 2009-11-16
Hi,
Just to show you how basic my knowledge is, please could you tell me where and how to enter the code? I presume I need to reboot and then enter the code. 
(I learn quickly)
Judith

---

### Post by puppywhacker on 2009-11-16
for typing commands use the terminal at
[applications] [accesories] [terminal]


For the 3G card I recommend a program called VMC "vodafone mobile connect" it should also work for other providers, and it is way more "point and click" than the other options.

For your wired connection we will have to do a bit of systematic troubleshooting. I think the broadcom 57xx modules (drivers) should be already included in linux. I think the driver should be called "bcm5700" if it is loaded already, this command should show 1. the module name 2. the size, 3. optionally the modules that depend on it.
```
lsmod | grep bcm
```

So if you plugged in the cable usually you would see lights burn at the plug to indicate the physical cable is recognized. blinking means there is traffic.

with "sudo mii-tool" you can see if the link is established

with "ifconfig" you can see which interfaces are up. Note that there should be a line "inet addr" to indicate you have an ip-address and the counters for Tx and Rx should not be zero.

"route -n" should have a line starting with 0.0.0.0 to indicate the default gateway to the internet

"nslookup www.google.com" should return name and address pairs.

---

### Post by dmizer on 2009-11-16
> **judith_sw said:**
> Just to show you how basic my knowledge is, please could you tell me where and how to enter the code? I presume I need to reboot and then enter the code. 
(I learn quickly)
Judith
No need to apologize for not knowing. I'm happy to explain.

You do not need to reboot to enter that command. Just click on: applications > Accessories > Terminal. Enter the code, and post the results here.

---

### Post by judith_sw on 2009-11-16
Thank you! This is the sort of stuff I need to know. I will have to enter the results manually, as the netbook is not connected - I am working on my office pc. There are a couple of sets of results. The first 2 lines of each are:
 
*-network UNCLAIMED
description: Network controller
product: BCM4312 802.11b/g
 
*-network
description: Ethernet interface
product: NetXtreme BCM5788 Gigabit Ethernet
 
I can type more details if necessary. I can also try the ethernet cable (on this computer) for the netbook again if needed.

---

### Post by dmizer on 2009-11-16
Unfortunately, I'll need the complete output. You can save the output to a text file, copy it to a USB drive, and move it over to the computer with access that way. :)

If you can get internet access at all, you'll probably be able to fix the whole thing via the restricted drivers interface.

---

### Post by judith_sw on 2009-11-16
Here goes:
 
*-network UNCLAIMED
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: [EMAIL="pci@0000:02:00:0"]pci@0000:02:00:0[/EMAIL]
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
resources: memory: fdffc000-fdffffff


*-network
description: Ethernet interface
product: NetXtreme BCM5788 Gigabit Ethernet
physical id: 3
bus info: [EMAIL="pci@0000:07:03:0"]pci@0000:07:03:0[/EMAIL]
logical name: eth0
version: 03
serial: 00:1f:29:9a:03:7d
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5788-v3.27 latency=64 mingnt=64 multicast=yes
resources: irq:16 memory: feaf0000-feafffff
 
Hope this helps!

---

### Post by puppywhacker on 2009-11-16
Ok, so your driver is the tg3

Can you run the following 4 commands for me?

sudo mii-tool eth0
ifconfig eth0
route -n
nslookup [www.google.com](www.google.com)

---

### Post by judith_sw on 2009-11-16
I typed them all in - with return between each one. The final response was:
 
;; connection timed out; no servers could be reached

---

### Post by puppywhacker on 2009-11-16
the other three commands should have returned something. The final part means that your DNS server can not be reached. That can be a consequence of one failure at one of the earlier three steps, or just that name resolving to go wrong.

for me the printout would look like this. In red the most interesting parts

**lsmod | grep 81**
[COLOR="Red"]**8139too**[/COLOR]                27360  0 
r8169                  38884  0 
8139cp                 23200  0 
mii                     6368  3 8139too,r8169,8139cp

**sudo mii-tool eth1**
eth1: negotiated 100baseTx-FD, [COLOR="Red"]**link ok**[/COLOR]

**ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:1d:92:b5:7a:d1  
          inet addr:[COLOR="Red"]**192.168.2.9**[/COLOR]  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fec0::1:9/64 Scope:Site
          inet6 addr: fe80::210:a7ff:fe10:8c43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:[COLOR="Red"]**433012**[/COLOR] errors:0 dropped:0 overruns:0 frame:0
          TX packets:[COLOR="Red"]**387627**[/COLOR] errors:0 dropped:0 overruns:6 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:427163836 (427.1 MB)  TX bytes:166795471 (166.7 MB)
          Interrupt:21 Base address:0xe800

**route -n**
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
[COLOR="Red"]**0.0.0.0         192.168.2.1**[/COLOR]     0.0.0.0         UG    100    0        0 eth0

**nslookup [www.google.com](www.google.com)**
Name:	[www.l.google.com](www.l.google.com)
Address: [COLOR="Red"]**74.125.79.103**[/COLOR]

---

### Post by judith_sw on 2009-11-16
Thanks! I'm home now and connected the ethernet - I have managed to coonect to the internet via this cable and have enabled the 2 drivers for the wireless internet. However, although wireless is now shown as enabled, I still cannot connect.

The commands you suggested show the following results:

judith@judith-laptop:~$ lsmod | grep 81
judith@judith-laptop:~$ sudo mii-tool eth0
eth0: no link
judith@judith-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9a:03:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

judith@judith-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
judith@judith-laptop:~$ nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

---

### Post by puppywhacker on 2009-11-16
Ok, time for a recap.

You have an HP 2133, which has a wired BCM5788 as eth0 using tg3 as driver, a wireless BCM4312 as eth1? and using b43? as driver. And you have a 3G usb-dongle that you don't use.

With a little bit of luck, networks will start working by itself, but since we are not having much luck we need to do some old school troubleshooting

At home you manged at one point to use the wired interface to connect to the internet, but at work that didn't work. At home you can't get the wireless to connect.

The commands that I gave are in order of network layers, so if the first one fails all others will as well. So when it says that eth0 has no link, that is most likely because you are trying now to use eth1 over wireless. Because you don't have a working link, your PC can't ask on a higher layer for an IP-address, and since you don't have a route to the internet you can't lookup where "www.google.com" is located.

To solve this we have to fix this in the same order, first get the link up and established and we can use mii-tool without anything to establish the link is up.
```
sudo mii-tool
```

For wireless, the command would be iwconfig

```
iwconfig
```

if that works we can later continue with ifconfig and dhcpclient.

---

### Post by judith_sw on 2009-11-16
You seem to have had some ESP link to my computer ... I woke it up and suddenly all the wireless networks were there! You are absolutely right, the wireless networks have somehow or other got themselves going.

Thank you for all your help - I am sending this message from my HP 2133 ... wirelessly.

I'm still finding UNR very slow (internet is fine), but that's another post for another day! I've learnt a fair bit this afternoon, so than you again!

BTW, does your alias refer to puppy linux?

---

### Post by puppywhacker on 2009-11-17
It's always nice to read "it's working now" messages, sometimes you need to wiggle the bytes a bit. My server is named puppy (like in small dog). It's a cute small little mac mini, and I beat it once in a while quiet severely. That is how I learn =)  Nothing to do with puppylinux, although impressive, and nothing to do with animal cruelty.

---

### Post by judith_sw on 2009-11-17
Just to let you know, not only did your advice work, I then installed Ubuntu (rather than the UNR version that was running very slowly), as I was told it might run faster. It runs far better than UNR, but still needed a few tweaks to get up and running, however, your advice paid off for this too, and all is well.

Now onto the dongle ...

---

### Post by xenosaga456 on 2009-11-17
well are u running ubuntu 9.10 if not then u probily should download the iso on another computer and burn it to disk and try reinstalling ubuntu or do a disk distribution upgrade and that might or should fix the problem

---


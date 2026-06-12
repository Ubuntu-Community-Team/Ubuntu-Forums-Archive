---
title: "omg help lol"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by poporo on 2006-06-29
okay so i'm a noob at kubuntu rofl, and i have a connection/networking problem

i ran ifconfig and i get...

[I]eth0 Link encap:Etherenet HWaddr 00:08:A1:00:2D:2D
       inet6 addr: fe80:208:a1ff:fe00:3d3d/64 scope:Link
       UP BROADCAST MULTICAST MTU:1492 Metric: 1
       RX packets: 129 errors:1283 dropped:0 overruns:0 frame:0
       TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes 12066 (11.7 KiB) TX byts:2665 (2.6 KiB)
       Interrupt:9 Base address:0xd400

lo Link encap:Local Loopback
   blah blah blah 127.0.0.1 Mask: 255.0.0.0[/I]

^First off... i was getting an IPv4 address of 192.168.2.9 (dhcp) which was a valid address on my network until... i ifconfig'd and it was like lol ipv6 so now i'mlike :confused: 

Um.... my PCI ethernet device is like CNETPRO200 Fast Etherent blah blah blah. worked fine before so i know it's not the device.... can anyone help?

---

### Post by H.E. Pennypacker on 2006-06-29
I've never come across a person who could laugh about his/her problems as well as you do.  Quite incredible.  I'll join you by saying "lol."

Please begin by telling us a few things about your setup and computer.  Provide us with necessary information...more than you think so that we can cover all grounds.

---

### Post by poporo on 2006-06-29
btw my etc/network/intefaces looks like:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 dhcp

auto ath0
iface ath0 dhcp

auto wlan0
iface wlan0 dhcp

---

### Post by poporo on 2006-06-29
and i'm on a quite old machine amd k-7 700mhz i believe

the PCI entry for my ethernet card in KInfoCenter says...

0000:00:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip Compatible 10/100 Etherent (rev31)
Subsystem: Unkown Device 4554:434e
Flags: bus master, medium devsel, latency 64, IRQ 9
I/O ports at d400 [size=256]
Memory at efffef00 (32-bit, non-prefetchable) [size=256]
Expansion ROM at eff800000 [disabled] [size=256]
Capabilities: <available only to root>




what else do you need... i'm clueless lawl'
and also... when i ran kubuntu live cd the network was fine... so maybe a driver error???? lol



and..... lspci -tv gives....

00.0 Advanced Micro Devices AMD System Controller
01.0 nVidia Corporation NV11
07.0 Advanced Micro Devices ISA
07.1-4 Advanced Micro Devices blah blah blah
0a.0 Davicom Semiconductor, Inc. 21x4x DEC-Tuilp compatible 10/100 Etherenet
0b.0 Creative labs sb live! 
^kind of cut some parts out i r the typing noob ><

---

### Post by H.E. Pennypacker on 2006-06-29
Please provide us with basic information before you move on to something else.  Start by telling us what kind of a connection you have.  Are we dealing with a wired or wireless connection?  If it is wired, do you have dial-up or broadband?  If it is wireless, what is the name of your wireless card?  

You need to start out with basic information first.  Once you've understood what type of connection you have, and your hardware information, begin by using the search feature, because it can be very useful.  If not the search feature, try google.com/linux.

If you still can't find anything, follow up, and tell us where you're going wrong.    Make a note to follow any Wiki instructions that you should be following.  Let us know what step becomes difficult or impossible.

This is all really basic information.

---

### Post by christhemonkey on 2006-06-29
After a quick google round,  your ethernet card seems to be affected by a bug that makes it use the wrong driver.

I got the solution from [this]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48287") page.

> To remedy bug, it suggests to:
- rmmod tulip
- rmmod dmfe
- modprobe dmfe

I did just that, followed by:

- /etc/init.d/networking stop
- /etc/init.d/networking start


The lines starting with - are commands that need to be typed into a terminal.
All of them should be prefixed with "sudo" (without ""s)


Hope that helps.

---


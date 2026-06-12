---
title: "Ethernet Connection Seen but Not Connecting"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by GrayArcadian on 2008-12-08
I'm green to Ubuntu but love it so far.  Here's my problem: About 4 days ago I downloaded the automatic updates and then rebooted and now my computer is showing a connection to the internet through my ethernet card but it will not ping anything.

Physical stuff:  I'm on a cable modem that connects to a router.  That router has an ethernet cable running from it to me.  The other computers on this router are working.  The ethernet cable when plugged in gives a strong, steady orange light and the ethernet connection works when we unplug it from my system and replug it in elsewhere, so I doubt it's a physical problem.  I've done the booting/rebooting/plug out/wait/plug in thing already.

Connection:  Autoeth0 is automatically connected.  When I run **ifconfig** it shows:

eth0   Link encap:Ethernet  HWaddr  00:14:2a:54:82:5d
       inet address: 192.168.1.2  Bcast: 192.168.1.255 Mask: 255.255.255.0
       inet6 addr: fe80::214:2aff:fe54:825d/64 Scope: Link
       UP BROADCAST RUNNING MULTICAST  MIU: 1500 METRIC: 1
       RX packets: 605 errors:0 dropped: 0 overruns:0 frame:0
       TX packets: 8 errors:0 dropped: 0 overruns: 0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes: 79193 (79.1 KB)  TX bytes: 1152 (1.1 KB)
       Interrupt: 16 Base address: 0xe000

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0
       inet6 addr:  ::1/128  Scope:Host
       UP LOOPBACK RUNNING  MIU: 16436  METRIC: 1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX: packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:0 (0.0 B)  TX: bytes:0 (0.0 B)

When I run **netstat** there's a long list, but everything shows as "connected."

I tried pinging ubuntu.com and the other computers on this network and I get a 0% received notice which on the help says there's a problem with my network connection related to a DSN, but I haven't been able to get much past this point.  In desperation I tried plugging in a wireless card and - same thing.  It detects the network, connects, and then can't ping or load anything on the browser.  Stats look similar when I run the terminal commands.  I have already tried deleting and reloading the network profiles and going through most of the System-->Administration--->network tools and the commands on the networking icon up by the clock.  I hardware tested and it used to be giving a "gateway" error, but I managed to get the system to find the gateway again so now it's not detecting any issues.

Thanks in advance

---

### Post by jmoorse on 2008-12-08
Please issue a ping by IP address to your gateway to test connectivity

Also:
if you are using DHCP please issue a `sudo dhclient eth0`
if you are using a static IP please check it is not already in use

---

### Post by GrayArcadian on 2008-12-08
*Please issue a ping by IP address to your gateway to test connectivity...if you are using a static IP please check it is not already in use*

Sorry Mr Moorse, not sure exactly what you mean but here's what I've done with the information:

Went into Network Tools, clicked the ping tab, entered the ISP 91.189.94.249 (ubuntu.com according to the help) and got a 0% successful packet again.  Also I made sure the ISP isn't the same as my roommates - it's not.

I ran **netstat -nr** to find my gateway and it shows the following:

Kernal IP routing table
Destination   Gateway   Genmask     Flags  MSS Window irtt Iface
192.168.1.0  0.0.0.0   255.255.255.0  U     0   0      0   eth0
0.0.0.0      192.168.1.1  0.0.0.0     UG    0   0      0   eth0

[I]Also:
if you are using DHCP please issue a `sudo dhclient eth0`[/I]

Ran **sudo dchlient eth0** in terminal and got the following:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:2a:54:82:5d
Sending on   LPF/eth0/00:14:2a:54:82:5d
Sedning on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 -- renewal in 34955 seconds.

I looked on the "for info website" and, while fascinating, it looks more like a place to get DHCP - which it seems like my system is detecting based on the above information (I could be very wrong.)

---

### Post by jmoorse on 2008-12-08
Please issue the following commands and post output:

ping 192.168.1.1

tracepath 4.2.2.2

Thanks

---

### Post by GrayArcadian on 2008-12-08
> **jmoorse said:**
> Please issue the following commands and post output:

ping 192.168.1.1

tracepath 4.2.2.2

Thanks

**Ping 192.168.1.1**

I get the following many multiple times:

ping: sendmeg: Operation not permitted

I finally had to cntl-c to stop it.  Ping statistic read 142 packets transmitted, 0 received, 100% packet loss, time 141107ms

**tracepath 4.2.2.2**

1: send failed
   Resume: pmtu 65535

---

### Post by jmoorse on 2008-12-08
Please issue the command:

sudo ifconfig eth0 mtu 1300

and retry the ping command

If it still does not work please issue command:

sudo ifconfig eth0 mtu 1492

and respond

---

### Post by GrayArcadian on 2008-12-08
Tried both commands and then **ping 192.168.1.1** both did the same thing:

ping sendmeg: Operation not permitted

Also, so I'm less of a newbie, what was it we've been trying to do on the system with the commands we've tried.  "ping" and "sudo" I understand.  "ifconfig" seems to be "go see how the system is seeing the internet connection." Other then that I have no frame of reference for what's being tried.

Thank you for your help and patience.

---

### Post by jmoorse on 2008-12-08
No problem.

Do you have another network card you can swap in to test?

---

### Post by GrayArcadian on 2008-12-08
Nope.  The other roommates are on laptops with internal cards.  I have the desktop downstairs.

So this could still be a physical issue?

---

### Post by jmoorse on 2008-12-08
Could be.  May also be a driver issue.  Have you tried swapping the ethernet cable?

---

### Post by GrayArcadian on 2008-12-08
Was starting to suspect the drivers, actually.

The ethernet cable works if we plug it into one of the laptops as a way to send and receive data over the internet.  Plus, the cord is new and in what looks to be excellent physical shape.

Problem with drivers is that I know very little about them other then "download this and it magically works or doesn't work because now the system understands the hardware."  I have the drivers for this card I'm pretty sure.  I'm not sure if the CD would work with linux.

---

### Post by jmoorse on 2008-12-08
The CD will not work directly, so to speak.

Can you issue the following commands and paste the output:

lspci | grep Ethernet
dmesg | grep -i eth0

Thanks

---

### Post by GrayArcadian on 2008-12-08
**lspci | grep Ethernet** gave me:

00.0 Ethernet controller: Realtek Semiconductor Co., Limited RTL-8139/8139C/8139C+ (rev 10)

**dmesg | grep -i eth0** gave me a HUGE output of stuff I had to make into an attachment here.

I should note:  I'm using a laptop that has XP on it now to access the forum.  The desktop only has Ubuntu.  There is no dual operating system thing going on.

---

### Post by jmoorse on 2008-12-08
Sorry to have to point you in another direction, but it looks like there might be some driver issues with 8.10:

[http://ubuntuforums.org/showthread.php?t=963978&highlight=8139](http://ubuntuforums.org/showthread.php?t=963978&highlight=8139)

---


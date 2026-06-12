---
title: "Cannot get DHCP to work with Ubuntu"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by zedster on 2006-07-16
Hello, 
I never posted a linux problem before, always was able to find the solution by searching. But all attempts have failed.

When I setup the box either dhcp or static, I cannot ping the router or anything else. It was working on breezy badger using static, but I didn't write down how I got it working, so when I wiped it and installed Dapper, it isn't working.
I disabled ipv6 by adding:
blacklist ipv6
to: 
/etc/modprobe.d/blacklist

No effect. I would like to get this working using DHCP, if possible.

Details:
output of cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Output of lspci | grep -i ethernet
```
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
```
Output of dmesg | grep eth
```
[4294681.004000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[4294681.518000] eth0: forcedeth.c: subsystem: 01565:2501 bound to 0000:00:14.0
```

Output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:F1:96:16
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1080 (1.0 KiB)  TX bytes:0 (0.0 b)
          Interrupt:225

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)

```

If I try to ping my router (or anything):
```
$ ping 172.16.0.1
connect: Network is unreachable
```

DHCP is up and running fine on 3 other PC's. My router settings are:
address: 172.16.0.1
Subnet Mask: 255.255.0.0
DHCP range: 172.16.1.33 - 172.16.1.250
This is also the default settings on this 2wire gateway.

I'm stumped. Any ideas? (static setup fails the same way, if you want ifconfig output, I can provide).

---

### Post by kiddo on 2006-07-17
Just a thought, might not work at all, try:

sudo ifdown eth0 && sudo ifup eth0 && sudo dhclient eth0

I hope it can do something :|

---

### Post by zedster on 2006-07-19
> **kiddo said:**
> Just a thought, might not work at all, try:

sudo ifdown eth0 && sudo ifup eth0 && sudo dhclient eth0

I hope it can do something :|

Well, I tried that. No beans...
Here is the output:
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:4c:f1:96:16
Sending on   LPF/eth0/00:e0:4c:f1:96:16
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:4c:f1:96:16
Sending on   LPF/eth0/00:e0:4c:f1:96:16
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:4c:f1:96:16
Sending on   LPF/eth0/00:e0:4c:f1:96:16
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any other ideas? If not, I think I will have to give up on dhcp, and see if I can get it working with static first.

---

### Post by zedster on 2006-07-20
Well, I can't get static ip assignment working either. Same problem. All ping attempts to the router produce the "Network Unreachable" error.

I'm really at a loss here. I don't understand what it could be. 

Would someone please post an idea here?

---

### Post by MerZo on 2006-07-20
I am sitting here with the same problem. It isnt working, has worked before, and I tried about everything it seems like.

---

### Post by Routhinator on 2006-07-20
I also have the same issue, with Kubuntu, and Ubuntu of this version. It seems like IPv4 support is non-existent, my router does not even record an attempt at pulling an IPv4 address. Manually configuring with static does nothing either. No communication to the router, let alone internet. Windows works fine and older versions of Ubuntu work fine. Has no one got a fix for this yet? How do we enable IPv4? And why would it not be enabled by default? ISP's have not even gone to IPv6 yet, let alone home users.

---

### Post by TheRobohobo on 2006-07-20
This seems to be the problem I have as well.

---

### Post by zedster on 2006-07-20
Since it was not working when I statically assigned an IP address, I am beginning to suspect a bug in the ethernet driver or in the kernel.

This was working in 6.04. I will attempt to wipe the drive and try again with 6.04, and compare driver versions.

MerZo, Routhy and robo, can you post what ethernet driver you are using? 

This information is easily read by typing:
lspci | grep -i ethernet
and
dmesg | grep eth
into the command line and posting the output.

If anyone thinks it may be configuration, not drivers, please post an alternative theory. I am grasping at straws.

---

### Post by kaktos on 2006-07-20
I got the same problem and my ethernet card is RealTek 8129.I had researched for 1 week and no answers to me.](*,)

---

### Post by MerZo on 2006-07-21
Let us do our best to not let this thread die. Because I really want to solve this problem. Right now I am at work, and because the networkd doesnt work I am not running Ubuntu at home right now.

But I will do the commands with my LiveCD so I can post the results (the same as the installtion, none of them working). 

The really wierd thing for me is that I can remember my wireless working on the same livecd before, and the wireless still working in windows, even tried different routers so that can be excluded. 

Even static doesnt give me internet access. I also have the feeling of a bug, but how can it have worked before? :/ real annoying not being able to use ubuntu because of this.

---

### Post by gigaferz on 2006-07-21
Im new at this..but looks like ubuntu does not work on Ethernet at all....who can develop a patch..or something like that?? Its really very sad to go trhough this..

---

### Post by MerZo on 2006-07-21
Connecting a cable to my laptop, works fabulous. Connection the wireless gives me a headache. 

Someone with knowledge on which log files to look at?

---

### Post by zedster on 2006-07-21
> **MerZo said:**
> Connecting a cable to my laptop, works fabulous. Connection the wireless gives me a headache. 

Someone with knowledge on which log files to look at?

Wow, so you are almost there!

When you have your wireless hw connected, what does ipconfig tell you about that interface? There are some other posts in here on wireless configs that may help you out with this. I had breezy working on my laptop with an orinoco wifi card. I had to specify everything statically in my /etc/network/interfaces file.

I assume DHCP is your problem.

---

### Post by MindFul on 2006-07-21
I think my problem is similar,

I booted to the Live CD and my internet works nice, but when I install ubuntu and booted it, I lost internet.

I have a CNet Pro 200 Ethernet Card too, and a Samsung Info Ranger Cablemodem SCM-120U.

I have XP and Ubuntu installed on the same machine, bu XP's is connecting ok to the net.

My network configurations looks the same in live CD ubuntu and hd intalled ubutu.

---

### Post by happymeteor on 2006-07-21
I also have same problem.
When installing ubuntu server, DHCP checking was "Success".
However, after that and rebooting, I can't use the Internet.
My lan card is on-board intel chipset.
I hope this thread will not die.

---

### Post by notoriousbigdan on 2006-07-21
Same deal here. Just installed Ubuntu and no ethernet. It's a dual boot machine and I never had a problem with it before.

---

### Post by NutherNut on 2006-07-22
Your problems sound much like mine and I joined this forum for the sole purpose of passing this along. I dual boot XP and Linux (though not Ubuntu) on a PC with built-in nVidia MCP51 Network Controller connected to a router with DHCP. Here's what I discovered.

After booting XP, Linux will not connect unless I power off by pressing and holing the switch for 20 seconds or so. It seems the network controller is holding a state from XP that the Linux driver does not clear. I have found a post or two elsewhere stating there is a new forcedeth driver.

---

### Post by MerZo on 2006-07-22
> **NutherNut said:**
> Your problems sound much like mine and I joined this forum for the sole purpose of passing this along. I dual boot XP and Linux (though not Ubuntu) on a PC with built-in nVidia MCP51 Network Controller connected to a router with DHCP. Here's what I discovered.

After booting XP, Linux will not connect unless I power off by pressing and holing the switch for 20 seconds or so. It seems the network controller is holding a state from XP that the Linux driver does not clear. I have found a post or two elsewhere stating there is a new forcedeth driver.

I have a feel that my problem comes in the way of something like this. Because the feeling I get is that everything is working but not loosing its grip of the wireless. Tried to reset the BIOS of the laptop but it didn't change anything. 

The ipconfig command gives me a connection without a IP-address. The iwconfig gives me a connection with signal and the router. Same with the scan.

One thing I was wondering about is that I got 2 devices, eth0 and wifi0 that is the same?

eth1 is the cable.

---

### Post by NvJuggalo on 2006-07-22
Well You can add me to this seemingly growing list.

I was running Ubuntu Fine, trying to Download a File, and getting one hell of a slow download, 6.5k when I should be getting 100+ and It stalled(the Download),
I try starting it again, same thing. I move my comp. a little to get a better signal to the router, I come back and try again. File starts downloading @300K WHOO HOO, I think I fixed it. 
but again the file stalls @4.7k/s. then I try again "cannot connect to server" and since then thats all I get...Windows works fine... WTH is going on?

---

### Post by steeltzar on 2006-07-22
Hi guys, looks like I need the same help. Just installed Ubuntu 6.06 on a clean machine, not running windows at all. Ubuntu loads fine, I can ping my wired router the networking connection detailsseem fine but it just won't connect to the internet. I run Firefix which comes with Ubuntu but no deal. Any ideas?

---

### Post by mips on 2006-07-22
> **MindFul said:**
> I think my problem is similar,
...
I have a CNet Pro 200 Ethernet Card too, and a Samsung Info Ranger Cablemodem SCM-120U.


Your problem is related to the Tulip chipset. Just do a search for 'tulip' here and you will find many posts, someone actually wrote a howto.

---

### Post by mips on 2006-07-22
If you assign static IP parameters ensure they are correct. If you cannot ping your router then the problem could be with the module for your LAN card.

There are known issues with a few chipsets, Nvidia, Realtek, Tulip and I dunno what else.

First test is to check your hardware is OK, cable, lan card, router. If it works from a livecd or another OS then all is good.

Next do a static config and try to ping your gateway, if this works then you have to sort out dhcp.

If the above fails start checking which modules are loaded for the LAN.

lspci -v  will give you a nice verbose output.

It always helps to post as much info as possible on your problem with outputs from several commands and config files.

---

### Post by MindFul on 2006-07-22
I solved the problem using using the h3h_timo post:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

long live to timo.

---

### Post by MindFul on 2006-07-22
> **mips said:**
> Your problem is related to the Tulip chipset. Just do a search for 'tulip' here and you will find many posts, someone actually wrote a howto.

thank you mips. 

you light me in the right direction.

I solved the problem using using the h3h_timo post:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

long live to timo.

---

### Post by zedster on 2007-01-05
Congrats to those who got it working.

For those still having problems:
I just waited and installed 6.10. It works fine for me out-of-the-box. I didn't have to change anything. If you want to have a look at my files, let me know what.

Good luck.

---


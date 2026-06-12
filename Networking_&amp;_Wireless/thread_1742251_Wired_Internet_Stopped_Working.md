---
title: "Wired Internet Stopped Working"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by humbug01 on 2011-04-28
I had shut down my laptop at work last week and when I booted it up the wired internet connect was not working.

The wireless connection is working (I'm typing now via wireless).

I have WinXP Pro on this machine (but I've never used it--I'm all Linux now). So I booted into WinXP and turned off the wireless and got internet connection through the ethernet cable, so it doesn't seem to be the cable or my ethernet card.

Here is the output of "ifconfig"

```
eth0      Link encap:Ethernet  HWaddr 00:1c:25:7a:fa:b6  
          inet addr:xxx.xxx.xxx.xx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe7a:fab6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:135122 (135.1 KB)  TX bytes:10630 (10.6 KB)
          Memory:fe000000-fe020000 
```

I'm running Lucid 10.04 on a Lenovo T61 Thinkpad.

I'd very much appreciate help! I know my way generally around a computer but know very little about networking....

Thanks in advance.

---

### Post by humbug01 on 2011-04-29
Two more bits of information.

lspci -nn give this:
> 00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)

When I left click on the Network Manager applet in Gnome panel it says: "Wired Network" "device not managed".

Thanks again for help.

---

### Post by diamondnular on 2011-04-29
Weird! I have mostly same problem: wireless working, wired works locally only (meaning it can connect to other website on other computer on network). Switch to a working static IP did not help. I would very appreciate anybody can help out of this!!!

More information:
```
$ sudo service networking status
networking stop/waiting
$ sudo service networking restart
restart: Unknown instance:
$ sudo service networking start
networking stop/waiting
```

---

### Post by humbug01 on 2011-04-29
Well, I'm not sure how all this works but the wired connection is now working after following advice in thread below and other places on web.

[http://ubuntuforums.org/showthread.php?t=1711586&highlight=device+not+managed&page=2]("http://ubuntuforums.org/showthread.php?t=1711586&highlight=device+not+managed&page=2")

What I did was comment out "auto eth0" and "iface eth0 inet dhcp" lines in /etc/network/interfaces file which reads:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Interestingly, the same file on my netbook with exact same installation of Lucid does not have those last two lines.

And before all this came up, Network Manager did not have an icon in my panel showing the wired network (it just worked), but now it does.

But it seems to work for reasons I'm not quite clear on.

---

### Post by diamondnular on 2011-04-29
> **humbug01 said:**
> Well, I'm not sure how all this works but the wired connection is now working after following advice in thread below and other places on web.

[http://ubuntuforums.org/showthread.php?t=1711586&highlight=device+not+managed&page=2]("http://ubuntuforums.org/showthread.php?t=1711586&highlight=device+not+managed&page=2")

What I did was comment out "auto eth0" and "iface eth0 inet dhcp" lines in /etc/network/interfaces file which reads:



Interestingly, the same file on my netbook with exact same installation of Lucid does not have those last two lines.

And before all this came up, Network Manager did not have an icon in my panel showing the wired network (it just worked), but now it does.

But it seems to work for reasons I'm not quite clear on.
Thanks for your suggestion humbug01, but unfortunately that will not work for my case since I dont have those extra lines:
```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


```

---


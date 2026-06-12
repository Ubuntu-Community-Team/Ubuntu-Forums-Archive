---
title: "Jaunty won't let me have eth0 LAN and wireless USB at the same time"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by LancerNZ on 2009-05-26
I have an ethernet LAN of a dozen computers (e.g. "computer01" 10.0.0.1 through to "computer12" 10.0.0.12) which I want to set up as a renderfarm for Blender 3D animation package.

My ethernet LAN works by itself but my wlan USB dongle (picked up as DHCP) on computer01 only works if I delete the eth0 connection to the eth0 LAN.

I have written more detail (IP infor etc) at the forum of Linux Format, but no one has been able to solve i so far. Link here: [http://www.linuxformat.com/index.php?name=PNphpBB2&file=viewtopic&t=10206](http://www.linuxformat.com/index.php?name=PNphpBB2&file=viewtopic&t=10206)

From what I can see, it appears that connecting to the eh0 LAN makes the eth0 LAN the "default" network, thus losing internet access through the USB dongle at wlan0. I have no idea on how to change the "default" in Jaunty.

Googling for solutions, most people have said to "comment out" unnecessary devices in /etc/network/interfaces. This does not work, as mine is empty...

```
lancer@computer01:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

...so it appears that Jaunty must have some other method for storing the interfaces.

How can I get both my eth0 and wlan0 up at the same time, with wlan0 being the default gateway?

---

### Post by superprash2003 on 2009-05-27
try this [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by LancerNZ on 2009-05-27
Thanks for responding.

Okay, I'll start with my connection to the internet working (through wlan0 configured through DHCP [it becomes 192.168.2.3] and seeking the internet router which is 192.168.2.1)...

```
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
```

As you can see, there is no eth0 because I deleted it. This is because once it's connected, my internet through wlan0 goes down.

Now I add eth0 as...
IP: 10.0.0.1
Mask: 255.255.255.0
Default Route: 192.168.2.1
Primary DNS: 192.168.2.1


And now, the route command gives me...
```
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

I don't know why there is a 10.0.0.0 there, as I told it to set up 10.0.0.1. Also I don't make much sense of what this table is about.

Here are a few attempts (my random guessing because I'm not a network guru, which is why I am asking here) at trying to use the /sbin/route command to get some life out of wlan0 once a new eth0 connection has cut it off...

```
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
lancer@computer01:~$ sudo route add default gw 192.168.2.1 wlan0
[sudo] password for lancer: 
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
lancer@computer01:~$ sudo route add default gw 192.168.2.3 wlan0
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.3     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```
With each of the above /sbin/route -n commands, I test the internet through wlan0 and it is down. 

I next reset the network and the internet appears to be working, but pinging computer02 (10.0.0.2) has broken.
```
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
lancer@computer01:~$ 
```

...where to now?

---

### Post by Iowan on 2009-05-27
> **LancerNZ said:**
> I don't know why there is a 10.0.0.0 there, as I told it to set up 10.0.0.1. Also I don't make much sense of what this table is about.That would be the network address. My **route -n**:```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

I haven't tried multiple connections on my Jaunty laptop yet.  The older versions of New NM (Hardy and Intrepid?) would only handle one interface at a time... which kinda sounds like what you're seeing.  It *might* be possible to define your eth0 configuration in */etc/network/interfaces*. Worked for me when I was having DHCP problems.

There may be some other issues with your current configuration,  I dunno if a 10.0.0.X/8 address will be able to ping a 192.168.X.X address without some routing magic.

---

### Post by MJBoa on 2009-05-27
I would think about just using /etc/network/interfaces. Mine for example lets me use the internet through wlan0 and be connected to another machine through eth1, I use this computer to allow that computer to connect to the internet. Now it sounds like you want to be able to basically be connected to two networks.

Your last route table looks like what it might look like if you had no eth0 at all. What you want to do is, any connection to 10.0.0.* you'd like to go through the LAN. I'm not positive about this but check out this page for some explanation on how to keep these routes permanently.
[http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html](http://www.cyberciti.biz/tips/configuring-static-routes-in-debian-or-red-hat-linux-systems.html)

So what you'd do is add a route for 10.0.0.0 netmask 255.255.255.0 to go through 0.0.0.0 and interface eth0. or it MIGHT go through 10.0.0.1.

The problem I see with this table:
```
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

is the last line, to my eyes, should be through wlan0 not eth0, maybe try deleting that line and adding the same one but through wlan0 first.

That first line as well looks like it might be unnecessary, even part of the problem. That would redirect traffic to 192.168.2.1 through the eth0 interface. Try those two things first. What the new table might look like:

```
lancer@computer01:~$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
```


Here's my route table as an example for comparison.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0

```
Quite similar to yours, my wireless is 192.168.1 not 192.168.2 and the LAN is 10.0.0 not 192.168.0. But it's almost exactly the same idea.

Now also, I don't know because I'm just trying to logic this out is that the second line might be 10.0.0.1 as gateway not 0.0.0.0 but I'd try to switch the last line first.
Don't take this reply too seriously because I've never tested any of these things but I often wondered how something like this would work, so I gave it a shot.

---

### Post by LancerNZ on 2009-06-01
Thanks for the replies.

I can finally get the network working (both wlan and eth) by running **network-config** (installed via synaptic) after log in. This is not good enough because it fails to mount necessary shared drives in time for the renderfarm. I think it works by manipulatin this thing called iptables, but I'm clueless to this much detail. When I run it, I get something like the following showing...

```
Configuring device wlan1 :

$ iwconfig wlan1 mode managed
$ iwconfig wlan1 essid "LancerNet"
$ iwconfig wlan1 rate auto
$ iwconfig wlan1 key XXX...
$ ifconfig wlan1 up

DHCP may take a while, please wait...
$ dhclient wlan1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
pid 6203
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:1b:11:17:c0:60
Sending on   LPF/wlan1/00:1b:11:17:c0:60
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.3 on wlan1 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 903635485 seconds.

$ modprobe iptable_nat
$ echo 1 > /proc/sys/net/ipv4/ip_forward
$ iptables -t nat -A POSTROUTING -o wlan1 -j MASQUERADE
$ iptables -A FORWARD -i wlan1 -j ACCEPT

Warning ! Device wlan0 does not exists.

Configuring device eth1 :

$ ifconfig eth1 up
$ ifconfig eth1 10.0.0.1 netmask 255.255.255.0
$ route add 10.0.0.1 gw 192.168.2.1
$ modprobe iptable_nat
$ echo 1 > /proc/sys/net/ipv4/ip_forward
$ iptables -t nat -A POSTROUTING -o wlan1 -j MASQUERADE
$ iptables -A FORWARD -i eth1 -j ACCEPT

Warning ! Device wlan0:avahi does not exists.
Warning ! Device eth0 does not exists.
```


So... if _when working_ my network looks like this...
```
lancer@computer01:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.1        192.168.2.1     255.255.255.255 UGH   0      0        0 wlan1
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan1
```

...then what do I need to do in order to make this permanent at start up? Currently my /etc/network/interfaces looks like this...

```
lancer@computer01:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

...what should I configure (and specifically how) to set the network in concrete?

---

### Post by LancerNZ on 2009-06-03
* Bump *

...does anyone have an inkling of what might be going on? Should I start another thread "***networking that Ubuntu can't do***"?

Using network-config does not appear to be the answer after all, as even though it makes both wlan and eth work simultaneously, and all nodes see the samba share on computer01, it turns out the renderfarm program, which each computer runs from that share, is unable to make computers see each other until wlan is disabled. :(

It seems so simple... all I want is to have an ethernet LAN (10.0.0.x nodes)... and add to this a wireless gateway (192.168.2.1)... seems like such a simple thing. Can someone please figure out what might be happening? 

Are there developers out there where I can send this in as a bug?

---

### Post by Iowan on 2009-06-03
> **LancerNZ said:**
> Are there developers out there where I can send this in as a bug? Check [here]("http://ubuntuforums.org/showthread.php?t=1011078").

---


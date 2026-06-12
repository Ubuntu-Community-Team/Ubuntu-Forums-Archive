---
title: "Cannot connect to the interwebs"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by Jeroen De Dauw on 2010-12-31
For some reason I'm suddenly unable to connect to the interwebs on my desktop machine running the latest Kubuntu. I can connect fine with my laptop when I connect it to the same switch though.

My network situation is as follows (I'm not a network person, so yes, this is probably rather vague): my landlord owns a series of houses in the street which get "free internet" (as in, included in the rent, unable to not pay for it) by connecting to some authentication server thinghy with a user and password you get when renting a place. What I have is a single lan port in the wall, to which I have a switch connected, on which my desktop machine and (sometimes) laptop are connected.

What happens on my desktop machine is that I can login via the authentication thinghy, but afterwards I end up not having a connection. This happened a few weeks back to a Windows install I also have on my desktop machine, and where I got an error saying something about not finding the DNS server, so I guess this is the same issue. I tried directly connecting to google via ip, but this also fails. 

I don't really have an idea what could be wrong or how to debug. Please help :)

---

### Post by PatchesTheCaveman on 2010-12-31
Hi Jeroen De Dauw!  Sorry you're having trouble getting on the Internet.

I'm going to have you check a few things, but I have a friend who lived in a place with a similar setup so I think I know what's going on.  Is the service provided by [Pavlov Media](http://pavlovmedia.com) by chance?

Go to your KDE Menu/Kicker > Accessories > Terminal/Konsole.  In the black box that appears, type this and press Enter:
```
ifconfig
```

Copy and paste that into a reply here.  Then type this and press Enter:
```
dig google.com
```

Copy and paste that as well.

Also, is it working right now?

---

### Post by Jeroen De Dauw on 2010-12-31
>  Is the service provided by [Pavlov Media]("http://pavlovmedia.com/") by chance?

The authentication thinghy states "powered by lancom systems", so I guess not.

> Also, is it working right now? 	

No, it stopped working at some point and I have not been able to connect since. 

The output of these commands:

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:df:11:11  
          inet addr:172.16.22.166  Bcast:172.16.22.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fedf:1111/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:436477 (436.4 KB)  TX bytes:274337 (274.3 KB)
          Interrupt:42 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1614 (1.6 KB)  TX bytes:1614 (1.6 KB)
```

dig google.com

```
; <<>> DiG 9.7.1-P2 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

---

### Post by PatchesTheCaveman on 2010-12-31
Okay, you aren't getting assigned a proper IP address, so you can't access the Internet.  This is most likely outside your control.  You can try it force it to get an IP address by running this command on the terminal:
```
sudo dhclient eth0
```

If that doesn't work you'll need to call whoever and tell them you're not getting an IP address.

Another thing you can try is to take the switch out of the equation and plug the computer directly into the wall and see if that helps.  Run the command above again and try to get a new IP address.  

You can tell if you get one by running *ifconfig* again and looking at the *inet addr* next to *eth0*.  If it's something that **doesn't** start with *172.16* you should be good.

---

### Post by Jeroen De Dauw on 2011-01-01
I ran dhclient, but it doesn't appear to have helped.

sudo dhclient eth0
```
[sudo] password for jeroen: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1d:92:df:11:11
Sending on   LPF/eth0/00:1d:92:df:11:11
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 172.16.22.166 from 172.16.22.1
DHCPREQUEST of 172.16.22.166 on eth0 to 255.255.255.255 port 67
DHCPACK of 172.16.22.166 from 172.16.22.1
bound to 172.16.22.166 -- renewal in 5834 seconds. 
```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:df:11:11  
          inet addr:172.16.22.166  Bcast:172.16.22.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fedf:1111/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160761 (160.7 KB)  TX bytes:165331 (165.3 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3389 (3.3 KB)  TX bytes:3389 (3.3 KB)
```

Same thing after directly connecting my desktop with the thing in the wall.

I'm getting a 172.16. ip as well on my laptop (which does connect without any problems) when running ifconfig, so the ip address thing might be wrong.

Either way, I'll poke the people responsible for the network thing. Not the first time I'm having problems (or other people). Either they don't know what they are doing, or don't care to do it well >_>

---

### Post by PatchesTheCaveman on 2011-01-01
My bad, your IP address is fine.  Run ```
ip route show
``` and copy/paste what appears here.

---

### Post by Jeroen De Dauw on 2011-01-02
ip route show:

```
172.16.22.0/24 dev eth0  proto kernel  scope link  src 172.16.22.166 
169.254.0.0/16 dev vboxnet0  proto kernel  scope link  src 169.254.1.79 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 172.16.22.1 dev eth0  metric 100 
default dev vboxnet0  scope link  metric 1003 
```

---

### Post by Zorael on 2011-01-03
```
default via 172.16.22.1 dev eth0  metric 100 
default dev vboxnet0  scope link  metric 1003
```
Hmm. I might be misinterpreting here since I'm not used to **ip route show** output (preferring **route** myself), but doesn't this look like you have two default routes? I understand vboxnet0 is a VirtualBox virtual interface, though beyond that I'm not sure I know what it does.

```
$ sudo ifconfig vboxnet0 down
$ sudo dhclient eth0
$ dig google.com
```

vboxnet0 can be persistently disabled by commenting it out in **/etc/udev/rules.d/70-persistent-net.rules**. But I'm not sure what'll happen with your Internet connectivity from within VirtualBox.

---

### Post by PatchesTheCaveman on 2011-01-03
If you notice, the vboxnet link is link-local (that's what the "scope link") so connections should only follow that route if they fail via the default route.  I prefer *ip route show* to *route* because that latter does not show additional information like that.  The output of the *ip route show* command is also exactly the necessary input to the *ip route add* command to manually add that particular route to the system.

Runing Zorael's commands will ensure that VirtualBox isn't getting in the way of you're internet connection.  Also, try running:
```
mtr google.com
```
and let it run for about a minute and copy/paste what has appeared and then press CTRL+C to exit.  That might give us an idea of where the bottleneck is.

---

### Post by Jeroen De Dauw on 2011-01-05
This is the contents of my  file:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:92:df:11:11", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

I don't see any vbox specific stuff to comment out...

When I run

mtr google.com
it just sits there and doesn't output anything.

I tried out some more things to narrow down the problem, and I can:
* ssh from and to my desktop machine to and from my laptop
* access the interwebs via my desktop machine when I connect my phone and share it's 3G connection

And cannot:
* access the interwebs via my desktop when running kubuntu 10.10 off an installation dvd

This would seem to suggest that the problem lies neither with my hardware, nor my Kubuntu's configuration. Is that a valid deduction? I contacted the people responsible for the network, and predictably got the reply that if I can connect with my latop and not with my desktop, the problem must lie with my desktop, and not the network. :(

---

### Post by PatchesTheCaveman on 2011-01-05
Does your laptop run Windows or Linux?

If it's the former, run ```
ipconfig /all
``` on the laptop and ```
ifconfig
``` on the desktop.  (To get a terminal on Windows press WindowsKey+R and type *cmd* and press Enter.)

If it's the latter run ```
ifconfig
``` on both.  Copy and paste the output to a reply to this thread.  Maybe there's some soft of difference between the two's connection we can discern that might help you fix the desktop.

---

### Post by Jeroen De Dauw on 2011-01-11
I send an email to the network maintainers, and after a whole discussion how it was not my installation that was the problem, I got them convinced to have a look at it. Only took them a week to get whatever was wrong fixed. So since today I can magically connect again with my desktop (on which I'm now - yay). I've send them another mail asking what was wrong.

---


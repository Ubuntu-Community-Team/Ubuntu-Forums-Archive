---
title: "Networking problem - eth0 card drops signal."
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by Bruce M. on 2008-12-17
Hi Folks,

I'm having a problem. My built in ethernet card keeps loosing its signal and then reconnecting.

I'm using: eth0

I see here: [Networking]("https://help.ubuntu.com/xubuntu/desktopguide/C/networking.html") where it talks about:

> Xubuntu comes with a graphical networking utility. Launch it with Applications->System->Networking.
OK, it's v6.06 and I have 8.10 and I see I don't have that *Networking* is this normal?

**[COLOR="Red"]EDIT:[/COLOR]** - Just realized that it is the Panel Applet: Network Manager.  *DUH!!!!!!!!*

I have *pppoeconf* installed and so I try:

```
sudo pppoeconf
```
In terminal I see:

```
I found two ethernet devices:
eth0
pan0 *- (my comment: what ever that is?)*

Are all your ethernet devices listed above?
(If No, monconf will be started so you can load the
card drivers manually.)

Or press ESC to abort here
```

I hit ESC!

How can I configure my ethernet card to use DHCP or at least check to see if it configured properly as it keeps dropping carrier on me.

Thanks
Bruce

---

### Post by cariboo on 2008-12-17
In a terminal type:

```
ifconfig
```

the result should be something like this:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe9c:84b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45170604 (45.1 MB)  TX bytes:1961878 (1.9 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47512 (47.5 KB)  TX bytes:47512 (47.5 KB)
```

I was having the same problem with the onboard nic on my server. I replaced the network card and solved the problem.

Jim

---

### Post by Bruce M. on 2008-12-17
> **cariboo907 said:**
> In a terminal type:

```
ifconfig
```

Found a place that said to use ifconfig -a
So I tried that:

```
bruloo@bruloo:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d3:c3:c4:b7  
          inet addr:200.114.178.234  Bcast:200.114.178.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:8919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3181510 (3.1 MB)  TX bytes:796109 (796.1 KB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7192 (7.1 KB)  TX bytes:7192 (7.1 KB)

pan0      Link encap:Ethernet  HWaddr 36:1f:eb:61:61:95  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bruloo@bruloo:~$
``` 
Look at those errors.  :(  Oh there aren't any!  :D

And what is this pan0 thing?


> **cariboo907 said:**
> I was having the same problem with the onboard nic on my server. I replaced the network card and solved the problem.

Jim

I have an extra ethernet card, but If I can't figure out how to reconfigure this one (built-in), I have no idea how to do an installed one.

Any idea how to disable a built in Ethernet card?

Doing the command **ifconfig** without the **-a** give the same results without the **pan0**

Now what?
Bruce

---

### Post by Bruce M. on 2008-12-17
I've been busy researching this even more.

At [Ubuntu Geek(dot)com]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html") I found something useful.

Because of that I've installed: Network-manager that shows up in
```
Applications->System->Network
```
and I read:

> Configuring DHCP address for your network card

If you want to configure DHCP address you need to edit the /etc/network/interfaces and you need to enter the following lines replace eth0 with your network interface card

sudo vi /etc/network/interfaces

# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp

I looked at mine and it was:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```
sooooo ... I uncommented that last line, and here I am.

However I open:
```
Applications->System->Network
```
and I see:

```
Wired connection (pan0)
Roaming mode enabled

Wired connection (eth0)
Address: dhcp

Point-to-point connection
This network connection is not co...
```

Now on my panel I have:
Network Monitor beside NetworkManager Applet 0.7.0 (see image)
 
Network Monitor - is working
NetworkManager Applet 0.7.0 - **[COLOR="Red"][X][/COLOR]** - says device unmanaged.

I'm at a total loss.
Any help appreciated.

CHIMO!
Bruce

---


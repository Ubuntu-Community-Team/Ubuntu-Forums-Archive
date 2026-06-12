---
title: "Wired Internet Not Working Since Upgrade to 9.10 Months Ago"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Eric_WP on 2010-04-20
Hi everyone, 
I've grown frustrated (intensely) with Ubuntu of late, but that is, in a way, my own fault as well.  I'm not sure if this is the right spot to post a **wired internet problem**, but here we go.

I upgraded from 9.04 to 9.10 the first or second day it was released, going as far as waking up during the night just to make sure everything was fine in the installation.  I upgraded straight from the Upgrade Manager (no disk, no clean install, just download), and the new version worked nicely at first...for the most part.

From time to time, the internet would fail, and I would need to reset the modem (Highspeed DSL Westell Model 6100 modem) for the internet to be back to its former glory.  I thought it was just an occasional thing, nothing to worry about.  Weeks later, however, the internet shut out **indefinitely**. My only way to get online was booting into Windows Vista (I dual boot on a 34 bit), and I stayed there until about half a year later.  Today I thought I'd give it a shot again at fixing Ubuntu (I want my Ubuntu back! :) ) by trying to upgrade with the latest **Alternative Disk installation**.  An offline installation seemed like a nice idea, but it tries to force me to install using a network upgrade, despite me clicking on the '**NO**' button when asked if I would like to use the network or not for the upgrade.

Further details:  [LIST]
[*]The network manager says my modem is disconnected (it knows what it is and what it's called, but won't connect), despite all blinking lights active.
[*]I tried the whole ping-back thing, and I get no ping :(
[/LIST]

Any help to restore my internet on Ubuntu 9.10 please?

---

### Post by Eric_WP on 2010-04-21
Hello, does anyone have any idea how this could have happened?  I'm sorry if my writing style puts anyone off, I can't help it. :P

---

### Post by dineshs on 2010-04-21
If you have a DSL modem connected via ethernet,please post the output of
```
ifconfig -a
```

---

### Post by Iowan on 2010-04-21
This is the right spot to post a wired internet problem, and your writing style is fine ;)
As **dineshs** mentioned, **ifconfig -a** will show interfaces and if they have IP address (among other things). MTU can cause problems if it gets messed up - it should be in the neighborhood of 1500 (64 would be a problem). From a similar thread:

> **shikhar_sharma said:**
> OK i figured it out myself.It was just a simple command 
sudo pppoeconf
and thats it.a nice and interactive wizard comes up and tells u wat to do and voila my internet is up again.
anywayz thanks all of u for reading my post and posting such helpful information.

---

### Post by Eric_WP on 2010-04-21
Hi Iowan and dineshs! Thanks for the reply.  Here's the output:

```
eth0      Link encap:Ethernet  HWaddr 00:25:11:01:ae:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0f:db:83:ee:69  
          inet6 addr: fe80::20f:dbff:fe83:ee69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:320 dropped:0 overruns:0 frame:320
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2276 (2.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20698 (20.6 KB)  TX bytes:20698 (20.6 KB)


```

Whoops, I actually replied without looking at your post, Iowan.  I'll try out what shikhar did and post back if any success.

---

### Post by Eric_WP on 2010-04-21
So I tried out the sudo pppoeconf command, with no success.  I got the following error:

```
Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond.  
Please check your network and modem cables.  Another reason for the scan failure may also be 
another running pppoe process which controls the modem.

```

---

### Post by Iowan on 2010-04-21
If you can connect with Windows, I'll presume the cable is OK... The modem is acting as a DHCP server - or is Windows configured with a static address? (What address does Windows get?) If DHCP is the problem, you could configure a static address for the machine (but you'd want to keep it outside the DHCP server's range) to see if you could ping the modem.

(I've seen threads that suggest adding pppoeconf - and others that report success by removing it. )

Neither interface seems to have an IP address - I presume the other one is a wireless card...

---

### Post by Eric_WP on 2010-04-21
I'm almost positive that my IP is dynamic, although I'm not too sure (I may have seen it change every couple months).  How would I go about configuring a static address in Ubuntu?

As for the devices, I don't have a wireless card, I doubt it.  I've been using this rusty old modem since I purchased this computer last year, with no other device.

---

### Post by dineshs on 2010-04-22
You can configure static IP as follows 
Ref[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
ie 
Right-click on the nm-applet and then click on Edit Connections. 
Select the tab, wired 
select the connection (eth0 for example)and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 8.8.8.8 
then click apply 
Note: The IP address,mask ,gateway etc are examples.You can substitute your values

---

### Post by Eric_WP on 2010-04-25
Hi dineshs, sorry for my late reply.  We've been busy over the last few days :(

I tried what you suggested with no luck, but I am questioning whether I did this right or not.  I looked up the values from Windows, which gave me what you see in the below attachment (using the ipconfig /all command).  

I inputed the corresponding values where you indicated in Ubuntu, but it didn't restore anything, unfortunately.

Edit:  Actually, now that I re-read Iowan's post, was the static configuration thing only to get some ping or to restore my internet?  If the former, I haven't checked yet, but I will later tonight and post back.

---

### Post by dineshs on 2010-04-25
Pl post the output for
```
ifconfig -a
```
```
ping 192.168.1.1
```
```
ping 8.8.8.8
```

---

### Post by Eric_WP on 2010-04-25
Here you go:

The second line just went on looping forever, while increasing the icmp_seq by one or more.
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.46 icmp_seq=3 Destination Host Unreachable


```

Just as above, it just went on looping.
```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.46 icmp_seq=2 Destination Host Unreachable
From 192.168.1.46 icmp_seq=3 Destination Host Unreachable
From 192.168.1.46 icmp_seq=4 Destination Host Unreachable
```

Output for ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:25:11:01:ae:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0f:db:83:ee:69  
          inet addr:192.168.1.46  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:dbff:fe83:ee69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2321 dropped:0 overruns:0 frame:2321
          TX packets:957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:98644 (98.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:245432 (245.4 KB)  TX bytes:245432 (245.4 KB)




```

---

### Post by dineshs on 2010-04-25
You have 2 ethernet cards.can you just change the network cable to the other ethernet port and repeat the PINGs

---

### Post by Eric_WP on 2010-04-25
The modem can connect using either USB or ethernet cable.  I was using the USB connection, so that might explain the 'two ethernet cards'.  I connected using ethernet cable this time and these are the results:

```
ping 192.168.1.1
connect: Network is unreachable

```

```
ping 8.8.8.8
connect: Network is unreachable
```

Output for ifconfig -a
```
Link encap:Ethernet  HWaddr 00:25:11:01:ae:54  
          inet6 addr: fe80::225:11ff:fe01:ae54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24480 (24.4 KB)  TX bytes:984 (984.0 B)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304699 (304.6 KB)  TX bytes:304699 (304.6 KB)


```

---

### Post by dineshs on 2010-04-26
Try assigning IP manually to ethernet(To which modem is connected now) .Make the other one (USB)'automatic DHCP'via network manager

---

### Post by Eric_WP on 2010-04-27
I tried that too, with no luck.

I think I may have skipped to mention something important.  Whenever I create the static IP for the USB, it says "Connection Established", and gets some ping, but then keeps looping as I mentioned before.  When I set up a static IP for the Ethernet cable, there's simply no connection at all, along with no ping results.

In another note, is there any way to fix this back to how it was, where it managed my connections on its own without the need of static IPs?

---

### Post by dineshs on 2010-04-27
> **Eric_WP said:**
> 
In another note, is there any way to fix this back to how it was, where it managed my connections on its own without the need of static IPs?
You can use NM to do any setting
Instead of manual method,select Automatic DHCP
You can refer these guides
[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
because if you are using NM,
```
gksudo gedit /etc/network/interfaces
``` 
should contain only this 
```
auto lo 
iface lo inet loopback
```

---

### Post by NichoTL on 2010-04-27
Sorry to ask this most basic question: are you connected via USB or Ethernet? From the look of the Windows output, I'd say Ethernet but I could be wrong.

---

### Post by Eric_WP on 2010-04-30
Dineshs:  I'll have to take a look at that tomorrow, which is when I'll finally have a free day (it's been hectic all week lol).

NichoTL:  I'm actually connected via USB right now.  I've only popped in the Ethernet cable to create the outputs that Dineshs requested.

---


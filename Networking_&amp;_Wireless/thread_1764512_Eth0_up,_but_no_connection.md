---
title: "Eth0 up, but no connection"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by roblan on 2011-05-21
So i've been reading similar threads for 2 days, but cannot solve this problem.

I have an ubuntu 10.04 server and it was running fine through an ethernet cable, and all of a sudden I could not access the website that was hosting off of it. I checked the server, and I cannot ping my router or browse the web. I can see the computer on the network when viewing the router page on a different computer.



Here is some info 
ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:11:5b:c3:1e:6e  
          inet addr:71.242.172.250  Bcast:71.242.172.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fec3:1e6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37787 (37.7 KB)  TX bytes:119358 (119.3 KB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:221345 (221.3 KB)  TX bytes:221345 (221.3 KB)

```

sudo emacs /etc/network/interfaces

```

 vauto lo
iface lo inet loopback
erver01-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5b:c3:1e:6e  
          inet6 addr: fe80::211:5bff:fec3:1e6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0

auto eth0
iface eth0 inet static
address 192.168.1.55
netmask 255.255.0
gateway 192.168.1.1

```

Router Info on Computer
```
	server01
Connection Type:	  DMZ Host
IP Address:	71.242.172.250
(192.168.1.55)
```

Any advice is greatly appreciated :KS

---

### Post by tapi0n on 2011-05-21
Maybe it's not so much a software problem. Have you tried swapping cables? 

Also when doing 
```
sudo emacs /etc/network/interfaces
```
why does your netmask only consist of xxx.xxx.xxx and not xxx.xxx.xxx.xxx?

---

### Post by roblan on 2011-05-22
Thanks for the response.

I was editing the file with different combinations, 
like 255.255.255.0 and  255.0.0.0 and must have messed it up.
I've changed it to  255.255.255.0, but still the same problem.
  
I've tried multiple cords which worked for other computers to no avail.

---

### Post by Iowan on 2011-05-22
Perhaps re-post your */etc/network/interfaces*... If what you posted is actually in there, it needs some editing - unless its a typo, this should not be there:
```
 vauto lo
iface lo inet loopback
erver01-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5b:c3:1e:6e  
          inet6 addr: fe80::211:5bff:fec3:1e6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
```

---

### Post by chili555 on 2011-05-22
> eth0      Link encap:Ethernet  HWaddr 00:11:5b:c3:1e:6e  
          inet addr:[COLOR="Red"]71.242.172.250[/COLOR]  Bcast:71.242.172.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fec3:1e6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37787 (37.7 KB)  TX bytes:119358 (119.3 KB)
          Interrupt:10 Base address:0x4000 I believe my colleague Iowan also would like to understand how you got an external IP address (i.e. Verizon).

Is the router hooked up correctly?

---

### Post by Iowan on 2011-05-22
> **chili555 said:**
> I believe my colleague Iowan also would like to understand how you got an external IP address (i.e. Verizon).
That, too... ;)

---

### Post by roblan on 2011-05-22
As of right now, this is the contents of the file
```

 vauto lo
iface lo inet loopback
server01-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5b:c3:1e:6e  
          inet6 addr: fe80::211:5bff:fec3:1e6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0

auto eth0
iface eth0 inet static
address 192.168.1.55
netmask 255.255.255.0
gateway 192.168.1.1
```

I am not quite sure how I got a static IP before, I just followed a tutorial i found online a while ago. I'm thinking that might be the problem because even when the server is off an unplugged, I still see it showing up under my network in the router page:
```
	
server01
Connection type:	DMZ Host
IP Address:	71.242.172.250
(192.168.1.55)
IP Address Allocation:	Static IP
MAC Address:	00:11:5b:c3:1e:6e

```

---

### Post by Iowan on 2011-05-22
The file *should* look more like:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.55
netmask 255.255.255.0
gateway 192.168.1.1
```

---


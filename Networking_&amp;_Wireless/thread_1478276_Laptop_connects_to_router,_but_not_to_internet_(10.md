---
title: "Laptop connects to router, but not to internet (10.04 / Gateway / Linksys)"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by robine on 2010-05-09
I just became the proud owner of a new laptop (Gateway NV5378U). So, I'm dealing with wireless issues for the very first time. I'm running 10.04. Also, not sure if it's relevant, but I have a dry DSL connection.
 
My dad helped me set up the router (Linksys Wireless-N WRT120N) at his house, so that I could take it home and use it without problems. He configured it via the Linksys / Cisco web site.
 
However, once home, it didn't work. Though it says it's connected to the network, I can't access the internet; any page I try just says "loading..." If I connect the laptop directly to the DSL, there's no problem getting online. I just can't seem to connect wirelessly, which puzzles me, because it seemed so easy at my dad's place.
 
What can I do?
 
(Also, does the kind of internet connection matter (i.e. DSL or cable)? Sorry if this is a redundant question, but it's a whole new world for me.)
 
Thanks for any guidance you can offer!

---

### Post by robine on 2010-05-09
Just got home. Tried to establish a wired connection from the router to the laptop, hoping that would at least be a starting point. 

Doesn't work, even though I have it set up properly (I think):
DSL -> modem -> router -> laptop

So, this tells me it must be a problem with the router. But why did it work on another wireless connection (at my dad's) so effortlessly?

Help? :confused:

---

### Post by Iowan on 2010-05-09
When connected to the router, does the machine get an IP address? Check from a terminal (Applications>Accessories>Terminal) :```
ifconfig -a
```

---

### Post by robine on 2010-05-09
> **Iowan said:**
> When connected to the router, does the machine get an IP address? Check from a terminal (Applications>Accessories>Terminal) :```
ifconfig -a
```

Hi! Thanks for responding, Iowan.
Here's what I got: 

```
robine@robine-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:2d:72:28:8e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe72:288e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21211870 (21.2 MB)  TX bytes:4981718 (4.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1248 (1.2 KB)  TX bytes:1248 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:c7:fb:03  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fec7:fb03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9685238 (9.6 MB)  TX bytes:16262 (16.2 KB)
```192.168.1.1 is the address associated with the Linksys router, from what I can tell. That's about all I know...

---

### Post by rasturn on 2010-05-09
same gateway, i turned off the "N" on the router, 54mb setting and it stay connected, i rather use N but it will have to do until they fix it. hope this helps

---

### Post by Vaphell on 2010-05-09
eth0 is a wired connection and it got 192.168.1.100 address, wifi on the other hand x.x.x.101, router apparently assigns numbers from the 100+ range. Locally it works imo.

there can be a problem with internet connection - login to administration page (usually [http://192.168.1.1](http://192.168.1.1)) of your router and see if the router gets the IP address from the internet provider's dhcp server.
If the answer is yes, there can be some problem with your isp rules. Some internet providers register MAC address (unique number of the physical device, listed as HWAddr in the output of ifconfig) and don't allow anything else to get through - router, ethernet and wifi have different adresses and if such rules are in place they may cause problems.

I experienced such stuff and MAC address cloning feature available at administration page came in handy. In my case laptop was registered earlier and router added later was cut off. I ordered router to introduce itself with MAC address of the laptop ethernet adapter to cheat the isp and everything was fine since then. I could go through the hassle of changing/registering new device, but that is a waste of time when the router can do it and additional devices allowed may cost extra.

---

### Post by benroth1981 on 2010-08-26
I had a problem where my laptop was connected to the wireless network, but I could not get on the internet. Google was giving me Error 105. 
The solution was to go to... 
SYSTEM
PREFERENCES
NETWORK CONNECTIONS
WIRELESS Tab
Chose your network
EDIT
Then I entered the MAC address from the label on my router. Mine happened to be a 2WIRE router for my UVerse. 

It fixed it instantly.
Hope this helps

---


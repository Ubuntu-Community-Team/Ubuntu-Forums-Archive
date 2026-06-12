---
title: "A &quot;unique&quot; sort of networking issue. [PICTURES]"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by CodyLeeK on 2013-05-25
Hi there.
I've made a NAS (network-attached storage device), and it seems to be working fine. It's running off of Samba.

The thing is, the server computer is an old HP Pavilion a622n, and it does not have a wireless card. It's running Ubuntu 12.04. Now, my laptop (one of many client computers), is connected to Wi-Fi, and I have it tethering the wi-fi connection to my server, via Ethernet cable, as seen below:

[IMG]http://www.codyleek.co.uk/snaps//68bj30.jpg[/IMG]

Now, this works. I can view the server's shared drive fine on the client laptop. The thing is that I am the only one who can do this. No other computer on my network can view the hard drive. 
Any ideas?

---

### Post by scbingham on 2013-05-25
You will need to bridge the wi-fi & wired connections, as they are effectively two separate networks.

Lots of examples how to do this if you do a google search.

---

### Post by CodyLeeK on 2013-05-25
> **scbingham said:**
> You will need to bridge the wi-fi & wired connections, as they are effectively two separate networks.

Lots of examples how to do this if you do a google search.

No, because my laptop is the one that is sharing the internet with the desktop. Basically, the desktop is running a wired connection because my laptop shares connections via Ethernet.

So, really, my laptop is just tethering the Wi-Fi connection to the server.

---

### Post by LordDelta on 2013-05-25
> **CodyLeeK said:**
> No, because my laptop is the one that is sharing the internet with the desktop. Basically, the desktop is running a wired connection because my laptop shares connections via Ethernet.

So, really, my laptop is just tethering the Wi-Fi connection to the server.

No, you just don't know much about networking. A tether means that you are running a router on your laptop. All computers behind routers can reach the internet, but not all computers on different networks can see each other. As previously mentioned, you need a bridge, not just a plain old tether.

If you want to prove this to yourself, take note of your internet adapter name, run:

ifconfig
(or ipconfig /all if you are stuck on a Windows box).

on the two different machines that 'can't see each other', and if their subnets don't match, they can't see each other. Period (unless, as mentioned, you have a bridge of some sort).

E.g. 192.168.1.13 and 192.168.2.2 can't see each other, as the respective subnets are different (192.168.1.* and 192.168.2.*)

A word of advice:

The internet is made up of a bunch of computers. There is nothing special about your home network: all the rules (and hassles) that apply to actual internet architecture apply to your home network - unless you're not running the Internet stack (e.g. you are using a WiFi mouse). About the only part of networking that takes no reading to get working is getting to a website; assuming of course your OS handled the internet connection for you.

---

### Post by CodyLeeK on 2013-05-25
> **LordDelta said:**
> No, you just don't know much about networking. A tether means that you are running a router on your laptop. All computers behind routers can reach the internet, but not all computers on different networks can see each other. As previously mentioned, you need a bridge, not just a plain old tether.

If you want to prove this to yourself, take note of your internet adapter name, run:

ifconfig
(or ipconfig /all if you are stuck on a Windows box).

on the two different machines that 'can't see each other', and if their subnets don't match, they can't see each other. Period (unless, as mentioned, you have a bridge of some sort).

E.g. 192.168.1.13 and 192.168.2.2 can't see each other, as the respective subnets are different (192.168.1.* and 192.168.2.*)

A word of advice:

The internet is made up of a bunch of computers. There is nothing special about your home network: all the rules (and hassles) that apply to actual internet architecture apply to your home network - unless you're not running the Internet stack (e.g. you are using a WiFi mouse). About the only part of networking that takes no reading to get working is getting to a website; assuming of course your OS handled the internet connection for you.

Alright, thanks.
Instead of making a bridge, could I just buy a wireless network adapter for the server box, or just run a big ass Ethernet cable from the computer to the router?

---


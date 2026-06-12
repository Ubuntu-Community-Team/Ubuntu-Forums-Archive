---
title: "Server Network Configuration Problem"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by arman89 on 2009-10-10
Hey Guys,

I don't have much experience with Ubuntu, yet I wanted to set up a hardy server for the website I'm trying to build. I am following the instructions at [this]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") site, and I came across a problem and have been trying to fix it for a couple days now with no luck.

I have a static ip and a domain, yet when I try apt-get update after I install the server, first it says 101 no internet connection. So I change the info on my /etc/network/interfaces, but when there seems to be an improvement, then I get an "113 no route to host error". Obviously something is wrong with the /etc/network/interfaces file.

So this is what the ./interfaces file is supposed to look like;

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address     ...
    network     ...
    netmask     ...
    broadcast   ...
    gateway     ...

I know my static ip, but I don't know anything about the other ones. I also have 9.04 on the same laptop, and I found out my connection info by right clicking the network manager, so I tried to fill out ./interfaces with that information on the server, but that didn't work either.

How do I enable the internet connection so I can actually do apt-get update on the server? I phoned my ISP and they have no clue what my network and netmask etc. are. Is there a way to find that out? Should "address" in ./interfaces be the static ip address that I just got? 

Sorry if it the questions seem silly, but nothing I found here or elsewhere worked.

Thank you in advance,

Arman

---

### Post by kreggz on 2009-10-10
Try using traceroute to determine if you have used the wrong default gateway or if routing hasn't been correctly setup for you subnet.

---

### Post by Iowan on 2009-10-10
Check **route -n** to verify the gateway setting is correct, and check */etc/resolv.conf* to see if the correct nameservers are there.

---

### Post by arman89 on 2009-10-11
Hey,

I tried traceroute, but I don't have it installed and I can't apt-get anything. My ./interfaces looks like

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address    192.168.1.1
      network    255.255.255.0
      broadcast  192.168.1.255
      gateway    192.168.1.1

And when I try apt-get update it gives 113 no route to host error. route -n gave me

Kernel IP routing table
Destination   Gateway   Genmask        Flags Metric Ref Use Iface
192.168.1.0   0.0.0.0   255.255.255.0  U     0      0   0   eth0
0.0.0.0     192.168.1.1  0.0.0.0       UG    100    0   0   eth0

I don't know what I'm supposed to make out of that, though. By the way, my static ip is 81.214.248.60, should I replace it with the address thing in ./interfaces?

---

### Post by arman89 on 2009-10-11
And my /etc/resolv.conf looks like this;

search armanoz.com
nameserver 81.214.248.1

armanoz.com is my domain and my static ip is 81.214.248.60.

---

### Post by Iowan on 2009-10-11
> **arman89 said:**
>  I phoned my ISP and they have no clue what my network and netmask etc. are.  That's a bad sign... If they assigned the address, they *should* know the netmask. ISP's don't always use 255.255.255.0.
Does this machine hook directly to Internet, or is there a router, modem, etc.? If it's directly connected, then the static address (which you may want to camouflage...) is the one that should be in */etc/network/interfaces*. The information you've given would work - if there is a router in the system (with address 192.168.1.1). In that case, the router would need to be set up with your static address.

---

### Post by arman89 on 2009-10-11
I finally managed to get the network up and runnung. But I have a new problem now. As I was installing mysql, I set a root password, and I actually wrote it down on a piece of paper. But now, when I'm trying to install ISPConfig, it asks me my MySQL user and password and it doesn't accept my password. How is this possible? I didn't have to specify a username, so I just put in root, but it doesn't accept my root password.

---

### Post by houstonbofh on 2009-10-11
You really want a new thread for this...

---


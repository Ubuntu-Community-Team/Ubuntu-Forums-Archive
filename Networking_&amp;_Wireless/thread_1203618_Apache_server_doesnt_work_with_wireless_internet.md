---
title: "Apache server doesnt work with wireless internet"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by Virtualboxbuntu on 2009-07-03
I am a web developer and I like to test my PHP scripts locally before uploading them to my website. **My problem, in a nutshell,** is that I can only access web pages on my computer when it's wired to the router, and not when connected wirelessly. Details are as follows:

So I installed LAMP on my Kubuntu Jaunty desktop, which has wireless Internet. I can access [http://192.168.0.102/](http://192.168.0.102/) (the computer's IP address) fine. But if I type 192.168.0.1 into my laptop, it can't access anything. I tried installing LAMP on my laptop and I can access it fine from the laptop. If I try to access the laptop from my desktop, I can't.

But if I plug the laptop into ethernet, I can access it from my desktop. What's going on here?

---

### Post by Hobgoblin on 2009-07-03
> **Virtualboxbuntu said:**
> I can access [http://192.168.0.102/](http://192.168.0.102/) (the computer's IP address) fine. But if I type 192.168.0.1 into my laptop, it can't access anything. 

This bit seems rather confused, can you elaborate?

What IP address does the system have when connected by wifi?  Is it the same as when connected by cable?

---

### Post by Virtualboxbuntu on 2009-07-03
It just magically started working, so it doesn't matter anyway.

What I meant was that if I try to access web pages on my desktop, from my laptop, it doesn't work. But it does work when the cable is connected.

But it works now, so don't worry about it.

---

### Post by philcamlin on 2009-07-03
ahah i was just going to comment put ah well

good to see it works 

mine is on wifi too :D

---

### Post by lchoate on 2009-09-08
I am having a similar issue. I work on several sites at a time and try to mirror my production environments as best I can.

My home network is 192.168.5.x and I connect using wired or wireless.
The other places I connect (Work/Coffee shop) wirelessly and everything seems to work fine as long as its not a 192.168.5.x network.

Here is my interfaces file:
```

auto lo
iface lo inet loopback

auto eth0:1
iface eth0:1 inet static
address 192.168.5.60
netmask 255.255.255.0

auto eth0:2
iface eth0:2 inet static
address 192.168.5.61
netmask 255.255.255.0

```When I first bootup or connect to a new network on wireless, I can access the internet but can not access my sub-interfaces... so I do the ol' 
```
sudo ifup eth0:1
sudo ifup eth0:2

```To which I usually get something like:
```

lucas@lucas-laptop:~$ sudo ifup eth0:1
 * if-up.d/mountnfs[eth0:1]: waiting for interface eth0:2 before doing NFS mounts
lucas@lucas-laptop:~$ sudo ifup eth0:2

```What its mounting, I don't know... but then I can access my sub-interfaces but not the internet. It seems to be a routing issue, since a traceroute to an internet host shows 5.60 as the gateway, but I've never had routing problems before. So i think its a configuration thing more than a routing thing.

If I just plug in the cable, it all works as soon as I "up" the sub-interfaces. 

Questions: Why am I having to "up" the interfaces at all. My home servers sub-interfaces come up automagically?
How can I fix it?

Thanks!

---


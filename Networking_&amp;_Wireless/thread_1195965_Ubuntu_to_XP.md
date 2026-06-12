---
title: "Ubuntu to XP"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Kruptein on 2009-06-24
Okay, so I have a laptop with ubuntu, it connects wireless with a D-LINK router, this works fine,
my pc, which is a xp, can't connect to the network, I dunno if it is the wireless usb or because my wpa2 isn't configured right.

Is it possible to connect with a cable my xp with my laptop, so I can go on the internet with the xp via the ubuntu?

To make it easier:

XP [cable] Ubuntu [wireless] Router
[cable]: Howto?
[wireless]: Works :)

---

### Post by jerrrys on 2009-06-25
this may be what your looking for

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Kruptein on 2009-06-26
Not entirely,

the idea is the same, the only difference is that in that article it is between two ubuntu's and I need one ubuntu and one windows xp,

that's what makes it so difficult

---

### Post by KarlIvan on 2009-06-26
if we knew a little bit more about your xp, then we might be able to help get that working, and skip this whole tunnel/routing (or atleast thats what i think your trying to do) thing

---

### Post by Kruptein on 2009-06-30
Okay:
Microsoft Windows Xp Home Edition
Version 2002 Service Pack 2

Hewlett-Packard Company
Compas Presario
AMD Athlon(tm) 64 Processor
3700+
Kloksn.  1.77 GHz, 1,00 GB

This is just configuration -> system info
So if you need something else just ask me!

---

### Post by KarlIvan on 2009-06-30
not exactly what I meant. I meant how is your router set up, how is your connection on your pc set up, etc etc.

How about this. I don't know the reason why, but I know the fix for it: I've heard of routers giving you crap for hooking up to them if your not configured a certain way. 

[Help setting up a router](http://portforward.com/networking/static-xp.htm)

It's literally a guid for dummies. It tells you how to open the command prompt. That page may help, but some of the stuff the guy tells you to do is useless (or so I think anyway). The only thing you should really have to do is set your ip address, your subnet, and your gateway. You may have to statically set your DNS, but besides that, I don't see it not working after that.

Anyway, if you still want to tunnel traffic, I don't know if I can really help you there. I've dabbled with racoon, and I'm messing with strongswan now. But 1) that's for encrypting traffic, and 2) I'm doing it in IPv6 which beleive it or not, is what is making this not work (long story short, it's not very well supported in some of these programs, and I mess around with lots of settings trying to figure out why its not working, so I dont know what settings work, and what dont with IPv4)

---

### Post by dmizer on 2009-06-30
> **Kruptein said:**
> Not entirely,

the idea is the same, the only difference is that in that article it is between two ubuntu's and I need one ubuntu and one windows xp,

that's what makes it so difficult

From the howto:
```
Any OS can connect to the internet as an ICS client as long as networking has been configured correctly.
```
All you need to do is configure Windows for a static IP address (the example is 192.168.0.100). You'll also need to set static gateway (in the example it's 192.168.0.1) and manually enter DNS servers (you can use [OpenDNS](https://www.opendns.com/start/device/windows-xp) if you don't know what your ISP DNS servers are).

---


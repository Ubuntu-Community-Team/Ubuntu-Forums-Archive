---
title: "Sharing DUAL LAN with another linux box"
date: 2006-02-12
forum: Networking &amp; Wireless
---

### Post by floyd27 on 2006-02-12
Hey..
I have my main comp (Kubuntu) connected to my modem (adsl).
My mobo, has DUAL lan, and I have in the past connected 2 comps (windows) with it. I have not yet with linux.

The comp I wish top connect to the other lan port iis running ubuntu as well.
if anyone has any tips or links for me to look at to get this configured properly, that would be great.. Im not sure of anything at this point so any help would be great..:)

---

### Post by mips on 2006-02-13
You basically have to configure each interface with it's own network details, ie.
eth0= network 192.168.0.0
eth1= network 192.168.1.0
eth2=network 192.168.2.0

And assign IPs to the interfaces accordingly. You then have to do IP forwarding.

In the past with Ubuntu I used Firestarter but it was only to share with one PC.

Have a look into Gaurddog & Guidedog for Kubuntu, packages are in the repositories. Just read the online manuals for them.

---

### Post by floyd27 on 2006-02-13
Sweet thanx for the reply...

Im only trying to connect 1 more comp to the existing one that is already connected, so ill give it a go..

---


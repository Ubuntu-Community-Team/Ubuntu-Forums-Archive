---
title: "Fresh install of Ubuntu Server 10.10 keeps dropping off network"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by dean.p on 2011-04-10
Hi, other than my CentOS web server... I'm pretty green when it comes to linux.

I've just built a new system this week to be a Linux Samba fileserver on a predominantly Windows XP and 7 network.

**Main Hardware is:**
Intel Core i7960 Nehalem 3.2Ghz
Asus P6X58D-E mobo (which has the Marvell 88e8056 ethernet controller)
Corsair CMP6GX3M3A1600C8 (3x2GB)
Dlink DIR-655 router

**Problem**
I installed Ubuntu Server 10.10 (about 5 times this week now!) and once I have the system installed and I ssh in from my laptop over the LAN (using putty), I sometimes lose connection to the server. I cannot ping the server from my laptop, any other pc on the LAN or my Iphone and on the server I cannot ping my router. Ubuntu does not say my eth connection is lost, I do get a "sky2 0000:05:00.0: eth0: tx timeout" message then a "link is up at 1000 Mbps, full duples, flow control both" message... which I guess inmplies that it was down. This seems to happen after a stright install (only installing ssh package) and also after full updating (apt-get upgrade).

Then after a while.. maybe a minute, the connection is back. Seems quite random, although I eventually got Samba working, logged into a shared folder from my windows 7 and transfered a 350MB movie file (on the second attampt as I lost connection again), then tried to play it over the network and lost connection before it could play... that happens every time.

**So, what I've tried:**
- Tried downloading and installing the latest Marvel linux driver for the 88e8056 ... installed and didin't fix the problem.

- made up new lan cables ... no fix

- replaced the DIR-655 with a brand new Netgear N600 router .. still had the porb.

- Installed CentOS (bit of a nightmare) ... still dropped out randomly.

- so, I then considered maybe hardware failure, so installed Windows 7. Once up and running, copied 1.5GB file across no probs and streamed an hour of movie to my laptop with no issues.

- reinstalled Ubuntu server 10.10. Network continues to drop out

So, fresh out of ideas... I might try the 10.04 version or Debian but I aint holding my breath... I really think is some driver or network config setting hidden somewhere that I obviously don't know about.

---


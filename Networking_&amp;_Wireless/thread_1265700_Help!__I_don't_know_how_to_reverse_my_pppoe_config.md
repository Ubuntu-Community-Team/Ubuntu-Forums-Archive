---
title: "Help!  I don't know how to reverse my pppoe configuration!"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by quigl1kd on 2009-09-13
Ok, so I've been using 9.04 with wireless for a while now and it has worked perfectly.  However I just moved into a new apartment that only allows wireless, no ethernet.  They have a router we have to connect to.  When I try to connect I find out that it is some sort of pppoe connection that requires a username and password.  Of course there is no installer for linux, but only a downloadable client for mac and windows.  So I started sudo pppoeconf and ran it through, and it worked!  It was connected, however when I rebooted later it stopped working, and now when I click on the connection icon on the toolbar only VPN connection is listed.

It says "device not managed" under wired and wireless connections.  So I can't connect at all anymore, even if I use a regular wireless router at a coffee shop.  My windows connection works fine...I don't get it.

Any ideas?

---

### Post by quigl1kd on 2009-09-13
Is there something else I should be doing to get people to respond to this post?  I'm a noob to the forums and I don't know how to get this post noticed.

---

### Post by quigl1kd on 2009-09-14
comon guys can't someone just point me in a direction to look?  I've been on google for hours..

---

### Post by Iowan on 2009-09-14
> **quigl1kd said:**
> It says "device not managed" under wired and wireless connections.  So I can't connect at all anymore, even if I use a regular wireless router at a coffee shop.  My windows connection works fine...I don't get it.
Any ideas?Check under */etc/network/interfaces* for configuration.  That'd cause NM to abandon managing it.

---

### Post by quigl1kd on 2009-09-15
How do I do that?  I'm kind of a n00b.

---

### Post by Iowan on 2009-09-15
Open a terminal (Applications>Accessories>Terminal), enter **less /etc/network/interfaces**. Ideally, the file will contain only:```
auto lo
iface lo inet loopback
```Otherwise, you can edit the file. 
(might want to make backup first with **cp /etc/network/interfaces /etc/network/interfaces.bak**)
 From the same terminal, you can **sudo nano /etc/network/interfaces** or (if you'd prefer a graphical editor) **gksudo gedit /etc/network/interfaces** and comment out (insert # at beginning of line) the extra lines. Save the file and restart (or reboot).  Hopefully Network Manager will play nice, then.

---

### Post by quigl1kd on 2009-09-16
Ok so when I do that it says 

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth2 up # line maintained by pppoeconf
provider dsl-provider

auto eth2
iface eth2 inet manual




So it does recognize the right router, and it knows pppoeconf is managing it...but when i run pppoeconf again it says that a pre-existing configuration exists and therefore can't manage it.  Do I need to enter the # before the first "auto"?

---

### Post by Iowan on 2009-09-16
My DSL modem handles the PPPOE stuff - my workstation connects to modem as if it were a router, so my PPPOE advice may not be the best... I would comment out everything but the two "lo" lines (if your file is missing those, I'd add them back in). If it doesn't help, you can uncomment the lines.

---

### Post by quigl1kd on 2009-09-17
Thanks!  That worked for a regular connection, however now I'm back to where I was before I ran pppoe conf, meaning it won't connect to my apartment internet.  That is alright with me though I'll figure it out..
 
appreciate it

---

### Post by Iowan on 2009-09-17
Did you use (or have you checked) the DSL option under Network Manager?

---


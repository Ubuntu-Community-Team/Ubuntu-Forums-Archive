---
title: "Server 9.10 Won't Connect any more"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by doublepedaldylan on 2010-03-22
I set up 9.10 as a file server at my house, connected through the router via LAN.  I had everything working, using it as a Samba file server.  I moved to to my college apartment and I am now having troubles...  I changed the network information in /etc/networking/interfaces  to what it should be (or at least I thought so...)

I can ping myself, but nothing else.  Also, on my router configuration page, the server is coming up as a connected device with the correct IP address that I set it to.

Any ideas what is going on?  Is there more specific info you need? Just ask.  Thanks.

Semi-n00b here too, but I have a few years of casual experience.

---

### Post by Iowan on 2010-03-23
So, *ifconfig -a* shows the proper IP address and the router knows it's there, but the server can't ping the router? I presume there's no firewall running...

---

### Post by doublepedaldylan on 2010-03-24
hhmm, didn't try pinging the router...  Problem is, I have a router attached to the University's network, so I don't know what firewall settings they have.  ...It's been a pain to get torrents to work for my game add-on files, or getting new ubuntu distro's...

I changed it back to dynamic and reserved the IP on the router for that machine.  It is working again so far (currently connected to the file system).  So for the time being it is ok...

the example stated /interfaces  should look like

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.100
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1

and I went with

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.10
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1

bc the router's IP was 192.168.1.1                     xxx.xxx.1.x
at home, it was 192.168.0.1 so in the third field(?) I had xxx.xxx.0.x

was my logic flawed?  When i switched back to dynamic, it was stating something in the stats about netmask being 255.255.255.255
don't know if that matters...

---

### Post by Iowan on 2010-03-24
> **doublepedaldylan said:**
>  When i switched back to dynamic, it was stating something in the stats about netmask being 255.255.255.255
don't know if that matters...255.255.255.255 doesn't seem like a valid subnet - that would have zero hosts, but I'm not sure if you want to fix what is working.

---


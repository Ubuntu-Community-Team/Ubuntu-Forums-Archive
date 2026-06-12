---
title: "Is Ubuntu DHCP or static when it's 1st installed?"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by GARoss on 2009-06-01
When I 1st installed Ubuntu it found an internet connection & was up & running. Is this connection DHCP or static? How can I check?
Thanks

---

### Post by MichaelSammels on 2009-06-01
If the Internet was up and running, then you are connected via Ethernet. You can use the Network Manager to find out:

System -> Administration -> Network Tools

Hope this helps.

---

### Post by lisati on 2009-06-01
Most of the installations of Ubuntu I've done enable DHCP.....

---

### Post by Iowan on 2009-06-01
Default installation is DHCP (even for servers), but manual is an option... in which case you'd have been asked for address, netmask, etc.

---

### Post by DGortze380 on 2009-06-01
> **GARoss said:**
> When I 1st installed Ubuntu it found an internet connection & was up & running. Is this connection DHCP or static? How can I check?
Thanks

It's not static unless you specifically input at least:
IP Address
Netmask
Gateway

---

### Post by GARoss on 2009-06-01
Thanks.

---

### Post by midfel11 on 2009-06-01
How can you change it to use a static IP?  I'm behind a router in a home network and would like to keep the same ip.

---

### Post by DGortze380 on 2009-06-02
> **midfel11 said:**
> How can you change it to use a static IP?  I'm behind a router in a home network and would like to keep the same ip.

You need to edit /etc/network/interfaces

[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

---

### Post by dmizer on 2009-06-02
> **DGortze380 said:**
> You need to edit /etc/network/interfaces

[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

In Jaunty, /etc/network/interfaces doesn't cooperate with network-manager. If you configure your static network according to that howto, you'll end up with a non-functional network. You'll have to uninstall network-manager first.

An alternative is to uninstall network-manager and download (on a separate computer) gnome-network-admin [https://launchpad.net/ubuntu/jaunty/i386/gnome-network-admin/2.22.2-0ubuntu3](https://launchpad.net/ubuntu/jaunty/i386/gnome-network-admin/2.22.2-0ubuntu3) 

Once gnome-network-admin is installed, you can configure static IP by going to system > administration > network.

---

### Post by Iowan on 2009-06-02
I must have been one of the lucky ones.  When "auto eth0" failed to get a DHCP address, I tried configuring a manual address in /etc/network/interfaces, and was able to get on network.  More of the story is [here]("http://ubuntuforums.org/showthread.php?t=1156441").  If it doesn't work, you can comment out (or delete) the settings. If it DOES work, Network Manager may still complain.

---


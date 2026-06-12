---
title: "Networkmanager chooses fastest LAN connection but slowest WAN connection"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by oneindelijk on 2009-04-08
Hi, 

I'm connected to my LAN which is currently on limited internet speed.
I'm also connected to my neighbours WAN (asked him permission) which
has normal speed.
Unless I disconnect my LAN, traffic routes over my own gateway.

I've noticed copying a large file from my server the networkspeed going up without interuption when I plug in the cable, so the networkmanager is correctly switching to the fastest connection.

I was wondering if there is a way to make networkmanager chooses the fastest route for WAN traffic ?

---

### Post by jeremyjjbrown on 2009-04-08
I'm sure that there is a way to configure the kludgey Gnome Network Manager to select the fastest connection. Or, you can switch to a much better network interface, Wicd. I think you might like it better. If you install it, it will automatically remove Network Manager. If you don't like Wicd (not sure why you wouldn't) you can enter this command in the terminal.

sudo apt-get install network-manager

And it will automatically put Network Manager back. There is the link for installing Wicd.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by superprash2003 on 2009-04-08
hope this helps [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---


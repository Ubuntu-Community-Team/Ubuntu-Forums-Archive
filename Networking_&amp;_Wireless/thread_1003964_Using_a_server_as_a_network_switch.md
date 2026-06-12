---
title: "Using a server as a network switch"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Mattventura on 2008-12-06
I have a server with multiple ethernet cards. Is it possible to use the server as a network switch? Also, is it possible to route the traffic that is going to be forwarded to another computer (or has been sent from another computer to the internet) through one network card, and the traffic between the internet and the server through a different card? If it helps, my setup will look like this:

```

                      Modem              NAS
                        |                 |
                     WRT54GL--------Other switch------Wifi AP
                        |                 |
    Other devices----Server           Computer

```

---

### Post by adaptr on 2008-12-06
> **Mattventura said:**
> I have a server with multiple ethernet cards. Is it possible to use the server as a network switch?
You can bridge them, so they logically belong to the same network and/or have no IP of their own.

>  Also, is it possible to route the traffic that is going to be forwarded to another computer (or has been sent from another computer to the internet) through one network card, and the traffic between the internet and the server through a different card? 
That is also possible.

You want to route from one interface to the other (and back), and you want to set the default gateway for the devices that hang off the server to the server's IP, so they will use that as their internet connection.

There's one tiny switch you have to set to make your server actually route traffic, but after that you're all set.

You do have to use separate subnets for these connections, however; for example, if your LAN uses 192.168.**0**.x, you could use 192.168.**1**.x for the second subnet that you connect to the server.

---

### Post by superprash2003 on 2008-12-07
you could use Firestarter for File sharing or use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Mattventura on 2008-12-08
Well, what I meant by "traffic to the internet" is traffic that gets switched to the router, not routed to the router. I want to have two ethernet ports connected to a router, and one is for traffic between the server to the internet and the other is for traffic switched to/from the internet to other nodes on the network. Is there a way to do this, or is routing the only solution?

---

### Post by Iowan on 2008-12-08
Perhaps I'm confused by > ... switched to the router, not routed to the router. You mean traffic coming in through the switch (via router?) as opposed to traffic through modem (via router)?

---

### Post by Dmole on 2009-01-07
this thread seems to have no closure...
not sure but this might be relevant:
[http://ubuntuforums.org/showthread.php?t=402581](http://ubuntuforums.org/showthread.php?t=402581)

---


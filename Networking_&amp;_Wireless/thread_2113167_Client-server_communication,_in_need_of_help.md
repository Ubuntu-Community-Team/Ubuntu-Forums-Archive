---
title: "Client-server communication, in need of help"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by il_maniscalco on 2013-02-06
Sorry for not being completely linux related question, but I didn't know where to ask, if you know a good and friendly community more appropriate, please address me in.

I need to let communicate clients and server in a point-to-point server, according to the following scheme:

[CENTER][IMG]http://i45.tinypic.com/2akgw7l.gif[/IMG][/CENTER]

As you can see, I maintain a complex network where the people who set up the LAN made for various reasons some virtual lan; each lan has got some servers, and now, I have to let communicate those servers through a point to point communication, to a remote lan which I can't manage.

The remote lan guys, will assign me an IP, and the remote clients (which need my servers), have to communicate only through that IP. But my local server belong to other ip ranges (as they are in VLAN). Moreover, the remote clients have to establish a 1-to-1 communication with my servers. So I have to recognize which client makes the request, and forward it to my server according to the IP.

I am quite sure this can be easily accomplished using a router, but which technique shall I use?

Thanks mates :-)

---


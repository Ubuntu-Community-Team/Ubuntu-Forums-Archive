---
title: "Building Mobile Broadband Server/Router Help"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by Arabica Bean on 2011-04-27
Hi all. Let me explain what I am trying to do.

I have an old tower that I've installed Ubuntu onto. It connects fine online with a mobile broadband stick. I also have an old wireless router knocking about, and I've been trying to network up my house wirelessly using the tower as a router, if that makes any sense. Long story short, this is my ideal setup


Internet ==> Mobile Broadband ==> Tower ==> Wireless Router ==> Wireless Devices.

I know that it's complicated, but I'm sure that it can be done. I've tried playing around with bind9, and playing with dhcp and the like. I feel that I am close.... but no cigar.

If anyone has any ideas how to route all traffic from the router, to the MBB stick, then your help would be greatly appreciated.

---

### Post by rosenkavalier on 2011-05-31
[FONT="Comic Sans MS"][COLOR="Blue"]+1, I'll help... [COLOR="White"]questions like this are mostly not getting any replies in this forum[/COLOR]

[s]first, I'm still unclear with your setup, that is broadband stick directly to tower then router? where do you place the ubuntu box? AFAIK, a router must be set up *between* the broadband stick and wireless transmitter (I meant, wireless router with additional antenna mounted on a tower).[/s]

-- edit, I thought the tower was some kind of transmitter

in fact, if we have a wireless router, we would only need iptables for NAT in our ubuntu box, the router will handle dhcp. [this article]("http://newbiedoc.sourceforge.net/networking/homegateway.html") explains how to set up NAT for internet connection sharing. some routers even have usb port for broadband stick, we can use the router with the broadband stick out of the box, without involving any shell commands in a linux box.

good luck :popcorn:[/COLOR][/FONT]

---


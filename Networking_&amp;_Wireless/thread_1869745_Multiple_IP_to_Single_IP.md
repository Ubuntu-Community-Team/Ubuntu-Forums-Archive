---
title: "Multiple IP to Single IP"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by nss11 on 2011-10-26
Hi guys,

My apologies if this is a stupid question, a google search seemed not to provide a good answer but I fear I may be unsure in what to search for if it has one.

**My question:**
Is it possible (is there any software available) which allows for the assigned IP address**es** for one server in a public network to route to just one IP address?

So basically, I want my server at home to have multiple IP addresses so I can provide some ambiguity between some virtual machines on it. My ISP doesn't want/can't provide me with multiple IP addresses themselves, so I was toying with the idea of getting a VPS with multiple IP addresses assigned to it which then all forward to my single home IP which then go to different virtual machines on my home server.

I'm aware of port forwarding, but would this work if I wanted all ports for an IP to go to a virtual machine?

I hope that makes sense. Again, I'm sorry if this seems like a silly question if it is easily done or if I've missed any obvious tutorials on google.

Ta.

---

### Post by nss11 on 2011-10-27
So I think something which does this behaviour would do the job. Does anybody know about any software/hardware?

[IMG]http://img526.imageshack.us/img526/6625/unled1yd.jpg[/IMG]

I'm not sure if this is a straight forward thing. I know that something like this in reverse is done with NAT. 

Cheers

---

### Post by nss11 on 2011-11-01
bump. Any ideas would be greatly appreciated. :)

---

### Post by Grenage on 2011-11-01
Alas not really; port forwarding is about as good as you're going to get, without multiple public addresses.

Seriously, if your ISP can't give you more than one IP, it's time to find a new ISP.  That's very bread and butter stuff.

---


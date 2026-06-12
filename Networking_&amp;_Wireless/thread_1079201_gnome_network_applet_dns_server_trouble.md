---
title: "gnome network applet: dns server trouble"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by edgue on 2009-02-24
Hi there,

I am running kubuntu 8.10 on my Lenovo T61p. I didnt take me long to realize that the knetwormanager was a no go ... so I decided to use the gnome network applet, but i I have a really strange problem with that application too.

[ First of all - my WLAN and ethernet works fine when i am in the office, so this shouldnt be a hardware thing ]

It was easy to define a new configuration for my WLAN at home. BUT: I am not using DHCP there, so I am setting the connection details manually. 

Works fine ... besides this: when i try to add *anything* into the line that says "DNS server" ... the "OK" button of the gnome applet goes gray. 

In other words: I am not able to specify & save a DNS server entry for my private WLAN configuration. 

A coworker told me this workaround: to add the nameservers to 

/etc/resolvconf/resolv.conf.d/tail

and I did so - by adding lines like 

nameserver x.y.z.ip

This button going gray is weired, but it gets stranger ...last week, this tail-workaround worked ... just fine. 

Yesterday evening, my WLAN seemed sooooo damn slow. It took forever to load any websites .... until I started my "AT&T" to connect into my companies intranet. 
And boom ... all of a sudden, speed was OK. 

I assume that there was some problem with the nameservers (or whatever) ... and as soon as I was connected to the company intranet DHCP ... everything turned normal. But I doubt that all 4 nameservers that I added were offline; I fear something "inside" my linux caused this slowdown.

So, this boils down to:
a) what is wrong this dialog window?
b) do I need another workaround?
c) what could explain the terrible slow down for my connection?

any idea is welcome,

regards,
eg

---

### Post by edgue on 2009-02-28
Problem solved.

My DNS server entries were ending with .2 .... and I typed them as I was used with windows: .002 ... which seems to be invalid to the connection editor. 

My connection is still kinda slow on initial connects; but as there were no responses during the last days I assume I wont find help on that ...:confused:

---


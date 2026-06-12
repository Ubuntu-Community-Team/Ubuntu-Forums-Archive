---
title: "Auth against Novell network?"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by thymox on 2010-06-11
Hi all,

I've installed Ubuntu 10.04 onto a nice external USB2 HDD so that when at work I can go from classroom to classroom and take my own working environment with me.  Bliss!

I am working on a nice little script that sets-up the various things I'd need for me depending on the individual machine - essentially a little BASH that reads the eth0 MAC address (since this will be unique to each machine) and set things like the IP address as required (for some reason they don't like DHCP where I work).

Anyho, that's all going rather nicely and is working well.  However...

The College that I work in use Novell for their authentication/mail/etc... and their proxy.  They have a Smoothwall Guardian Server that checks that you've authenticated to the NDS and applies some rules depending on your auth credentials.

All well and good, but without authenticating to the NDS the proxy prevents access to everything.

I have tried this:[code]ncplogin -S <servername> -U <username.context.tree>]/code]and this succeeds... but then when I fire up Firefox it still shows as unauthenticated.

Any thoughts?

Cheers.
Grant.

---

### Post by pricetech on 2010-06-11
I had zero success getting anything Novell to work right with Ubuntu.  That has been a couple of years ago though, so maybe things have gotten better.  Make a trip out to Novell's site and see what they offer.

Good Luck with it.

---


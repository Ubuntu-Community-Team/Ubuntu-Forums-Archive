---
title: "Setting up a proxy.... good advice.."
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by melsen on 2010-03-15
Hey folks,

I was hoping some of you have experience setting up and configuring proxy servers.... 

The primary use is a reverse proxy server that supports caching... it might later be used for internal proxy use as well.. but since I only have 1 public IP, my main focus is setting it up as a reverse proxy.

Currently, I only have an apache based reverse proxy server, but I have been hearing some good things about Squid.. and boy... that just seems crazy to set up... huuuge configuration files. Not sure I can make that work.

So... do any of you know of an .iso image based thing where I can just plug in a CD, boot it up and install, and then perhaps configure through a webbased interface... kind of what we see with things like Proxmox, pfsense, Deep-O-Fix and so on?

Or do any of you know of a really easy setup/howto guide on how to set it up in Ubuntu?

Thanks


/Allan

---

### Post by toosneaky on 2010-03-15
untangle linux seems like the one for you... they do an up to date iso on thier webbie or you can deploy an older version of it on hardy if you want to mod it.
but - the really good features of the iso you have to pay for on a user based license

edit - out of the box as far as i know it uses squid clamav and dansguardian

---

### Post by melsen on 2010-03-16
I'll check it out.. thanks.

---


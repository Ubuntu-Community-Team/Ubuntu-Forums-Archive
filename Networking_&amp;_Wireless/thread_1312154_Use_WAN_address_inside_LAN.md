---
title: "Use WAN address inside LAN?"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by raydowe on 2009-11-02
I imagine this is covered somewhere but I've been searching for hours and can't seem to find an answer. Not sure if missing something, hopefully someone can help.

I recently changed my Windows server to an Ubuntu server. Along with other computers, I use a netbook for web development. I cannot seem to access the server using my Static WAN IP (69.XXX.XXX.XXX) from inside the network. However, everything works as expected when I'm connecting from a remote location.

All the appropriate ports are forwarded, and my ISP is not blocking any ports. I know this because everything worked fine on my Windows Server before the switch. I'm guessing it's something to do with Ubuntu server not liking requests made to a WAN address?

I have considered just sucking it up and using the LAN address, but this would cause obvious problems when I'm taking my netbook in and out of the area.

I've been looking at router loopback, but my router (D-Link 1310) does not seem to support it. I also wonder why this would be necessary as the Windows Server worked fine without it.

---

### Post by efflandt on 2009-11-02
You could install bind9 and learn how to configure your own little nameserver to point the public name for your server at its LAN IP.

But at some point it would be a good idea to test your server from the internet (dial up or mobile data device) from a computer not on your LAN, to make sure that everything is working properly from there (server config, port forwarding, etc.).  Or you could possibly test it using lynx or an ssh X tunneled browser remotely in an outside shell account.

---

### Post by raydowe on 2009-11-02
Thanks for the reply :)

I have tried it from outside and it works fine. Both Apache and SSH work with my WAN address, but only from outside my LAN.

I thought there might be a solution with setting up a DNS, but I don't have a domain name that resolves to my current WAN, just a static IP. Is that still a solution?

---

### Post by Iowan on 2009-11-03
Have you tried connecting via the local (LAN) address?

---

### Post by raydowe on 2009-11-03
Yes

LAN address works while on the network
WAN address works while outside the network

My goal is to be able to use the WAN address regardless of where I am, (switching back and forth would be a massive headache for things like svn, ftp...)

---


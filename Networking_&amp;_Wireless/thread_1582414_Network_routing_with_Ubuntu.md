---
title: "Network routing with Ubuntu"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by Stalker150 on 2010-09-26
Hi there!

I have a task to do but I really don't have an idea how to do it so maybe someone of you can help me out here that would be awesome!

I have to realise a network between two different network groups, routet by a linux server. I made a picture so you'll understand what I mean:

[IMG]http://www.vivi-art.de/network.gif[/IMG]

I'm not allowed to use a router and there's another problem. The server only got one ethernet card with one ethernet port. This means it should look like this:

[IMG]http://www.vivi-art.de/network_connect.gif[/IMG]

The server is connected with the ethernet card (eth0) to a switch which is connected to both network PCs.

Everything I found out so far is that I can assign two IPs to one ethernet card. The card is eth0 under Ubuntu in the media folder and the first IP would be on eth0:1 and the second on eth0:2.

These two needs to be connected (or bridged - I don't know) together and a NAT needs to be set. Is it possible with Ubuntu or the Ubuntu Server Edition?

Please, can someone show me **exactly** what I have to do to set this up? 
Or maybe someone can type a list with all the commands I have to type into the shell of a fresh installed system?

stalker

---

### Post by Iowan on 2010-09-26
Perhaps a few more details so the task looks less like a homework assignment... ;)
I'll need to try to find some details - I vaguely remember seeing aliases set up in */etc/network/interfaces*, but don't remember if/how it can be done via Network Manager.

---

### Post by Stalker150 on 2010-09-27
> **Iowan said:**
> Perhaps a few more details so the task looks less like a homework assignment... ;)


It is a homework but I canceled it. I'll do it now with two ethernet cards in the server pc so I don't have to bother you anymore. And I can find more information how to do it with two ethernet cards without aksing you.

Thanks for the response. :)

**Thread can be closed now.**

---

### Post by Iowan on 2010-09-27
> **Stalker150 said:**
> 
**Thread can be closed now.**
Done!

---


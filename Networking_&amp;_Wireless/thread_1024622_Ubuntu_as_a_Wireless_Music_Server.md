---
title: "Ubuntu as a Wireless Music Server"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by perrti-y02 on 2008-12-29
I am trying to set up a Music server on this Ubuntu machine. I have got mpd up and running and can connect on the local machine. (I haven't got my new motherboard yet so I haven't tried connecting from a different machine by any method)

Ultimately what I am trying to do is have a central server which wirelessly transmits the music feed to a number of machines around the house.

The part I need help with is establishing the server as a wireless network of it's own.

Any ideas?

I fear little of that actually makes sense

---

### Post by perrti-y02 on 2008-12-29
Anyone?

---

### Post by khaliraja on 2008-12-29
Im trying to do something similar, though I'm fairly new at it and not getting very far due to how complex it has become for me.  Try this though : [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver).  good luck!

---

### Post by Maddman on 2008-12-29
What are you really looking for?  These machines around the house, what are they going to be playing music with?  Are they more ubuntu PCs, or windows/macs?  Do you simply want to access they files from other computers?

The easiest way to do this is to set up a Samba server.  Samba is a Linux server that pretends to be a Windows server.  So to set up a music server, you set up the music as a Samba share, map/mount your other PCs to that share, and play the music files.

Here's the official SAMBA How-To
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

As for it being wireless, it really doesn't matter.  Setting up a wired vs. wireless server is the same process - as long as you have a network connection, Samba doesn't care if its ethernet or wireless.  Best would probably be to have the server wired to the router because its faster, but it should work either way.

---

### Post by perrti-y02 on 2008-12-29
These machines are little boxes running a really simple version of Ubuntu. All they will be doing is playing music. Nothing else.

The issue i have is with wirelessly networking, to start with, one machine with my server box. How do i create this wireless network on my server? I can only join current networks and cannot work out what i am looking for on google.

---

### Post by Maddman on 2008-12-30
> **perrti-y02 said:**
> These machines are little boxes running a really simple version of Ubuntu. All they will be doing is playing music. Nothing else.

The issue i have is with wirelessly networking, to start with, one machine with my server box. How do i create this wireless network on my server? I can only join current networks and cannot work out what i am looking for on google.

Okay.  Are you using a router?  If so, then you want to create a network with your router and have all the computers join that.  Then mount the music folder on the server on all the other PCs.

If you just have a wireless adapter on each PC and don't want to get to the outside world, then you're wanting an ad-hoc network.  Not sure how to do that, but it might give you something to google :)

hth

---

### Post by perrti-y02 on 2008-12-30
Is it possible to do it without using a router? Could I not setup the server as a router or am I missing something fundamental about how a router works?

---

### Post by perrti-y02 on 2008-12-30
Ignore that. I will just buy a little router. What kind of thing am I looking for? This network doesn't need to connect to the real world but the server does by a totally separate network interface. Does this create complications?

---


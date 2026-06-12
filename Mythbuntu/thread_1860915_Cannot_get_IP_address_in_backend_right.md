---
title: "Cannot get IP address in backend right"
date: 2011-10-15
forum: Mythbuntu
---

### Post by chipppy on 2011-10-15
Good Evening

I am trying to setup IP address in backend but I keep getting the 'unable to connect to Master Backend server error'
This error means that the IP address is wrong.

My setup is a little different from standard so i explain incase that part of the problem

It is a 8TB RAID5 system built using Xubutntu 10.10 Alt-install CD.  yes thats right 8000GB).  I then installed mythtv from the software centre.  This is single Front/Backend machine, with no network connection.  I plan to connect to network and make it master backend once I get the bugs sorted.

right after initial install I got the error, due to Master Backend IP being 10.0.0.1.  changed to 127.0.0.1 and FrontEnd connects to Backend.

reading through MythTV wiki this address is bad if usinf remote Frontends and a few different IP suggested.  I tried them all and I get the 'unable to connect to Master Backend server error' again.  i tried 192.168.0.1, 192.168.0.100, 192.168.0.200, and a few others.

I dont know much about networks.
what am I doing wrong?

How do i setup the various IP address and where to get this setup for remote front front ends, and I suppose remote back ends (justin case i ever run out of room   lol)

Cheers
chipppy

---

### Post by williammanda on 2011-10-15
I can't give you every detail but you first need to find out what the ip address is for the mythtv computer. In gnome there is a network icon in the upper right of the screen that will give all the network details. Find the xbuntu cousin for the network program and start there.

---

### Post by thatguruguy on 2011-10-15
> **chipppy said:**
> Good Evening

I am trying to setup IP address in backend but I keep getting the 'unable to connect to Master Backend server error'
This error means that the IP address is wrong.

My setup is a little different from standard so i explain incase that part of the problem

It is a 8TB RAID5 system built using Xubutntu 10.10 Alt-install CD.  yes thats right 8000GB).  I then installed mythtv from the software centre.  This is single Front/Backend machine, with no network connection.  I plan to connect to network and make it master backend once I get the bugs sorted.

right after initial install I got the error, due to Master Backend IP being 10.0.0.1.  changed to 127.0.0.1 and FrontEnd connects to Backend.

reading through MythTV wiki this address is bad if usinf remote Frontends and a few different IP suggested.  I tried them all and I get the 'unable to connect to Master Backend server error' again.  i tried 192.168.0.1, 192.168.0.100, 192.168.0.200, and a few others.

I dont know much about networks.
what am I doing wrong?

How do i setup the various IP address and where to get this setup for remote front front ends, and I suppose remote back ends (justin case i ever run out of room   lol)

Cheers
chipppy

According to your post, you have no network connection.  That means that the only connection you have available on that machine right now is 127.0.0.1, which is localhost (the machine you're on).

That will change when you hook up your computer to a network, whether it's wired or wireless.  Once your computer is hooked up to a network, come back here and someone (maybe me!) will walk you through setting up your back-end to correctly identify your ip address on the network.

---

### Post by chipppy on 2011-10-16
Good Evening

DOH!.  That now makes sense after reading your post and a little bit more.  I will sort the other problems and get back to this post.

Cheers
chipppy

---


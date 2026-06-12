---
title: "Wirelessly sharing a mobile broadband connection"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by apkent on 2009-05-14
Hi,

I'm Andy, new to the forums, and even newer to Linux & Ubuntu.

What I'd like to do is run Ubuntu headless as a server, with my mobile broadband dongle permanently connected. I haven't actually got the distro up and running yet (or even bought the hardware!) but want to make sure it'll work before I spend any money!!!

The idea is that my server will share the internet wirelessly via a wireless adapter on the mobo around the house, basically acting as a wireless router (except that I will also use the server for storing/serving media etc.)

Is this possible, and is it easy to set up?

I did a search but couldn't find anything, so hope its an easy one!

Cheers,
Andy

---

### Post by apkent on 2009-05-14
Anyone?

---

### Post by superprash2003 on 2009-05-14
you want to share it with only one pc wirelessly or more than 1?

---

### Post by apkent on 2009-05-14
Ideally I would share with more than one, but if I have to use it only on my Vista laptop to start with that would be ok....

---

### Post by apkent on 2009-05-14
Looking into this further, should I be looking at iptables to try and route the connection properly?

---

### Post by superprash2003 on 2009-05-14
well if its with only machine its fine.. to make things simple, you could firestarter to share internet connection, and you would need to create an AD HOC network present in ubuntu's network manager ( 8.10 and above ).

---

### Post by apkent on 2009-07-22
Magic. Got it working eventually :)

I left the router settings at default, set up a static IP on the laptop and boom, all good.

Now I'm having a little trouble port-forwarding as I've effectively got 2 firewalls to go through, first firestarter on the server and then the router itself......

---


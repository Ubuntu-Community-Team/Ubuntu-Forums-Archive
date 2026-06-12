---
title: "Internet won't connect"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by dymonik on 2011-01-11
I am running Ubuntu server 10.10 ( i think )
i set it up as a LAMP.. apache mysql and php 5
 
My problem is, when i first set ubuntu up i set it up as dhcp internet and everything worked fine.
 
Now i just upgraded my internet service because my last connection was only 4 mbps.
 
And now i have a static ip. I bought a router, configured the router, and my windows 7 pc works like a charm, but i have no earthly idea how to re-setup the ubuntu server with a new internet connection, the only thing i did notice is the preferred DNS and alternate DNS were loaded onto ubuntu.
 
ifcongif | grep inet shows
 
inet6 addr: fe80: :22cf: 30ff........ scope:Link
inet addr:127.0.0.1 mask 255.0.0.0
inet6 addr: : :1/128 Scope:Host
 
really have no clue what i need to do
 
using linksys E2000 router, i kinda figured it to work like windows, plug in the computer to the router and it be connected... but yah, it can't be that easy

---

### Post by PatchesTheCaveman on 2011-01-12
If you have a router, you should only configure the static IP on the router, and let the Windows and Ubuntu machines continue to get an automatic address, which will be assigned by the router.  If you configured the static IP on the Windows box, that's probably gumming up the works.

---


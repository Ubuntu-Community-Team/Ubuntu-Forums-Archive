---
title: "Wired Networking Between Ubuntu and Vista"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Subtle_Demise on 2010-05-29
So my wireless card no longer works in my windows machine for some odd reason, probably due to the temporary video card I have until my actual one comes back from XFX. It works perfectly in the Ubuntu box though, so I bought a crossover cable hoping to have it automatically create a wired network that I can bridge to my router. Obviously it's not that simple. 

Anyway, I have the computers connected through crossover cable and they sort of know there's supposed to be some form of networking going on (Windows has limited connectivity on "unkown network" while Ubuntu just won't connect to Auto eth0), but that's as far as I get. basically all I need is to:

1. Get the computers to connect to and communicate with each other.

2. Bridge the wired connection with the wireless one within Ubuntu so that the Windows computer can access the Internet as well as the shared files on the other computers in the wireless network.

And no, I do not want to buy another wireless adapter. Thanks in advance. 

I'm running 10.04 Lucid with Gnome desktop, if it makes a difference.

---

### Post by Subtle_Demise on 2010-05-30
Managed to get the two computers to see each other so that they can ping and arp successfully. I've even turned on ipv4 forwarding through sysctl. Still no luck in getting Windows to connect beyond Local Only.

---

### Post by ub-newbie on 2010-06-05
Don't have an answer, just some things you might look into.
Is "Internet Connection Sharing" turned on?
Have you installed "Bridge_utils"?

---


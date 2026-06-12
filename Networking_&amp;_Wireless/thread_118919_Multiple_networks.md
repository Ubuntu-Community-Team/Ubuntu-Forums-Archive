---
title: "Multiple networks?"
date: 2006-01-18
forum: Networking &amp; Wireless
---

### Post by jd_k on 2006-01-18
I'm currently connected to a wireless network at my house. The other computers are all running XP; the wireless router connects me to the DSL modem. Pretty standard setup.

What I would like to do is set up another network between my computer and another linux computer. The network would be a cable network, running through another router that I have. The other computer doesn't need to access the internet.

I know this is confusing without a diagram. Call my computer 1A and the other computers in my house are 2, 3, and 4; call the non-internet computer that I want to connect to on a wired basis B. The idea is that the numbered computers can only see each other, and all have internet access. The lettered computers can only see each other, and don't have internet access. My computer is the best of both worlds.

How would I set this sort of a network up? Or is it even doable?

---

### Post by cwaldbieser on 2006-01-18
[QUOTE=jd_k]I'm currently connected to a wireless network at my house. The other computers are all running XP; the wireless router connects me to the DSL modem. Pretty standard setup.

What I would like to do is set up another network between my computer and another linux computer. The network would be a cable network, running through another router that I have. The other computer doesn't need to access the internet.

I know this is confusing without a diagram. Call my computer 1A and the other computers in my house are 2, 3, and 4; call the non-internet computer that I want to connect to on a wired basis B. The idea is that the numbered computers can only see each other, and all have internet access. The lettered computers can only see each other, and don't have internet access. My computer is the best of both worlds.

How would I set this sort of a network up? Or is it even doable?[/QUOTE]
Yes.  Just connect your "Letter" computers to a router via ethernet cable.  Their default route should be the router.  Let them get IPs via DHCP, or assign static IPs on the same network.

Your PC just needs an extra route to reach that network.

---

### Post by darth_vector on 2006-01-18
or you could put two network interfaces on 1A. you could then set up two subnets:

192.168.1.0/29 and put A1(interface 1) and B on this
192.168.1.8/29 and put A1(interface 2), 2, 3, 4 on this

This way if you decided to connect B to the internet you could do it with minimal bother.

---

### Post by jd_k on 2006-01-19
Thanks. I'll give it a try.

---

### Post by jd_k on 2006-02-04
Sorry to drag this up again. Finals came and went, and I had to put off the project for a bit.

I'm back at it now, though, and I'm having a little trouble. I have my laptop (my main computer) connected to the rest of the computers in my house via my wireless network, which then connects to the internet. I also have it connected via ethernet cable to a router in my room, to which my second linux computer (desktop) is also connected. The wireless router assigns 192.168.1.2-5 to the computers on that network. The wired router assigns 192.168.0.2-3 to my laptop and my desktop, respectively. I can ssh into my desktop; I can connect to the wireless shares and the internet.

In the terms I used earlier: 1A can communicate with B just fine. 1A can communicate with 2, 3, and 4 just fine. The former are wired together. The latter are on a wireless network, with internet.

The only problem: I can't do them both at the same time. As long as I have my ethernet device active (eth0) I cannot connect to the internet (wireless network, via device ath0). How do I resolve this?

Apologies if my question is dense...

---

### Post by hajk on 2006-02-04
Why do you need a router to connect 1A with B? Why not make it a dedicated connection, Ethernet cable straight between them? Assign static 192.168.1.1 to 1A and static 192.168.1.2 to B. The routing table on 1A should look something like this:

192.168.0.0        *                wlan0
default           wireless-router  wlan0
192.168.1.2     192.168.1.1      eth0

(the last line is added), and on B

192.168.1.1     192.168.1.2     eth0

All of this with entries in /etc/network/interfaces to match. Important is that you have only one default route on 1A. Right now you say that you cannot use your two interfaces simultaneously -- probably because in each case a different default route is set...

Just my €0.018 worth...

---

### Post by jd_k on 2006-02-04
I like the idea of getting rid of the router and just using a single ethernet cable. I appreciate your explaining how to do it, but I'm not exactly tracking with you. What files do I need to edit in order to set that up? And regardless of whether I use a router or not, how do I ensure that I have only one default?

You'll have to forgive my ignorance regarding these things... ::embarrassed::

---

### Post by Ocxic on 2006-02-04
would it be possible to setup something like this, for what your proposing.
this guide shows you how to setup you compupter to use 2 internet connections at the same time. possibly even automatically not using the disconnected one.

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

edit: missiterpreted your post sorry guys

---

### Post by hajk on 2006-02-04
Setting a point-to-point connection:

1. Connect the two computers with Ethernet cable, without going through a router.
2. On computer A: "sudo gedit /etc/networking/interfaces" and make sure that    your wireless interface (I call it wlan0) comes up automatically at boot by the line "auto wlan0". Then edit the eth0 lines to read:

     iface eth0 inet static
          address 192.168.1.1
          netmask 255.255.255.0
          pointopoint 192.168.1.2
     auto eth0

3. On computer B do the same for eth0, but with the addresses reversed.
4. On both computers (assuming wireless is up on 1A) do "sudo ifup eth0".
Check with "sudo route" whether the point-to-point connection is indeed up, you should be able to ping one from the other.

Check with "man interfaces" and "man route" for further finetuning this, if needed.

---


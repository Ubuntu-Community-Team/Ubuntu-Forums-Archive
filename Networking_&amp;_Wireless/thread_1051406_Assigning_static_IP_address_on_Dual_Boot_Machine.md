---
title: "Assigning static IP address on Dual Boot Machine"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by qprfact on 2009-01-26
Hi, I'll try and give as much detail as possible - I'm sure the answer will prove to be really obvious!

OK, my son has a Dell dual boot PC, Win XP and Ubuntu. It connects to the network using an Acer Homeplug.

Also on the network are three other laptops (one running Vista and two Acer Aspires running Linpus), and this machine, a Mac. These all connect wirelessly to my Belkin ADSL router.

I have decided I want all machines to have static IP addresses, and then turn off the DHCP server.

This has worked with all but my son's PC.

I have edited /etc/network/interfaces to show the new connection, changing the eth0 entry to refer to static rather than dhcp. This MAY be my first issue, at least according to this article - [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) - should I have not done this and left it to Network Manager?

However, I also read that there is an issue with dual boot machines in that Win "hangs on" to the connection, particularly with NVIDIA cards (which I have a feeling the Dell has)

I have tried /etc/init.d/networking restart many times, but after doing so I still can't ping anything, not even the router. 

Should I be making the changes in System -> Administration -> Networking and then just referring to the connection in Network Manager?

Seeing other posts about issues with NM, should I be using it at all?

Hope someone can help.

I just noticed the thing about System -> Administration -> Networking, and as my son is now in bed, I can't try that one out tonight!!!

---

### Post by Iowan on 2009-01-26
If it's Intrepid, Network Manager may also cause problems with static addresses. [Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a How-To for setting up static address via NM, and [here]("http://ubuntuforums.org/showthread.php?p=6623406#post6623406") is a proposal to remove NM and re-install the old manager.

---


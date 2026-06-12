---
title: "Internet Sharing Through A Windows Box"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by lan_rogers_book on 2009-08-15
First post, yay!

I recently installed Ubuntu and now I'm trying to share a internet connection from a windows box (which is receiving internet from a wireless network) via a CAT5 cable. I pushed a few buttons but haven't made any major changes yet. So... how would I go about sharing said connection?

---

### Post by spd106 on 2009-08-16
First, if you're not using a switch then you will probably need to use a cross-over Ethernet cable.

Once you have the hardware setup then Ubuntu should automatically detect the network settings via DHCP from the Windows box. If it doesn't work then open System -> Preferences -> Network Connections and try editing eth0 by manually setting the IP address to one in the 192.168.0.x range with at subnet mask of 255.255.255.0 and gateway of 192.168.0.1, as these are the defaults that Windows use.

You should now be able to ping the windows box.

---

### Post by rshrc1 on 2009-08-16
I made a post about this before although I have a feeling it won't get any replies... Could anyone post information about how to setup the connection? I can't speak for the other user, but personally I'm using Vista on the computer connected to the internet. Thanks.

---

### Post by Bachstelze on 2009-08-16
To activate the Internet Connection Sharing, go to the Control Panel > Network and sarng center > Change adapter settings. Then right-click on your Internet connection, go to the Sharing tab, and tick the "Allow other network users to connect..." box.

---

### Post by lan_rogers_book on 2009-08-16
Thanks for the replies spd106 and HymnToLife, My only question is this: what is the difference between a cross-over cable and a CAT5 Ethernet cable? I have a "CAT5 Patch Cable. UTP" is this enough to get the job done or do I need something more?  

> **spd106 said:**
> First, if you're not using a switch then you will probably need to use a cross-over Ethernet cable.

---

### Post by lan_rogers_book on 2009-08-16
I did a little reading and it seems I have the correct hardware, my problem is that my Ethernet adapter claims a cable is unplugged, I remember running into a similar problem like this a long time ago and it was a relatively simple fix...

---

### Post by rshrc1 on 2009-08-17
Me too. It just says no cable is connected on both computers.

---

### Post by lan_rogers_book on 2009-09-13
Solved. Turns out that it was my cable, I was just in denial. I borrowed a wired router and hooked it all up, worked like a charm.

---


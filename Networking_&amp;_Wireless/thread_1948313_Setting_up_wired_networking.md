---
title: "Setting up wired networking"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by squelchy451 on 2012-03-28
Hi. I installed Xubuntu on a AMD E350 ITX board.

The eth0 is showing up but it's not recognizing the wired network. I'm trying to set it up by entering the DNS, IP addresses, and these numbers and codes that I have no idea what they mean.

I'd appreciate some help.

Thank you!

---

### Post by farrinux on 2012-03-28
> **squelchy451 said:**
> Hi. I installed Xubuntu on a AMD E350 ITX board.

The eth0 is showing up but it's not recognizing the wired network. I'm trying to set it up by entering the DNS, IP addresses, and these numbers and codes that I have no idea what they mean.

I'd appreciate some help.

Thank you!

squelchy:
I think you are going to have to be more specific about the problem.  What codes what are their lalbels etc.  But for now look at this [https://help.ubuntu.com/10.04/internet/C/connecting-wired.html](https://help.ubuntu.com/10.04/internet/C/connecting-wired.html)

---

### Post by Paqman on 2012-03-28
If your router is doing DHCP then everything should be all sorted for you. Can you connect another device to your router and does it set up ok?

---

### Post by Gone fishing on 2012-03-28
Your network probably uses DHCP, i.e. a network server, router or similar assigns IP address to the computers etc. I would right click the network icon and select edit connections. Then go to Wired and edit, select Ipv4 Settings and in Method select Automatic (DHCP), probably best also click &#8220;Available to all users&#8221; then click save.

This should now connect to the network, just to check reboot login open a terminal and run the following command ```
sudo ifconfig
``` you should then see the eth0 and the IP address it has been given.

If this doesn&#8217;t work post back

---

### Post by mörgæs on 2012-03-28
Moved to the network forum.

---


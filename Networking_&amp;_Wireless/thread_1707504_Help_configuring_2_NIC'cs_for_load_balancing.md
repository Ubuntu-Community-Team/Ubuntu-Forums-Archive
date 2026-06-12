---
title: "Help configuring 2 NIC'cs for load balancing"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by varunsworld2000 on 2011-03-15
Hi,

New to this forum as well as the world of Ubuntu.

I need help configuring my NIC's. I am using Ubuntu 10.10 Server Edition with three Nic's. Two NIC's(Two ISP connections) would be for WAN and one for the LAN. The two WAN NIC'S can/cannot be on DHCP and the LAN needs to be on static. How do i go about setting up. I read about network bonding but need more clarity.

Any help would be appreciated, Thanks in advance.

Regards,
Varun

---

### Post by Kirboosy on 2011-03-15
Hi! Welcome to the forums!

I personally have never setup a multi-NIC server so I can't help all that much, but [this thread]("http://ubuntuforums.org/showthread.php?t=501221") might be of some help. :)


~Caboose

---

### Post by varunsworld2000 on 2011-03-15
Thanx Caboose for the help it doesnt help with my setup though. I do appreciate ur help :-)

---

### Post by Kirboosy on 2011-03-15
A good starting place for Ubuntu in general is [here]("https://help.ubuntu.com/community")

For networking [this page]("https://help.ubuntu.com/community/NetworkDevices") and [this page]("https://help.ubuntu.com/community/InternetAndNetworking") are useful

---

### Post by varunsworld2000 on 2011-03-16
Thnx for the links Caboose. Going through them. Hopefully will find a solution.

nyways this is how my network look likes.


[[IMG]http://dc244.4shared.com/img/QI43vEAD/0.5120739751290794/My_Network.png[/IMG]](http://www.4shared.com/photo/QI43vEAD/My_Network.html)

---

### Post by rokabear on 2011-04-21
Can you provide a description of what your are trying to do?  I do not think you need nic bonding.

Are ISP1 and ISP2 the same ISP and connection?

Do you want some traffic to go to ISP 1 and some to go to ISP2?  

It sounds like you have two ISPs and when one connection gets filled up you want to be able to use the other.  Is that correct?

---


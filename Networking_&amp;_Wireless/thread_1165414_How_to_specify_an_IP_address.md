---
title: "How to specify an IP address?"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by ajm4481 on 2009-05-20
I would like to put ubuntu on a computer here at work to see if it will improve the stability of the machine. The only problem is htat the machine has to have a specific IP address. So i am wondering how to go about specifying an IP address for a machine using Ubuntu 9.04?
 
Any help would be greatly appreciated. 
 
I am fairly new at using Ubuntu as I just installed it on my laptop a few days ago, and I must say I LOVE IT! But please, remember I am fairly new and need things explained kind of simply.
 
Thanks
Adam

---

### Post by Iowan on 2009-05-20
Jaunty seems to be pretty straightforward for static address setup. Under System>Preferences>Network Connections is an option to Add. You will need to manually add the MAC address. Under the IPv4 tab is an option for Manual - under which you can enter address|netmask|gateway.

---

### Post by stefangr1 on 2009-05-20
I understand you want to install Ubuntu on a computer that is already present in the network at your work, but now running windows?

Since the MAC address is hardware based, the dhcp server at your work will most likely give the same ip-address to your computer when it runs Ubuntu.

---


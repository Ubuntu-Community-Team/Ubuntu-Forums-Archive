---
title: "wireless card"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by SpikeyMike on 2009-04-04
I have ubuntu working via wired ethernet but want to use wireless, if i look in system > administration > hardware drivers it says that proprietary drivers are installed for the atheros 802.11 wireless lan cards, I am using wicd instead of network manager. when I go to the network settings it says that no wireless networks are found, and if I look in preferences there is nothing filled in for wireless interface, in wired interface it says eth0. How can I get it to work?

Spikey

---

### Post by Bucky Ball on 2009-04-04
Is the wireless light on? Try going to System->Administration->Network, unlock and goto wireless properties. Have you filled in the details for your network in there or anywhere else?

---

### Post by SpikeyMike on 2009-04-05
> **Bucky Ball said:**
> Is the wireless light on? Try going to System->Administration->Network, unlock and goto wireless properties. Have you filled in the details for your network in there or anywhere else?

thanks for your reply, i got it working by disabling the default atheros proprietary drivers in system > administration > hardware drivers and then running the following command in a terminal which then added a second choice for atheros drivers to hardware drivers,  when I enabled this it worked

sudo apt-get install linux-backports-modules-intrepid-generic

Spikey

---

### Post by Bucky Ball on 2009-04-06
Excellent news. Hope that helps someone else also. :)

---


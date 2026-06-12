---
title: "Problems having Linksys WUSB11V2.6 adapter to join the network..."
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by nkannan on 2009-01-10
I have an old hp6835 Pavilion desktop system that I have installed Ubuntu 8.10 release. I have a Linksys WUSB11 V2.6 adapter that gets recognized and sees the wireless access point that I have. However it is not joining the network and not getting a DHCP address and fails.

I have made sure that the wireless connection it sees has automatic DHCP enabled but I am wondering if I filled out all the necessary fields properly in the Network Manager setup.

My network is mainly a Windows network and they are all working fine. Was wondering in addition to selecting Infrastructure Mode I need to fill the MAC address and BCCID addresses also?

I am a newbie to Ubuntu and any help appreciated. 

Regards
Nari

---

### Post by sp0nge on 2009-01-10
Confirm your router is set to DHCP, as well as the other settings like channel, mode, encryption type and so forth. Once you're sure you're not overlooking an i that wasn't dotted or a t that wasn't crossed, perhaps consider assigning a static IP to that machine and see if you can connect that way. 

The MAC and BCCID shouldn't be an issue unless you're filtering at the router- which is never a bad idea IMHO.

---

### Post by Hawkman on 2009-01-17
sp0nge, do you mean assign a static IP to the router or the ubuntu box?

---


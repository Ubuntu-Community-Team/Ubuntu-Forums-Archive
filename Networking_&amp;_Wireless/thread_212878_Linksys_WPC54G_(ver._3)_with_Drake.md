---
title: "Linksys WPC54G (ver. 3) with Drake"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by lsyn on 2006-07-10
I am trying to get the PCMCIA wireless card (Linksys WPC54G v.3) in my laptop to work.  Currently, I have Kubuntu 6.06 (dapper drake) as my o/s.  Here is the situation:

I installed Kubuntu in text mode, and the wireless card was detected as eth1.  It asked for the SSID and passphrase for my secure network (which works fine in Windows - my system is dual boot), but the installer reported a setup failure.  It did not say if it was hardware or DHCP problems, but I am confident that the SSID and passphrase were correct.  I chose not to configure the network at that time, so now I am stuck trying to configure it with the Kubuntu GUI.

The Ubuntu wiki does not have specific data for this card, but it indicates that usually an ndswrapper is required for the other versions to even get detection to occur.  So...

My question is:  Since the card has been detected automatically, do I really need to go through the wrapper routine?  Or is anyone aware of another way?  

Thanks!
DJ

---

### Post by lsyn on 2006-07-14
Since no one has replied, I'll add this for completeness.

YES, there is a way around ndiswrapper.  It involves downloading some new drivers and basically following

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

DJ

---


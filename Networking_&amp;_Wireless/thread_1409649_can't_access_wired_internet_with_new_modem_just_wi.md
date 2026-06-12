---
title: "can't access wired internet with new modem just wireless"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Brian_Newbie on 2010-02-17
My cable company came by with a new modem, one that my new internet phone plugs into, as well as my computers. I have 3 computers but don't share an internet connection between them. I simply plug the ethernet cable into the computer I'm using at any given time.

The cable guy reset my IP address on my iMac desktop and it connects to the internet just fine.
My System 76 Linux laptop also connects to the internet just fine but strangely uses the Mac address of my old modem the cable guy took with him. Also the system 76 laptop is using my old IP address that was associated with the old modem and not the new one.

The computer that I can no longer get connected to the internet through the wired ethernet cable is my Acer Aspire 4315 laptop. This computer will connect to any unsecured wireless network, the one I'm using right now - it just won't connect via the ethernet cable any more.

The Acer aspire is set up to automatically connect via DHCP but for some reason it doesn't detect the new modem's IP, Mac address, etc.  

How can I get wired internet to work on this computer?

---

### Post by Iowan on 2010-02-17
So... the two machines that work wired use static addresses? Some modems "lock onto" the MAC address of a connected machine and must be reset to use another. Since you have two other machines that work, this may not be the problem. 
You might configure the laptop to use the same IP address as what is in the iMac... Something doesn't seem quite right - but first, make it work...

---

### Post by Brian_Newbie on 2010-02-18
Thanks Iowan. I had never even thought of resetting the modem with my computers connected to it. When I reset it for my Acer 4315, network manager instantly connected it to the internet. 

I cannot say for certain if the modem locked onto the Mac address of my iMac desktop before it had to be reset to connect my acer computer to the internet, since the System 76 computer has always been able to connect to my old and new modems without any resets being required. Whatever the case, your suggestion solved the issue. I now have 3 IP addresses for each of my 3 computers and they all used the automatic DHCP method to successfully connect to the web.

Thanks again

Brian

---


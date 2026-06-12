---
title: "Networking problem with Linksys router"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by guumby on 2006-06-05
I'm a beginner with linux and am quite stuck ](*,) with trying to figure out a network problem I am having.

I have a clean Dapper install where everything seems to work except the network.  My computer is a duel boot XP / Linux, and I have multiple XP machines on my home network with a mixed wired/wireless Linksys WRT54G router.  The Dapper machine is wired with an nvidia Ethernet controller (Asus A8N-E motherboard).

I'm pretty sure the ethernet is working because in Linux I can see the other XP machines on my network, connect to a networked hard drive, and access the Linksys web interface.  What I cannot do I ping or connect to the outside on the machine (I can with the XP boot).  I have tried DHCP and assigning an IP address, as well as installing nForce4 linux specific drivers, to no avail.

I would appreciate any and all help to figure this out.  Thanks.

---

### Post by beameup on 2006-06-05
Lets get started with a couple of questions.

How many IP addresses are you letting the router assign? Check if there is enough to cover this machine.

Do you have a firewall running? Could try turning it off.

And one more. How is the network card on the Linux box configured right now?

---

### Post by guumby on 2006-06-05
I have the router set to assign 8 ip addresses (currently 4 are being used, including the dapper pc).
The firewall was running, turning it off and doing '/etc/init.d/networking restart' does not change anything.
under networking: the network card is configured for dhcp as eth0, is active, and is getting an ip address from the router (although the router does not show my hostname like it does with xp boxes).  lspci tells me: Bridge: nVidia Corporation CK804 Ethernet Controller.  Based upon other posts I read I disabled the IPv6 incase there was any interference (no change). Not sure what else to check.  

Even weirder - I tried pings:

I am able to succesfully ping my gateway ip, and my primary and secondary dns servers.  Infact, I am able to succesfully ping any ip address (ie. 72.14.207.99 for google.com and 82.211.81.166 for ubuntu.com). However I am unable to resolve hostnames either via firefox or the command line - really strange. So still no web browsing or apt updates.

Thanks for the relpy, will keep trying to figure it out.

---

### Post by beameup on 2006-06-06
Any DNS servers listed in your eth card config? If not add them manually. You can get them from the router info page. I have a linksys Wrt54G and I have the nvidia chipset on this machine.

---


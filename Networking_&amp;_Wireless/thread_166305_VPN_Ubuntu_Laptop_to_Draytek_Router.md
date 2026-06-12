---
title: "VPN: Ubuntu Laptop to Draytek Router"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by bucky on 2006-04-26
Hi,

I'm fairly new to Ubuntu and so for I'm getting most stuff I want working.  However, I have a requirement to connect to a number of remote networks on a regular basis in order to manage client servers.  Most of these clients are using Draytek Vigor 2600 and 2800's.

Has anyone had experience trying to connect to these or similar routers and do they have any advice on what VPN software to use and where I might find some pointers on getting it going?

Cheers

Si

---

### Post by mips on 2006-04-26
First you need to know how the Draytek VPN is configured as it supports many different ways of setting up a VPN.

[http://www.draytek.co.uk/products/about_vpn.html](http://www.draytek.co.uk/products/about_vpn.html)

Stuff like protocol, authentication & encryption are important.

---

### Post by bucky on 2006-04-26
Thanks. I've got a pretty good idea of what the Draytek can do but no idea where to start looking on the Linux side.  I've been using the Draytek's to connect to XP machines, other Draytek's and a Sonicwall so I'm good with that.  I just need some pointers on the Linux side.

---

### Post by mips on 2006-04-26
I was going to recommend something like openvpn but that uses SSL which the draytek does not support.

I dont know what type of protocols/Authentication/Encryption you use so I can't really recommend anything.

Maybe something like ppptp etc will work for you. Or search the Howto section for "VPN" and look in the wiki.

---

### Post by roland67 on 2006-06-12
Hi,

Did you manage to get this working in the end? I have exactly the same situation and set of questions.

Thanks, Roland

---

### Post by bucky on 2006-06-13
I must admit I've been doing a big rollout for a customer so I've not even thought about this for a while.  I'll be looking in the near future though. I'll post up here my findings.

---

### Post by charlie1 on 2006-07-13
Configuring a VPN is not to difficult if you understand how a VPN works and can be configured. Knowledge of TCP/IP would be very advantageous.

> [http://www.draytek.co.uk/products/about_vpn.html](http://www.draytek.co.uk/products/about_vpn.html)

>> Has anyone had experience trying to connect to these or similar routers and do they have any advice on what VPN software to use and where I might find some pointers on getting it going?

You don't need any software to configure the routers. Draytek explains it well: [http://www.draytek.co.uk/support/vpn_setup.html](http://www.draytek.co.uk/support/vpn_setup.html)
 
Plan your VPN and create a logical diagram (network addressing, WAN encapsulation protocols etc), if you haven't already and you should be able to setup the VPN.

Good luck

---


---
title: "Mac address with dual boot  issue?"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Cue2 on 2010-05-05
I have a motherboard with 3 onboard connections.

Ralink Wireless N
Marvell GB Ethernet
Realtek GB Ethernet

I've been able to setup my wireless N perfectly and my two Ethernet ports work. However there is a bit of an issue with the Ethernet ports regarding MAC addresses.

You see in windows vista I manually changed the mac address of the Marvell controller. lets call this mac address 1A and we changed it to 1B. So now

Marvell GB Ethernet
Mac address 1B

Realtek GB Ethernet
Mac address 2

I connect my ethernet to the Marvell port. 

boot into windows the Mac address of the connected port is Mac address 1B

However when I boot into Ubuntu the connected port (eth1) has mac address 1A. I thought, fine, I need to change eth1 in linux to mac address 1B. However, the really odd thing is that the second unconnected port eth2 has the mac address set to 1B already.

Why? does the mac address set in windows carry itself forward to linux? if so, why does it swap to the Realtek interface instead?

Now this wouldn't really be a problem but this is confusing, add the fact that I use dhcp address reservation and WOL and things get a little more confusing.

Can anybody explain this behaviour?

---


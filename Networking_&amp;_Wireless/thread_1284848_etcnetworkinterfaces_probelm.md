---
title: "/etc/network/interfaces probelm"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by josephmcnelis on 2009-10-07
Hey All,

Im currently trying to configure my ubuntu VPS (Hardy), ive been following some tutorials on slicehosts which have worked well enough so far but im at the stage where im trying to configure my iptables.

I have managed to configure them as i reckon will be suitable, then according to the tutorial im following and many others it ive to edit /etc/network/interfaces

Apparently i have to add 
pre-up iptables-restore < /etc/iptables.up.rules

Just after [FONT=monospace]
[/FONT]iface lo inet loopback

In theory i suppose this makes sense but it doesn't work, when i reboot my server it reverts back to default. I then actually took the time to read the text at the top of the file which informed me that /etc/network/interfaces is automatically generated and then recommend that i edit the interfaces.template file which i tried looking for but apparently doesn't exist.

Im pretty sure im making a horrible noob mistake but its strange since every tutorial i read doesn't mention the problem above.

-Cheers

---


---
title: "VPN via linux-pptp not working with ipdredator"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by bryce123 on 2010-11-29
Hi guys,

I am trying to get VPN (ipredator pptp) running without the network-manager, but it seems to be impossible.

Using [[COLOR="Red"]this guide[/COLOR]]("https://help.ubuntu.com/community/VPNClient#Manually configuring your connection") does not work. 

The /etc/ppp/peers/ipredator from [here]("http://ubuntuforums.org/showthread.php?t=1472045") also does not seem to work. 
With logging on, it complains when I try to connect (sudo pon ipredator nodetach):
```
Connect: ppp0 <--> /dev/pts/1
MS-CHAP authentication failed: 
CHAP authentication failed
Connection terminated.

```


I am 99% sure that the syntax in my /etc/ppp/chap-secrets is correct.

---


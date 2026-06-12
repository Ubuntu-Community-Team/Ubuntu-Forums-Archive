---
title: "Lost internet connection when upgraded 8.04 to 10.04"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by olorin19 on 2011-07-25
I was running 8.04 and my internet (Comcast) comes via a Motorola SB5100 cable modem then into a Netgear router then into my Dell. When I upgraded to 10.04 yesterday, I lost the wired connection. The wireless connection still works fine, but I have not been able to get a wired connection. Also, most online solutions reference the Network Manager, which is nowhere to be found.

Anyone have any solutions? I would be willing to revert to 8.04 if needed, as that worked fine, and obviously I quite regret the upgrade!

---

### Post by .... on 2011-07-25
What is output of:
```
sudo lshw -C network
ifconfig -a
```

---

### Post by nm_geo on 2011-07-25
Be sure to get all the updates & upgrades.. 
 
```
 
sudo apt-get update

```
```
 
sudo apt-get upgrade

```
 
Something good might happen and you need them anyway.

---


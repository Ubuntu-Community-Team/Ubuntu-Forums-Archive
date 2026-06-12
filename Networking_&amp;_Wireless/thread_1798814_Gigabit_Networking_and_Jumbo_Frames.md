---
title: "Gigabit Networking and Jumbo Frames"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by erilidon on 2011-07-06
I am trying to get my internal network to gigabit. I have a Gigabit switch that is behind a gigabit firewall/router. The connection between the switch and router is running at gigabit speeds.

However my main Linux box is my "server" I just put in a new DLink DGE-530T 10/100/1000 Network card. It is however only running at 100mbps. I am not sure what the problem is. I have increased the MTU to 9000 but still it is only 100mbps.

I do know that it is not the cabling. It is all Cat5e.

Any ideas? Thanks!

---

### Post by jmoorse on 2011-07-12
MTU has nothing to do with negotiated speed, I recommend you don't change this.

Please install ethtool (sudo apt-get install ethtool) and provide the output of 'sudo ethtool [adapter]' where adapter is likely eth0

---


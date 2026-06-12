---
title: "Switching the networks"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by Ewgenijkkg on 2010-10-25
Hello, guys. I installed the new ubuntu a couple of days ago on my PC here. My problem is that I got several networks here at my working place, which I want to connect to alternately. What I do now is, that I go to the network connections each time, select the network I want to connect to, set its connection setting to "automatically connect" and restart my PC. But that is quite annoying.
 
So, what would be an appropriate way to achieve my goal? I tried the network manager, but in the current version it does not provide the necessery functionality.
 
BR
Ewgenij

---

### Post by arubislander on 2010-10-25
You are talking about switching wireless networks? Can't you just select the one you want by right clicking on the network indicator?

---

### Post by Ewgenijkkg on 2010-10-26
Hi, no, its not about wireless. Its about the usual LAN. I have different network cables here. Each cable is connected with its own network. I pull one cable out of the LAN-Port of my PC and put another one in.
 
As I said, for each network I have an own IP/TCP configuration. So, its only about switching between them. And it is quite annoying to restart each time...

---

### Post by SeijiSensei on 2010-10-26
You could add more network adapters to the machine and have full-time connectivity to all the networks.  Hopefully their address spaces don't overlap.  

You would need to make sure your computer didn't become a router.  By default IP packets aren't forwarded on Ubuntu machines, and you can reinforce the policy with some additional rules to the iptables FORWARD chain if you're still concerned.

---

### Post by mickwombat on 2010-10-26
try doing ```
# sudo /etc/init.d/networking restart
``` from a terminal instead of rebooting.

Confirm it has the settings by doing an ifconfig.

---

### Post by Ewgenijkkg on 2010-10-26
OK, I will try ;) Why doesn't it work with the network manager? I saw tutorials on the ubuntu site, where the network manager was able to switch between the networks "sites" on the fly. However, in the manager package I downloaded from ubuntu a couple of days ago, the functionality was not present!

---


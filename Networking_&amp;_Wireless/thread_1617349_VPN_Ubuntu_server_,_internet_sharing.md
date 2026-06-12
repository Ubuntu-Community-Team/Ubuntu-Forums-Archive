---
title: "VPN Ubuntu server , internet sharing"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Dmitry13 on 2010-11-09
I am trying to setup vpn on ubuntu server from which i want to share the  internet connection. It seems that internet works on the server, but when i try to  share that connection via eth1 problems begin. From the second PC I am  able to ping webs, but i can&#8217;t open them in any of the browsers. They  are opening  pages very slow, up to 5 mins. 
I have Ubuntu on my laptop (not a server  one). And I connect to the internet via VPN using NetworkManager. I do  all steps described in &#8220;Internet ConnectionSharing&#8221; section of this web  cite in order to share the internet from the laptop. After that I connect my PC to the laptop. That PC gets proper  internet connection. 
I had the same problem on my router WL-500. The problem was solved by setting &#8220;nomppc&#8221;. After that I  was able to get proper Internet connection behind the router. However  there is no such a setting as nomppc in ubuntu server pppd.
 
Any suggestions why it works via my laptop using NetworkManager, but  doesn&#8217;t want to work on another machine with ubuntu server?

Thank you in advance

---

### Post by Dmitry13 on 2010-11-09
Up

---

### Post by Dmitry13 on 2010-11-10
Solved

---


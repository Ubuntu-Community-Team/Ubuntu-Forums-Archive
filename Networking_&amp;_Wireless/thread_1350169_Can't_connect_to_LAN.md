---
title: "Can't connect to LAN"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by U-boy on 2009-12-09
Hi there,
   
  I’ve installed Ubuntu 9.10 on my old Compaq Presario v3000.  And now I can’t easily connect to LAN in my office. Ubuntu can’t take IP address from DHCP at once. I’ve to try connect several times before it gets connected. You know, I restart the notebook or plug in and out cable and there is rotating thing and it says “Disconnected – you are offline now”. Is there something wrong? With Windows XP it was easy. You just need to plug in the network cable and it gets IP from DHCP and you are connected. Can I do the same on Ubuntu?

---

### Post by ubhi on 2009-12-09
1. open terminal from application -> Accessories -> terminal
2. type network-admin
3. it open network admin dialog box, -> press unlock & enter ur login password
4. now check you network should be on automatic ip setting (DHCP) & clicked on enable roaming mode
5. last type ifconfi on terminal & check u get ip address from server or not..

---

### Post by cavh on 2009-12-09
The last command given by ubhi should be 'ifconfig', not 'ifconfi'

;)

---


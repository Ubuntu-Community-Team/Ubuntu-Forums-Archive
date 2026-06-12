---
title: "network monitor for others on the network"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by Wanas on 2009-02-27
I want a tool to let me know how much bandwidth is taken by others on my same network.
I want something easy like switchsniffer. 
all the other network users is using windows.

---

### Post by superprash2003 on 2009-02-27
[https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals](https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals)

---

### Post by Wanas on 2009-02-27
I want to monitor other users in the network not only me
and it would be great if its a gui

---

### Post by Perryg on 2009-02-28
> **Wanas said:**
> I want to monitor other users in the network not only me
and it would be great if its a gui

bandwidthd will do what you want.  Configure it to listen to any when it installs and then read the bandwidthd.conf file to see where it places the html pages. I use the static version but there is also one that uses PostgreSQL.

---


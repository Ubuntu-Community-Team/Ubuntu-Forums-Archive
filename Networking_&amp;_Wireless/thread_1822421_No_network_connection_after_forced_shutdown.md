---
title: "No network connection after forced shutdown"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by mosaik on 2011-08-10
I have installed ubuntu 10.04 on my laptop recently. Internet connection was working fine. Since a forced shutdown (monitor stayed black when starting from standby-mode, so I had to press the on/off button until the computer was off) there is no network connection any more. Is it possible that some configuration got corrupted? I have a german system, so I hope I get the terms right: when I check System->configuration(settings?)->Network connections then there is no entry in any of the tabs (cable, wireless, VPN, DSL) .. Since I have a LAN network, shouldn't there be at least an entry for cable?

thanks,
Andy

---

### Post by Iowan on 2011-08-10
My "other computer" has some bookmarks about similar problems. I'll try to fire it up here shortly and post a few.

---

### Post by 741Baus on 2011-08-10
Hi mosaik ,
          I have had this problem before with power outages and such, open up a terminal and paste these commands in it

 sudo service network-manager stop

```
 sudo rm /var/lib/NetworkManager/NetworkManager.state
```

```
sudo service network-manager start
```

running these codes generally gets your network connection up and running I hope this helps

---

### Post by mosaik on 2011-08-11
The problem was that the network was "deactivated". At first I had ignored the wireless symbol with the red exclamation mark (because I have a LAN and no wireless connection), but then I read this tooltip "Network deactivated" that made me wondering. After a right-click I could easily activate the network again. Hm, a hint that the network is deactivated and how to active it, would have been helpful.

Thanks,
Andy

---


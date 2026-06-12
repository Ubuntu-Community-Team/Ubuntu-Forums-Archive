---
title: "Wireless stalls"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by Sallée on 2011-11-22
My wireless connection stalls constantly.  Every couple of minutes or so, the notification pops up that my network is disconnected.  After several seconds, it reconnects, will sometimes repeat several times, and then reestablish the connection. This happens more often when I am using the connection, but also happens when there is no apparent traffic.  This same pattern occurs with both my home and work networks.

I have had this problem since installing oneiric, but in the past two days it has gone from occasional to nearly constant.  If I remember correctly, this was an issue pre-Maverick as well, but cleared up when I installed that release.

I have an ath9k card, have tried several solutions like turning off power management, setting up modprobe, and setting the MTU to 1500 bytes, but nothing has help at all so far.

---

### Post by bluexrider on 2011-11-22
Try this thread

[http://ubuntuforums.org/showthread.php?t=1866335](http://ubuntuforums.org/showthread.php?t=1866335)

---

### Post by Sallée on 2011-12-03
Seems to have worked.  Thanks for the tip.  I have been resisting wicd because of an issue when I started using Ubuntu, but it seems to work beautifully now.  Did have to fix the Unity tray, though.  To review:

```
sudo apt-get install wicd
sudo apt-get purge network-manager
gsettings set com.canonical.Unity.Panel systray-whitelist "['wicd-client']"
```

Then restart or log out/in.

---


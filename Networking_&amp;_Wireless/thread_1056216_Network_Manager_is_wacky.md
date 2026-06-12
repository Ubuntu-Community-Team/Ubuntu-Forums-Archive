---
title: "Network Manager is wacky"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by phantom3113 on 2009-01-31
I've been having some interesting experiences with network manager. Normally I connect to my home wireless network and NM connects fine right after I boot up. However, every now and then the connection's not very good so I try to reconnect to get a better connection (click on the panel icon and select the network to redo the connection). For some reason though, NM cannot reconnect to my home network no matter what it does. On the other hand, whenever I connect to my college's network, I can reconnect as many times as I want and it works fine!

Today though, after trying to reconnect and after fiddling a bit with NM, I rebooted and was prompted to put in the WEP key again (normal after fiddling with the connections). After I did that, the window that was doing the prompting froze so I xkilled it which removed the panel icon and (as far as I know) all of the GUI bits of NM. Strangely enough, my internet connection has never been faster. I've though about putting wicd on here instead, but I had a bad experience with it on 8.04 (I'm running 8.10) and I don't feel like reinstalling my OS if wicd fails again. Any thoughts on why this is happening and/or what I can do?

---

### Post by cariboo on 2009-01-31
If it works, why worry about it. :) You can reinstall network manager by using the reinstall option eg:

```
sudo apt-get reinstall network-manager network-manager-gnome
```

Jim

---

### Post by phantom3113 on 2009-01-31
True, I guess it just gets annoying sometimes. Fortunately, I've never had trouble with the Lan connection so I'll always have something to fall back on :P

---


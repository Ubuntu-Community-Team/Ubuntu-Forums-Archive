---
title: "Wireless can't Re-activate"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by chrisninjabay on 2012-05-22
I've bene useing lubuntu fore a cupple af years now and Im really fond of it.

But since I updated my eeePC to 12.04, this wierd Thing has happened.
When I turned off wifi in the task bar, I couldn't reactivate it.
I found a fix, where I logged into lubuntu netbook edition, and activate it there.
But sadly I accidentally switched that one off as well, and now I cannot find a way tu turn on my wifi again.

I do not have the possibility to connect on etherneti, since I'm currently staying in a hotel.

Please help


Best wishes Chris

---

### Post by km3952 on 2012-05-23
Have you tried Menu > Preferences > Network Connections ?

---

### Post by sssSami on 2012-05-23
Try this:
```
sudo /etc/init.d/networking restart
```

---


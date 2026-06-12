---
title: "Wired ethernet not working"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by arigwapo on 2009-01-28
I've just installed 8.10 on an Atom-based server.  The plan is to run it headless as a media server with a wired connection although I did all the testing using a wireless USB adaptor.  Everything was working great with wireless, including Remote Desktop.

Now that all the bugs have been worked out, I pulled out the wireless USB adaptor and plugged in the ethernet cable.  It doesn't work.  "Auto eth0" shows up under wired network, the green LED at the jack lights up and it tries to connect but it can't seem to hook on to the network.

Any ideas??

---

### Post by cariboo on 2009-01-28
I use an Intel Atom powered computer for a media center. I set up the wired with a static ip address, I am connected with both wireless and wired right now. You could try in a terminal:

```
sudo dhclient eth0
```

to see if you can obtain a dynamic ip address.

Jim

---


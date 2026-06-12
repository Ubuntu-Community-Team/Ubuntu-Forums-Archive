---
title: "Huawei E160 on 10.04.3 LTS Server (with no X)"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2011-11-23
Hello,
 
My ISP has a major fault in the area, and I would like to use my o2 dongle as a backup internet. The dongle is a Huawei E160 on o2.
 
My Ubuntu 10.04.3 LTS server is headless, and has various NIC's, and currently works as a router for the entire house. I do not have X / gnome / etc installed. it's console only.
 
Any advice welcome!
 
SS

---

### Post by sparky-steve on 2011-11-24
Although I didn't want to go on "alone" I had to get it up and running, and it was remarkably easy.

```
tail -f /var/log/messages
```

Plug the USB modem in....

Wait for it to all settle, and announce a huawei modem.

run wvdialconf (ironically, this wasnt installed, so the hassle of installing it is another story!)

```
wvdialconf /etc/wvdial.conf
```

That'll spurt out some stuff.. 

Then, if all has gone well, run wvdial

```
wvdial
```

and watch it connect.....

If, like me, you're running this on a router, you'll likely need to make changes to shorewall or whatever you're using...

For me, the temporary changes to shorewall was basically changing the "net" zone in /etc/shorewall/interfaces from eth1 (my ethernet modem) to ppp0 (my USB dongle).  YMMV.

It's worth noting that the console with wvdial running needs to stay open, and a CTRL-c will shut the connection off. 

Anyway, it might help someone in the future!

I intend (and indeed have started) to write a script to bring this interface online should the ethernet modem go down. If I have it working successfully, and I remember, I'll post back. If I havent, you could always bump me!

SS

---


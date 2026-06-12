---
title: "network / wireless icon 10.04"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by delboy1 on 2010-05-09
I have a fresh install of 10.04 but have a very odd icon for network / wireless

Essentially it is like the windows wired network icon with two terminals but it constantly has a red cross. This icon appear with wired or wireless networks and, as above, the red cross is constantly on whether or not I have successfully connected to a network.

Everything seems to be working OK but the icon is really frustrating as I constantly think there is a problem. Can anyone tell me how to change it?

Cheers

---

### Post by Iowan on 2010-05-09
Do you have interfaces defined in Network Manager or */etc/network/interfaces*?

---

### Post by delboy1 on 2010-05-09
> **Iowan said:**
> Do you have interfaces defined in Network Manager or */etc/network/interfaces*?

contents of etc/network/interfaces is


auto lo
iface lo inet loopback

---

### Post by TehWhale on 2010-05-09
I'm also having a similar issue. If I'm connected to wireless I have a exclamation point over the normal icon. My file is the same as the above.

---

### Post by robert.wilson1 on 2010-05-09
I had issues with this too... I removed the messed up icon from my panel about a week ago and was good until today. I took my laptop to another location and could not connect to anything. I brought it back to my original location and nothing. I broke out the ipod and found this post, and noticed no answers. 

I then right clicked on the panel --> add to panel --> and scrolled down to "Notificatoin area. Once added I got my internet icons back! 

End result, both my wired and wireless work wonderfully!

:guitar:

Hope this helps.

---

### Post by TehWhale on 2010-05-10
Okay at above post, now after I loaded Ubuntu to up to try this, it doesn't even display allow me to connect to a wireless network (doesn't show it)...****...

---

### Post by delboy1 on 2010-05-11
contents of etc/network/interfaces is


auto lo
iface lo inet loopback 


I have tried with a mobile broadband dongle and the icon changes to the mobile icon so it's like it is seeing wireless networks as wired

Can anyone help?

---

### Post by delboy1 on 2010-07-05
Anyone know of a fix for this yet?

---


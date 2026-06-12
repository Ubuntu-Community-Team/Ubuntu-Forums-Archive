---
title: "Ubuntu Server 12.10 Static IP"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by m7redp on 2013-02-12
Hello all,

I recently set up an old laptop as a media and file server for my home and I had gotten it set up to have a static ip, wireless network authentication, and static dns/gateway.  I am running Ubuntu Server 12.10 on a Dell Inspiron e1405 with an Intel networking card. I have gotten this all working then I accidentally unplugged it and since the lid was closed the laptop went to sleep. Upon waking up the wifi card will not turn on. (I do not mean it is disabled, I have tried ifconfig wlan0 up). The configuration is still there, but the light showing the wifi card is powered on, is off.  Restarting the server didn't help either.   Any help would be appreciated.

Thanks!

---

### Post by jdthood on 2013-02-12
Does rebooting fix it?

---

### Post by m7redp on 2013-02-12
Sadly, no it does not. I use to have this issue back when I was using Ubuntu for regular use, and rebooting would fix it. But since I have it set up to be used as a server I went in and configured the networkinterfaces file to connect to my home network, so I believe it is not using network-manager at the moment. Which may have something to do with it.

Like I said I have had this working for a few weeks now, with no problems through reboots, but this was the first time I have suspended it.  I will post more details on how I set up the static ip, and my specific wireless card once I get home. I do not have the machine with me at the moment.

---

### Post by ahallubuntu on 2013-02-12
~

---


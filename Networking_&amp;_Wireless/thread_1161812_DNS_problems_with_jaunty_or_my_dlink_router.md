---
title: "DNS problems with jaunty or my dlink router"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by sonicb00m on 2009-05-17
Just recently the webbrowsing has been constantly dropping making browsing useless. I am sure it's something to do with dns resolving in Jaunty since Pidgin and filezilla are still active with sending/receiving.

I also have [www.google.com](www.google.com) hardcoded in my /etc/hosts file to fix googleearth connection issues and unsurprisingly it's the only website that works when this problem happens.

It is also possible that the router could be responsible since the only thing that fixes it is disconnecting and reconnecting to the internet (no reboot or anything required).

I have a dlink DIR-615 if anyone knows of any problem with it. It's driving me nuts and seems to be getting worse.

---

### Post by bruno9779 on 2009-05-17
If it is a DNS issue, the easiest solution I can think of is setting some custom DNS servers:

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by homburg on 2009-06-02
I had a similar problem with my d-link dir615 router.

I was able to ping ip adresses outside of my lan but could not resolve web adresses.

Also I was unable to ping local computers by their hostname (eg. "$ ping server.local")

Everything worked fine a while after rebooting the router for a few minutes/hours.

But I think I have resolved the problem by updating my router firmware from version 4.00 to 4.11
I downloadet the firmware from d-link's support page. The routers firmware auto-update function didn't seem to work.

Hope this helps.

---


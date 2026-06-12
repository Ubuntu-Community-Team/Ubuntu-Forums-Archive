---
title: "Maverick internet connection problems"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by aethex on 2010-10-11
Hi, all
I have a Trendnet USB network dongle in my desktop (for lack of a wifi card). It shows up as Ralink 2770 or the like in lsusb. I've had problems with this thing before, in Lucid, but it was solved by installing the lucid network backports.

Now, I've been there, done that, and while my internet is working for a few minutes, it is about as slow as dial-up and mysteriously disconnects every so often. I have to disable/re-enable networking in order to get it up again.

I'd have thought that this would have been fixed by maverick (hence the backports), but apparently not. Any help?

---

### Post by dnelub on 2010-10-21
I have exactly same problem after installing maverick apart from the model of usb wireless model. Mine is Ralink RT2870.

---

### Post by aethex on 2010-10-30
Come on, guys, help us out here.

---

### Post by srhart on 2010-10-30
Hi
I dont have a Ralink NIC but I did do a quick Google on your behalf and found a bug on Launchpad that may be related - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866")

I scanned it and, if relevant, it looks like there's a workaround that may help.

Good luck
Simon
--------------------
[www.L3n.co.uk]("http://www.L3n.co.uk") L3n Network Support - Contact L3n for voice and data network design, supply, installation and support - based in Cambridge UK

---


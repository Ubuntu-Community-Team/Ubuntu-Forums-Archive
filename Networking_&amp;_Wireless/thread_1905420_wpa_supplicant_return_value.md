---
title: "wpa_supplicant return value?"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2012-01-06
Is there a return value that I can look for with a script or something that will allow me to know when wpa_supplicant has established a connection while running as a daemon?

---

### Post by chili555 on 2012-01-06
I don't know the answer directly, but maybe this, from /var/log/syslog will help:> Jan  6 20:25:21 LAPTOP60 wpa_supplicant[6470]: **CTRL-EVENT-CONNECTED** - Connection to 99:13:10:62:88:77 completed (reauth) [id=0 id_str=]

---

### Post by brandon88tube on 2012-01-06
Hmm, I'm not sure. I could possibly make some script that searches the syslog for that output, but that seems like a lot. I was hoping there would be some simpler indications that it was connected to make it easier.

Edit:
Oddly, I checked my log and didn't notice the CTRL-EVENT-CONNECTED showing up today... Seems it didn't report that, but it did show dhclient.

---

### Post by brandon88tube on 2012-01-07
Anyone have any other ideas? I doubt I can use the suggest method above as it doesn't seem all that reliable not to mention how much text it would have to search in order to find it along with having to use the date and time.

---


---
title: "Wireless can see networks but fails to connect. (Ubuntu 10.04)"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by Kellen0070 on 2010-06-30
I have an Atheros AR242x card.  It can see my wireless network (WPA2).  When i attempt to connect to the network it asks for the WPA2 passphrase.  After entering the password it begins connecting but hangs up for about 3 minutes before saying wireless disconnected.  The wireless worked for one day on a fresh install (Ubuntu 10.04)and then started doing this.

---

### Post by Geneset on 2010-06-30
I have a similar issue, I have an intel card that refuses to connect to a completely open AP; Win7 has no problem on the same machine, and the machine has no problem connecting to other, secured, AP's. The Access point itself is a Netgear, and the specific wifi care is a intel 4965.

Syslog pickes up a lot of disconnect reason=6 events (see attached) which implies that the AP gave up waiting for authentication, but there is no authentication!

[PS I've been stuck with this query for quite a while now, and noone seems to have a decent answer :(]("http://superuser.com/questions/152427/ubuntu-9-04-cannot-connect-to-visible-open-wifi-ap-reason-6")

---

### Post by Geneset on 2010-07-08
I fixed this by using the compat-wireless drivers; writeup [here]("http://goo.gl/fb/93hJP")

---


---
title: "how can I identify wireless protocol version (b,g or n) in use ?"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by scotty64 on 2012-12-14
Is there a way to identify the protocol version (b,g or n) in use for a particular wireless connection ?
thanks for any help, Mark

---

### Post by haqking on 2012-12-14
> **scotty64 said:**
> Is there a way to identify the protocol version (b,g or n) in use for a particular wireless connection ?
thanks for any help, Mark

look at your bit rate

iwlist <iface> bitrate

b =11
g = 54
N = (cant remember what it shows for N, i think it depends on your adapter) I think it shows 300

or look at your connection GUI

There are better ways to check with additional software tools such as kismet or airmon but i wont go into those here

---

### Post by agklimit on 2012-12-15
Just out of interest, I tried iwlist (on a working wifi connection) and it comes up with "no information" whatever command option is used (including bitrate). (Both with and without sudo, it's the same).

---

### Post by haqking on 2012-12-15
> **agklimit said:**
> Just out of interest, I tried iwlist (on a working wifi connection) and it comes up with "no information" whatever command option is used (including bitrate). (Both with and without sudo, it's the same).

mmm not sure, can you show us a screen dump or terminal output

---


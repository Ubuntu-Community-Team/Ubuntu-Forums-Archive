---
title: "Totem sends data on the network ?"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Antoine Guigan on 2008-11-06
Since I upgraded to Intrepid, Totem seems to send a lot of data over my ethernet card (120 xbytes/s as reported bu System Monitor)
If I type 

```

$ sudo ifdown eth0
$ sudo ifup eth0

```

the network traffic goes back to normal...

Anybody has a clue about what is happening ?

---

### Post by Antoine Guigan on 2008-11-18
Well, I found my answer. It was pulseaudio which was sending data.

---


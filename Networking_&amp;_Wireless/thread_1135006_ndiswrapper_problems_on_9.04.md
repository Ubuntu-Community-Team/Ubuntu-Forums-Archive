---
title: "ndiswrapper problems on 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by krojew on 2009-04-24
I upgraded my system form 8.10 to 9.04 and I have problems enbaling wifi on my Dell Vostro 1500. I installed bcm43xx using nidswrapper (using ndisgtk) but wifi isn't working. nidswrapper -l shows:

```
bcmwl5: driver installed
device (14E4:4328) present (alternate driver: ssb)
```

Can anybody help?

---

### Post by krojew on 2009-04-24
Fixed it - just needed to add:

```
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44
```

to /etc/rc.local

---


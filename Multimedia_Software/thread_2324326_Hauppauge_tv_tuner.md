---
title: "Hauppauge tv tuner"
date: 2016-05-12
forum: Multimedia Software
---

### Post by kulaywolf on 2016-05-12
I got a Hauppauge Tv tuner.   What software can I use to watch tv with it?

---

### Post by pablosquared on 2016-05-13
I use VLC with my elderly Hauppauge PCI DVB card (UK). I installed w-Scan ([http://wirbel.htpc-forum.de/w_scan/index_en.html](http://wirbel.htpc-forum.de/w_scan/index_en.html)), a command line app which searches for channels and creates a file which I open in VLC to view TV.

```

w_scan -ft -c GB -X >> channels.conf

```

It's easy enough to create a Unity launcher, or similar for your preferred desktop environment, that loads the .conf file on VLC startup, so that you can watch TV without having to manually load the TV channel listing.

---


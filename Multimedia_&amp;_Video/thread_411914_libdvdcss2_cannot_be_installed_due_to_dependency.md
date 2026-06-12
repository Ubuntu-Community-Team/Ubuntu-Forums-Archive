---
title: "libdvdcss2 cannot be installed due to dependency"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by CTZenObserver on 2007-04-17
I have installed Ubuntu 6.0.6 LTS. Everything works fine except that I cannot run DVDs. After searhcing many forums I realized I need libdvdcss2to be installed, so I tried to do that and got the following error

```
libdvdcss2:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
```

On my machine I installed the latest version of libc6, I have the same version of libc6 on my machine and yet cannot install libdvdcss2.

I have attached a screen shot from Synaptic to make sure I am giving you the correct version number

Please help
Thanks a million.
CTZenObserver

---

### Post by mshale on 2007-04-17
you might try to reinstall all of the libc6 files and while you are at it, try that libc6-dbg file. ;)

---

### Post by CTZenObserver on 2007-04-17
Thanks for the quick reply...
Now I have the library, the debug version, and the development version, and the problem still persists.
Any other suggestions?
Thanks again

---

### Post by CTZenObserver on 2007-04-18
I solved the problem.
All along it was telling me that I needed the latest version of the library. I upgraded to 2.1.0 edgy and the problem was fixed.
Still totem does not work, but other media players (gxine or mozilla mplayer) work just fine.
Note: In order to upgrade to edgy one needs to run the following command in terminal:
gksu "update-manager -c -d"

---

### Post by mshale on 2007-04-19
very nice.  thanks for the extra info!

---


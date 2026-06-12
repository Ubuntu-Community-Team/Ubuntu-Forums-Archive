---
title: "How to get wireless adapter to work on ubuntu 11.04"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by kchowk on 2011-09-04
I am a complete and total linux noob (I just installed ubuntu yesterday), and I can't seem to get my wireless usb network adapter working.  I have a linksys WUSB300N.  I tried googling it, and I tried some of their methods, but nothing seemed to work for me.  I read somewhere that you have to install Ndiswrapper to get the drivers working, but being a total linux noob, I couldn't install that either.  So how can I get a Linksys WUSB300N adapter to work?  Thanks!

---

### Post by praseodym on 2011-09-08
Hello,

please show the output of the following terminal commands:

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by lkjoel on 2011-09-08
Could you run the Network Info script (in my signature), and attach the generated file?

---


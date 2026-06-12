---
title: "no wireless dell m1530"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by searayman on 2009-05-26
I had wireless working then I upgraded to 9.04 it started to work randomly and now it doesn't work at all. Any ideas to diagnose the problem and fix it

---

### Post by Crafty Kisses on 2009-05-26
What are the results of these commands?
```
lspci
lshw -C network
lsusb
ifconfig
iwconfig
```

---

### Post by searayman on 2009-05-26
> **Codename said:**
> What are the results of these commands?
```
lspci
lshw -C network
lsusb
ifconfig
iwconfig
```


lspci: [http://pastebin.ca/1435592](http://pastebin.ca/1435592)

lshw -C network: [http://pastebin.ca/1435593](http://pastebin.ca/1435593)

lsusb: [http://pastebin.ca/1435594](http://pastebin.ca/1435594)

ifconfig:[http://pastebin.ca/1435595](http://pastebin.ca/1435595)

iwconfig:[http://pastebin.ca/1435596](http://pastebin.ca/1435596)

ok here are all my results to those commands, let me know if you see how we can fix this. Thanks for the help!

---

### Post by searayman on 2009-05-26
anyoen else have any ideas after looking at my diognostics?

---

### Post by Crafty Kisses on 2009-05-26
Read this: [http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328).

---

### Post by searayman on 2009-05-26
> **Codename said:**
> Read this: [http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=297092&highlight=BCM4328).

When I get to step 3 and do the sudo make it ends with this error:

ion ‘iwe_stream_add_point’
make[3]: *** [/home/mike/ndiswrapper-1.51/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/mike/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mike/ndiswrapper-1.51/driver'
make: *** [all] Error 2
mike@ubuntu:~/ndiswrapper-1.51$

---

### Post by Crafty Kisses on 2009-05-26
Make sure you have the following package installed:
```
sudo apt-get install build-essential
```

---

### Post by searayman on 2009-05-26
I just did a clean install of 9.04 and wireless still doesn't work but this time lshw -c network after running doesn't display anything

---

### Post by Ayuthia on 2009-05-27
Have you tried going into System->Administration->Hardware Drivers and enabling the Broadcom STA module?

---

### Post by searayman on 2009-05-27
> **Ayuthia said:**
> Have you tried going into System->Administration->Hardware Drivers and enabling the Broadcom STA module?

It says this driver is activated but not currently in use. So how do I get it in use?

---

### Post by Ayuthia on 2009-05-27
Try the following from the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
Let us know if it reports back any wireless sites.

---


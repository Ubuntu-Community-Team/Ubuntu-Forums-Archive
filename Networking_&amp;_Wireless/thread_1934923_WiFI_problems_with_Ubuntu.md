---
title: "WiFI problems with Ubuntu"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by Jayhawker on 2012-03-03
After some time reflecting on and watching my HP laptop 6500 series and HP notebook 110's behaviour with Ubuntu 11/10, I come to the conclusion that my router WIFI doesn't fit with HP computers for some reason. 

I'll explain myself: Ubuntu 11/10 is inside WIndows at both computers. Both of them work perfectly when catching any library's or coffee shop's WIFI signal for instance. But they don't catch my own router WIFI. Needless to say that when in Windows there is not any problem at all.

SO, might the problem be that my router works at 128 bits WEP instead of WPA/WPA2?

I must add that another old PC computer which works exclusively with Ubuntu 9.04 has not any problem with my Router WIFI. So must I infer that when in Ubuntu as a sole Operating System there is not problem with any kind of WIFI signal? 

Thanks

---

### Post by praseodym on 2012-03-03
Which hardware is in use? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by mordsith007 on 2012-06-04
Have you tried these methods: [http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)

---


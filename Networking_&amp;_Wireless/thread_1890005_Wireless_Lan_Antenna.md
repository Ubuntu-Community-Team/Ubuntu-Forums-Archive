---
title: "Wireless Lan Antenna"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by leshin88 on 2011-12-02
I just install ubuntu on my pc and it can not recognize my wireless lan antenna... where can i find the drivers?
Wirelles Lan Geetek Janus 2 part#:GT-H10DN

---

### Post by jonobr on 2011-12-02
Hey Chief

Welcome to the forums

Recommend you post some information on your device hardware so people can see what your running
Also , if you read the sticky which is the third one from the top posted by bapoumba, it will give you a lot of great info on finding out info, using the howtos and posting info.
Cest of luck

jonobr

---

### Post by poolet on 2011-12-02
hey, please open up a new terminal... to to Applications-->>Accessories -->> Terminal 
write the following and paste the output here:: 

```
 sudo lshw -C network
``````
 uname -mr gt 
``````
lspci
``````
lsusb
``````
 lspci -nn | grep 'Wireless Brand'
``````
 ifconfig
``````
iwconfig
``````
iwconfig wlan0
``````
 lsmod
``````
 lsmod | grep "wlan_module_name"
``````
 dmesg
``````
 iwlist scan
```

---


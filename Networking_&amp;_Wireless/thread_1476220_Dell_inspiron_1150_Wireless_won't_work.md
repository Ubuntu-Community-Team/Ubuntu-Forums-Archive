---
title: "Dell inspiron 1150 Wireless won't work"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by pckid on 2010-05-07
hi
my dell inspiron 1150 internal wireless won't work and ive tried ndiswrapper. can some one give me the link to an open source driver? My ubuntu distro is 9.10 (soon to be 10.04 as soon as i get the video drivers;) ) 

dell inspiron 1150 
ubuntu 9.10/10.04 
512 mb ram
40 gb hd
intel centrino cpu 2.80 ghz

---

### Post by bkratz on 2010-05-07
> **pckid said:**
> hi
my dell inspiron 1150 internal wireless won't work and ive tried ndiswrapper. can some one give me the link to an open source driver? My ubuntu distro is 9.10 (soon to be 10.04 as soon as i get the video drivers;) ) 

dell inspiron 1150 
ubuntu 9.10/10.04 
512 mb ram
40 gb hd
intel centrino cpu 2.80 ghz

Actually we need to find out what wireless card you have.

Go to the terminal (Applications>>Accessories>>Terminal) and enter


```
lspci | grep Wireless 
```


Hopefully it will tell us what card you have, If no output, just try 

```
lspci
```

and look for it. (Those were LSPCI in lowercase--W in uppercase)

---

### Post by pckid on 2010-05-10
i switched to ubuntu studio 9.10 and off the bat it said "new drivers are available for your hardware". so i just clicked on that and all my problems were gone. ;)

---

### Post by pckid on 2010-05-24
There is also another way (I just realized). You update your machine and reboot, then go to System>Administration>Hardware Drivers then click update then reboot. Voila!

---


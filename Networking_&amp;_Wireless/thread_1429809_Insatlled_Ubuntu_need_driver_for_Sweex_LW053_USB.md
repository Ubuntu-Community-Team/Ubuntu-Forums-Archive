---
title: "Insatlled Ubuntu need driver for Sweex LW053 USB"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by Lincshistory on 2010-03-14
Hi All
 
I have installed Ubuntu [first time user] on to my kids PC as it is quite old and struggling with MS. 
 
I now need a driver to make their Sweex LW053 Wireless LAN USB 2.0 Adaptor connect to the internet.
 
Any help really appreciated, please explain in a step by step guide as I am an intermediate computer user.
 
Thanks

---

### Post by chili555 on 2010-03-14
Please open Applications > Accessories > Terminal and do:```
lsusb
```Post the part that seems to relate to your device (hint: it may be a Ralink). If it turns out to be 148f:2573, then I will need this little hint I am leaving for myself or any others who may answer.```
$ modinfo rt73usb | grep 2573
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt2500usb | grep 2573
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
```Thanks.

---


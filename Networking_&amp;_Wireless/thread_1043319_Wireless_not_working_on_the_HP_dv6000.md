---
title: "Wireless not working on the HP dv6000"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by zwingly03 on 2009-01-18
Hello my friends,

I recently installed Ubuntu 8.10 after usin other distros, but I'm unable to use wireless. I installed the backports, wifi-radar, the firmware, but it doesn't work. The led is still orange, which means that the wireless card isn't working. However, the card worked perfectly on Mandriva and Fedora 10.

Could somedy help me please???

---

### Post by cdtech on 2009-01-18
Post the output of:
```
iwconfig
```
Which card are you using? Post:
```
lspci
```

---

### Post by zwingly03 on 2009-01-19
Well, I checked the Synaptic and installed the 3 backport modules packages and 3 the headers packages and it now works :P. So I think if somebody has the same problem on Ubuntu Intrepid, make sure you have linux-backports-modules-intrepid-generic, linux-backports-modules-intrepid and linux-backports-modules-2.6.27-9-generic for the backports, and linux-headers-lbm-2.6.27-9-generic, linux-headers-2.6.27-9-generic and linux-headers-2.6.27-9 for the headers. 

By the way, I'd like to thank you cdtech for you quick response :)

---

### Post by LinkRJH on 2009-03-11
Hey, I was having this same exact problem on the same exact laptop, however installing the things you listed didn't make it work. It still says 'no device found.'

I'd really like to get this laptop up and running. Is there anything else you did or installed?

---

### Post by LinkRJH on 2009-03-12
?? :(

---


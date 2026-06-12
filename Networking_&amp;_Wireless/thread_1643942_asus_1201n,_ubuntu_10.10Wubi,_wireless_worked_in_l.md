---
title: "asus 1201n, ubuntu 10.10/Wubi, wireless worked in live usb but now does'nt"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by doron387 on 2010-12-12
i have installed ubuntu 10.10 desktop 32bit using Wubi on an asus 1201N netbook (Win7 is the main OS).
before i installed it, i tried it using a live usb and the wireless worked (SURPRISINGLY i have to mention !!! LOL to the developers).
but after installing with Wubi the wireless does not recognize my wireless net. 
what shall i do ?
[ some more info : the Win7 uses RTL8192SE wireless driver ]
----------------
EDIT : SOLVED !!!
follow the very simple instructions in this site :

[http://gadgetmix.com/netbook/wi-fi-not-working-on-asus-eee-1201t-or-1201n/comment-page-1/#comment-25147](http://gadgetmix.com/netbook/wi-fi-not-working-on-asus-eee-1201t-or-1201n/comment-page-1/#comment-25147)

and indeed voila !!! it works, but every time i reboot i have to go to terminal and type :
sudo su
password
modprobe r8192se_pci

---


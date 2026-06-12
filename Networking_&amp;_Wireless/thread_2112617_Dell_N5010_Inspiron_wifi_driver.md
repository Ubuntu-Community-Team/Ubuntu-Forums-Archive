---
title: "Dell N5010 Inspiron wifi driver"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by tharejamohit on 2013-02-05
Dell N5010 INSPIRON WIFI DRIVER PROBLEM 

I SERACH IN DELL SUPPORT CENTER I CAN DOWNLOAD ALL DRIVER FROM DELL SUPPORT SITE BUT NOT MATCH DRIVER

PLZ HELP SOMEONE TO SOLVE MY PROBLEM

THANKS
BR.

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by tharejamohit on 2013-02-06
> **ahallubuntu said:**
> You will need to figure out which wireless card you have and update/install the driver yourself.  You probably won't get it from Dell.

Open a terminal window.  What's the output of these commands?

```
uname -r
sudo lshw -C network
iwconfig
lspci | grep -i broadcom
```


i am using windows 7 not linux
bro i dont know how to check with terminal plz help 

i check on device manager 

network controller is missing 

[[IMG]http://img502.imageshack.us/img502/2954/wifis.png[/IMG]](http://imageshack.us/photo/my-images/502/wifis.png/)

---


---
title: "No wireless detection on Dell Inspiron E1405"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by dmubu on 2011-09-18
Hello,

I just installed Ubuntu on an older machine, and there are no wireless networks being detected.

I believe that I have installed the proper drivers.  Further, when I run ```
iwconfig 
```, I get the following output:

```


lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.


```

There is no wlan0.  What should I do?

Thank you.

---

### Post by wildmanne39 on 2011-09-18
Hi, please run these commands and post the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by dmubu on 2011-09-18
Thanks for the reply...

I actually got it working by installing the drivers via a wired connection and rebooting.  Before, I was using a wireless usb card.  I am not sure why the new method worked, but it did.

Thanks again for the help.

---

### Post by wildmanne39 on 2011-09-18
Hi, I am glad you got it working, enjoy ubuntu.
Thank you

---


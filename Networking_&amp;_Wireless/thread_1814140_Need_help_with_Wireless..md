---
title: "Need help with Wireless."
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by Mexican97 on 2011-07-29
Ok, So I just recently got ubuntu 10.10 and it doesnt let me connect to my wireless.. The wireless is good because I have other laptops that connect perfectly. The only way I can connect is if I plug in my phone and tether it. Can someone please help me???!!!

Thanks, Mexi

---

### Post by wildmanne39 on 2011-07-29
Hi, run these commands in a terminal please 
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
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
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Mexican97 on 2011-07-29
I dont really know anything about this... I just learned about it today, so im not sure what its under. im not the most amazing with computers.

---

### Post by Mexican97 on 2011-07-29
I figured it out, I just had to install drivers, thanks for the help though!

---

### Post by wildmanne39 on 2011-07-29
Hi, your welcome,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---


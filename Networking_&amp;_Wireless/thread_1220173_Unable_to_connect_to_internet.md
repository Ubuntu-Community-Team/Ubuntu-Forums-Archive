---
title: "Unable to connect to internet"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by Austin B on 2009-07-22
Hi,
 
I'm currently using Ubuntu on my laptop, and I'm impressed with it, although it is a bit confusing at first.
 
Anyways, I'm not able to really get onto the internet from it. Why? I have no clue, in the Network Manager it shows that I'm connected to the internet, but when I open Firefox and try to go to a website, It says that I'm not connected to the internet.

---

### Post by martinbaselier on 2009-07-22
First of all, are you connected wireless or by cable?
What kind of network card (brand and type) are you using? 
If it's wireless, is there any form of encryption?

---

### Post by Austin B on 2009-07-22
It's Wireless.
I have NO CLUE what that is.
No, It's not security encrypted.

---

### Post by martinbaselier on 2009-07-22
open a terminal and paste the following command to it:
lspci
please copy the output (mouse to select, ctrl+shift+c to copy)
and paste it here. use  [ code ] [ /code ] to enclose the text (remove the spaces for the tags to work.)

---

### Post by Austin B on 2009-07-22
I'm getting alot of ATI Technologies devices, but I'm not sure which is which. And I can't copy the text to here, because I'm on another computer, I have my laptop with Ubuntu beside me.
 
I think I have an RTL-8185, although I'm not quite sure.

---

### Post by Austin B on 2009-07-22
I did lspci -v | less and got something saying something like this
 
```
Kernel driver in use: rtl8180
```

---

### Post by superprash2003 on 2009-07-24
post output of
1)ifconfig
2)iwconfig
3)ping google.com

---


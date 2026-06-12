---
title: "help UNDOING"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by desertfox1986 on 2009-01-02
so i was tyeing to add something to make my zune work on Ubuntu and i did something to my WIFI. I cant connect though it. is there something like time machine. i got Ubuntu 8.10 i think and my WIFI is a Broadcom STA wireless. it did work before.i cant find the forum tells me how to make the zune to work. all i know is that i use terminal to add the code.

i know how bad my grammar is, i just need some help

---

### Post by superprash2003 on 2009-01-02
presuming wifi doesnt work now.. post output of 
1)iwlist scanning
2)iwconfig

---

### Post by Ayuthia on 2009-01-02
Please also include:
```
lsmod|grep -e b43 -e ssb -e wl
```Those are the possible modules for your wireless card.

---

### Post by desertfox1986 on 2009-01-02
> **superprash2003 said:**
> presuming wifi doesnt work now.. post output of 
1)iwlist scanning
2)iwconfig

this is what i got
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

jason@jason-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

---

### Post by superprash2003 on 2009-01-03
ensure that the wifi driver is enabled under administration->hardware drivers .. try re - enabling it..

---

### Post by desertfox1986 on 2009-01-04
> **superprash2003 said:**
> ensure that the wifi driver is enabled under administration->hardware drivers .. try re - enabling it..

it say that it is enabled

---

### Post by Ayuthia on 2009-01-05
Have you tried the following from the Terminal:
[code]sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart[/code[

---


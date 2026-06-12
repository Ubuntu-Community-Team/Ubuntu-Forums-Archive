---
title: "Wireless Not Working On Laptop"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Moneykidz1 on 2009-12-15
Hey everyone, I'm new to Ubuntu and the Ubuntu Forums and I have a question.
 I just installed Ubuntu 9.10 on my Dell Inspiron 700m. And for some reason, the WiFi doesn't work. I'm not sure what to do. I'm not familiar with Ubuntu. So if you could please help, I would appreciate it. Thanks.
 

 Also......
 Should I reinstall Ubuntu 9.10? The disc I used was a month or so old. Should I download Ubuntu 9.10 off Ubuntu's website? And leave my Internet line plugged in when Ubuntu is installing? Once again, I'm not familiar with Ubuntu. So if you could, please help me.

---

### Post by chili555 on 2009-12-15
First of all, I would not re-install quite yet.

I think your laptop uses the Intel ipw2200 module. Let's ask the computer to tell us! Open a terminal (Applications -> Accessories -> Terminal) and do:```
lspci | grep -i wireless
```Post the result and we'll solve this!

---

### Post by Moneykidz1 on 2009-12-15
> **chili555 said:**
> First of all, I would not re-install quite yet.

I think your laptop uses the Intel ipw2200 module. Let's ask the computer to tell us! Open a terminal (Applications -> Accessories -> Terminal) and do:```
lspci | grep -i wireless
```Post the result and we'll solve this!


Says

02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by Moneykidz1 on 2009-12-15
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by chili555 on 2009-12-15
Very nice! Now let's see if the module is loaded. Please do:```
lsmod | grep 2200
```If you do see that it is loaded, please do:```
iwconfig
```Please post the result. If it is not loaded, let's load it:```
sudo modprobe ipw2200
iwconfig
```Now, do you have a wireless interface, *eth1*, perhaps? If loading the module didn't start the wireless, then let's do some exploratory surgery:```
dmesg | grep 2200
```Please post the results.

---


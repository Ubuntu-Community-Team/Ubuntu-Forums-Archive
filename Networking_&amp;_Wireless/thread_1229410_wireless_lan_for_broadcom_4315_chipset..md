---
title: "wireless lan for broadcom 4315 chipset."
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by magic_din on 2009-08-02
I am having HP compaq 6535s series NT334P model laptop. It has AMD turion processor and 4315 broadcom wireless chipset for IEEE b/g standard. I have latest ubuntu 9.04 intalled and have updated it till date. I have WAP-personal encryption always on internet wireless connection. I am new to ubuntu yet seeing the posts, I have tried the ndiswrapper installation and installing the driver but in vain. Anyone please help me.

---

### Post by magic_din on 2009-08-02
after upgrading to the latest kernel : 2.8.26.13 and restricted module 2.8.26.13.17 version. then using the wireless connection wizard I entered the password and connection name. I connected to the my hidden network ( not publishing SSID). It ask the connection name and password three times. I pressed ok everytime and then It gets disconnected. 
Now, The connection comes into the menu when left click on wireless connection icon. then selected the name of my wireless connection, It got connected. 
Finally, It works though it fails for 3 times.

I have also added a line 
wl 
in the /etc/modules. so that it automatically loads the driver wl.

---

### Post by lance bermudez on 2009-08-19
would you please open a terminal and type
sudo uname -r
please let me know what the kernel is that you are running now. are you running 2.6.28-15-generic? what driver did you use for the ndiswrapper could you please tell me where you got it from.

---


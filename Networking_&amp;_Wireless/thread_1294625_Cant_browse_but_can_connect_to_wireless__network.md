---
title: "Cant browse but can connect to wireless  network"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by jack_the_lad on 2009-10-18
So i have 9.04 ubuntu installed with dual booting with win xp. On win xp i must set my ip adress as 192.168.1.x, subnet mask 255.255.255.0, default gateway as 192.168.1.1 and manually configure dns servers to browse. It works perfectly. 

In ubuntu I can see my network and when I try to connect it asks me for a key. I put the key and then it says that I'm connected but when I open firefox I cant browse anything. Also I cannot ping 192.168.1.1. Can someone tell me what to do? Do I have to install drivers for wireless usb adapter?

---

### Post by ajgreeny on 2009-10-18
If you can see the router then it's not a driver issue, but probably a security keyword/password issue.  WEP or WPA?  Perhaps you need to use the encrypted version of the keyword you entered.  There seem to have been a few posts on this subject just in the last few days.

---

### Post by jack_the_lad on 2009-10-18
i have a WPA-PSK key and i realized that when i enter correct key and connect to my network and when i click edit connection and go to wpa key that the key is protected with ***'s and when i click on show key it shows some random set of characters that has nothing to do with my network key also when enter dhcp wlan0 the result is wmaster0: unknown hardware address type 801.

also when i reset my connection it sometimes loads my login page with user: password: fields for my router (the 192.168.1.1 page in firefox) it loads it only once. i don't know what to do. please help

---

### Post by jack_the_lad on 2009-10-18
> **ajgreeny said:**
> If you can see the router then it's not a driver issue, but probably a security keyword/password issue.  WEP or WPA?  Perhaps you need to use the encrypted version of the keyword you entered.  There seem to have been a few posts on this subject just in the last few days.

are you sure its a password protection issue because network manager tells me i'm connected every time. i think that some other process is blocking connection or something.

---

### Post by jack_the_lad on 2009-10-18
solved this with compat-wireless-2.6.30.tar.bz2 update

---

### Post by david-emm on 2009-10-19
This is the same problem that I'm having right now. You have solved your with compat-wireless-2.6.30.tar.bz2 update. I'm loath to put this in blind so to speak on my system so can you tell me what (who) pointed you to this solution. Thanks

---

### Post by jack_the_lad on 2009-10-21
sorry for such a long delay.

check out [http://linuxwireless.org/](http://linuxwireless.org/) i remember that that page was very useful

---


---
title: "Help needed with Wi-Fi"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by tyrannor on 2009-04-02
Hello,

I am very new to this OS and am struggling to get my wireless card working.
I know that similar questions have been answered in other threads and various other forums, but they are not in detail.
I have absolutely no knowledge of Ubuntu so I cant understand half the stuff that is said in the threads. I will be glad if someone solves my problem as I am close to pulling my hair out.

My Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
OS is Ubuntu 9.04 32 bit

Hoping for a detailed set of instructions soon.
Thanks in advance,
tyrannor

---

### Post by gdave on 2009-04-02
a quick search for "linux wireless bcm4318" brings up a lot of links.

you might get some mileage here:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/)

---

### Post by tyrannor on 2009-04-02
Thanks for the reply but the procedure that has been mentioned in the link will not work because the blacklisted file is protected and somehow I cant change it's contents.

---

### Post by freonchill on 2009-04-02
if you are editing a file that is not in your space (e.g. /home/your_user_name) then you are going to have to sudo gedit file or sudo vi file

---

### Post by superprash2003 on 2009-04-03
try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html) . if this doesnt work try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

---

### Post by tyrannor on 2009-04-08
Thanks, will try and post back.

---

### Post by Cheburator on 2009-04-09
Hi! I have the same wifi chip on my HP compaq laptop with ubuntu 8.10. On the first startup after install you should have got a restricted driver pop-up.. There you should have the option to chose the broadcom STA (my choice) and b43.
You can check on restricted drivers in system->administration->restricted drivers (i think..not on my ubuntu machine right now) or try "sudo jockey-gtk" in terminal

Is your wifi button active?

---


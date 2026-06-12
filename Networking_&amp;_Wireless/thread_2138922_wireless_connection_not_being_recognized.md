---
title: "wireless connection not being recognized"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by pajopet on 2013-04-25
I have 2 ASUS itx mobos Z77 & H77. Gnome doesn't even see the Broadcom  connection on the Z77 and niether Gnome nor Unity accept the ASUS N13 wifi stick connection although they recognize N13 the usb device. This is confusing since Pinguy ][Gnome], Deepin [Gnome] & Ubuntu these distros are 12.04 & they work just fine.
Am I alone in this dilema????????

After rebooting the router it connected BUT upon selecting install it kicked out.

What ever happened to "It Just Works"
On a lighter side I will bet that the "Amazon Lens" works quite well'

Consider me slightly confused.
bye the bye Xubuntu has the same problem.
Is 13.04 Really ready for release. I ask this only because all 12.04 distros connect propmptly.

---

### Post by cariboo on 2013-04-25
A bump for the move

---

### Post by wildmanne39 on 2013-04-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by pajopet on 2013-04-26
How come all of my 12.04 ubuntu distros work just fine and NONE of the 13.04 distros will connect.Although the 32bit 13.04 fire up on my OLD ASUS 1000he quite quickly?
Is it possible to Just upgrade from 12.04 to 13.04 without loosing the ability to connect?

Wild Man
I really do thank you for the help. But why the lose of consistance? I've beed with Ubuntu from the Drake and thought that we would get past this stuff.

pajo

---

### Post by wildmanne39 on 2013-04-26
Hi, I do not know why.

If you want help we well try to help you if you post the information  asked for.

Upgrading will most likely break wireless.
Thanks

---


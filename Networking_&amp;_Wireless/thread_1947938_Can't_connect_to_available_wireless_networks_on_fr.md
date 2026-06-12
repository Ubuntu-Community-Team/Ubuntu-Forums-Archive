---
title: "Can't connect to available wireless networks on fresh 10.04 install / Dell Mini 10v"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by rainjam on 2012-03-27
I'm trying to connect to wifi on a Dell Mini 10 which used to manage this fine. I lent it to a friend, who used it only as a word processor, but said he couldn't connect either. Now I've got it back (the hardware hasn't changed, he wouldn't have a clue how to!), and in an attempt to sort it out I've done a fresh reinstall of 10.04 from a USB stick. The only thing I've done which isn't "out of the box" is install the Broadcom STA proprietary wireless driver, without which the machine wasn't detecting wifi networks at all.

Now, I get a list of available networks, but I've tried to connect to two different ones and it just won't take the WPA key - as if I'm entering the wrong key. It works fine on a wired connection.

Attached is the output from the various shell commands suggested at [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) (apart from dmesg, which output a 44k file that I couldn't upload). I'm not particularly techy with Ubuntu, so any pointers would be very gratefully received.

---

### Post by rainjam on 2012-03-28
*bump*

anyone?

---

### Post by wildmanne39 on 2012-03-28
Hi, try this please:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
praseodym is correct I did not look all the way to the bottom of the file you posted.

I thought you were using the 2.6.33 kernel and not the 2.6.32 so follow his directions after you get rid of ndiswrapper.
Thanks praseodym

---

### Post by praseodym on 2012-03-28
Hi,

imho this device works with b43 from 11.04 and on. In 10.04 it only works with the Broadcom-STA driver (activate it in "additional drivers"). You should remove ndiswrapper as decribed, though.

---

### Post by rainjam on 2012-03-29
Thanks for the suggestions. Oddly, ndiswrapper didn't seem to be installed (the path in /etc wasn't there, and the previous commands didn't seem to do anything). I've got the proprietary Broadcom STA driver installed as before but unfortunately it still won't connect.

---

### Post by wildmanne39 on 2012-03-29
Hi, try this with your wired connection unplugged:
```
sudo rmmod -f b43
sudo modprobe wl
```
if it does not work then please post the output of the following commands by copying and pasting:
```
ndiswrapper -l
```
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---


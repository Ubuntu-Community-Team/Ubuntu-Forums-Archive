---
title: "Asus G71GX-RX05 from Best Buy and Wifi Atheros Ar928x Wireless N MiniPci Card"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by dzuchowski on 2009-07-31
I just got an Asus G71gx-rx05 from best buy... 

[http://www.bestbuy.com/site/olspage.jsp?skuId=9366615&type=product&id=1218092150740](http://www.bestbuy.com/site/olspage.jsp?skuId=9366615&type=product&id=1218092150740)

It has an Atheros AR928x wifi N card... The card works great ubnder Windows 7 RC beta. When I boot into Ubuntu Live CD the wifi card works just fine. I then installed Ubuntu 9.04 from the live cd, When I rebooted the wireless card would not see any devices. I went to the indianapolis public library also to see if it was my router linux did not like, but same isssue their as well. I need some help in installing this driver. I am new to linux and would love to stick with Ubuntu 9.04 Please provide detailed info if you can thanks. Other then that I love Linux and the compiz stuff....

---

### Post by Crafty Kisses on 2009-08-01
So what you can do here is a couple of things, I'll give you the simplest way. So first you need to grab the driver, you can grab the driver right **[here.]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2")** Before initially compiling the driver you need a couple of things, make sure you have build essential installed, you can do this by running as root:
```
apt-get install build-essential
```
Then you need to extract the driver by running:
```
tar xvf compat-wireless-old.tar.bz2
```
Then you obviously need to go to the wireless directory. So run the following:
```
cd /home/username/Desktop/compat-wireless-old*
```
Remember substitute your own information, and I'm also just assuming you have saved this and extracted this file to your desktop. Then once your in the compat wireless directory, you need to run:
```
make
make install
```
Then you need to load the appropriate module for this card, so run as root:
```
modprobe ath9k
```
Then once you have loaded the module, make sure the module is listed in lsmod, so run the following:
```
lsmod | grep ath
```
That should give you results, if it doesn't you may need to reload the module. Now once you have made sure the module is in place, you now need to run:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
Then see if you can connect. This should work.

---

### Post by dzuchowski on 2009-08-01
> **Codename said:**
> So what you can do here is a couple of things, I'll give you the simplest way. So first you need to grab the driver, you can grab the driver right **[here.]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2")** Before initially compiling the driver you need a couple of things, make sure you have build essential installed, you can do this by running as root:
```
apt-get install build-essential
```
Then you need to extract the driver by running:
```
tar xvf compat-wireless-old.tar.bz2
```
Then you obviously need to go to the wireless directory. So run the following:
```
cd /home/username/Desktop/compat-wireless-old*
```
Remember substitute your own information, and I'm also just assuming you have saved this and extracted this file to your desktop. Then once your in the compat wireless directory, you need to run:
```
make
make install
```
Then you need to load the appropriate module for this card, so run as root:
```
modprobe ath9k
```
Then once you have loaded the module, make sure the module is listed in lsmod, so run the following:
```
lsmod | grep ath
```
That should give you results, if it doesn't you may need to reload the module. Now once you have made sure the module is in place, you now need to run:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
Then see if you can connect. This should work.
 
 
how do i know if i am running as root? I will try this in a little bit. in process of moving today..

---

### Post by dzuchowski on 2009-08-01
> **Codename said:**
> So what you can do here is a couple of things, I'll give you the simplest way. So first you need to grab the driver, you can grab the driver right **[here.]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2")** Before initially compiling the driver you need a couple of things, make sure you have build essential installed, you can do this by running as root:
```
apt-get install build-essential
```Then you need to extract the driver by running:
```
tar xvf compat-wireless-old.tar.bz2
```Then you obviously need to go to the wireless directory. So run the following:
```
cd /home/username/Desktop/compat-wireless-old*
```Remember substitute your own information, and I'm also just assuming you have saved this and extracted this file to your desktop. Then once your in the compat wireless directory, you need to run:
```
make
make install
```Then you need to load the appropriate module for this card, so run as root:
```
modprobe ath9k
```Then once you have loaded the module, make sure the module is listed in lsmod, so run the following:
```
lsmod | grep ath
```That should give you results, if it doesn't you may need to reload the module. Now once you have made sure the module is in place, you now need to run:
```
ifconfig wlan0 down
ifconfig wlan0 up
```Then see if you can connect. This should work.


when i do the make it tells me it is for a different kernal I have  2.6.28-15 generic.
You should use another tree/tarball for newer kernels  this one is for kenrels <= 2.6.26"

---

### Post by Crafty Kisses on 2009-08-01
I'm not sure what kernel you had, I should have asked, I guessed you had an older kernel, what are the results of the following command?
```
uname -r
```
Now you need to read **[this. ]("http://linuxwireless.org/en/users/Download")** Then follow my steps again. You then obviously need to extract the tarball by runnung:
```
tar jxvf compat-wireless-$(version).tar.bz2
```
Then run **make**, then run as root:
```
make install
```
Then remember to load the ath9k module, run as root:
```
modprobe ath9k
```
You also asked how do you know if you are root? You can put "sudo" in front of the commands you want to run as root, so for example, if I wanted to run Firefox regularly, I would just run:
```
firefox
```
Now if I wanted to run Firefox as root, I would run:
```
sudo firefox
```
You might want to read **[this]("https://help.ubuntu.com/community/RootSudo")** for more information. You also should read this page about "ath9k" on Linux Wireless, so read **[this]("http://linuxwireless.org/en/users/Drivers/ath9k")**.

---

### Post by dardack on 2009-08-01
I have the same issue.  The card is detected and that module is loaded, however it will not scan and find any access points.  I've followed what you put no change at all.

UPDATE:  I found the fix. Apparently the bluetooth and wifi reside on same chip and can't function at same time so in /etc/rc.local right before exit 0 put in the following:

echo 0 > /sys/devices/platform/asus-laptop/bluetooth # disable bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan # enable wireless

Sorry had like 200 tabs opened and couldn't find who to give credit to.  Whoever you are thanks.

---

### Post by dzuchowski on 2009-08-02
> **dardack said:**
> I have the same issue.  The card is detected and that module is loaded, however it will not scan and find any access points.  I've followed what you put no change at all.

UPDATE:  I found the fix. Apparently the bluetooth and wifi reside on same chip and can't function at same time so in /etc/rc.local right before exit 0 put in the following:

echo 0 > /sys/devices/platform/asus-laptop/bluetooth # disable bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan # enable wireless

Sorry had like 200 tabs opened and couldn't find who to give credit to.  Whoever you are thanks.

thanks How can I edit that file as it wont let me save it....

---

### Post by dardack on 2009-08-02
You have to sudo nano /etc/rc.local
or some variation, you need to be root to edit this file.

---

### Post by dzuchowski on 2009-08-21
> **dardack said:**
> You have to sudo nano /etc/rc.local
or some variation, you need to be root to edit this file.

i have upgraded the wifi to intel 5300 which support dual band 2.4 and 5.0 ghz radios....  d
did clean install and when i click on the icon to connect to wireless access their is none not enabled..... are their new drivers? i updated to 9.1 beta update thru live update//// still not working... clean install with 9.01 again and still nothing.

---

### Post by kingnate on 2009-10-01
Thanks Dardack __ for finding that, saved me a bunch of trouble as i just bought this laptop.

---


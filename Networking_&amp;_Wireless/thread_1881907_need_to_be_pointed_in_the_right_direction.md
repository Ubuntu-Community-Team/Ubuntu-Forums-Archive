---
title: "need to be pointed in the right direction"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by aydinahmed on 2011-11-16
I recently installed Ubuntu as a dual os with xp. My wireless doesn't work and I have read exhaustively about the subject. I have a Broadcom bcm4311 with a vendor id of 14e4:4312.  I've downloaded ndiswrapper from my cell, since I have no internet connection, and transfered the file to Ubuntu desktop. How do I unzip and install this??? Also, after about 15 min of use, I freeze, everytime. How can I access a log of some sort or does anyone have suggestions on how to fix. After reading, I suspect I need to update my kernal......I've downloaded linux headers, image and i386, they are all deb files, which I believe is the update, how do I install this??
Thank you

---

### Post by praseodym on 2011-11-16
Hi, and welcome.

You dont need ndiswrapper for this device, so you can remove it safely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
The driver b43 for this device only needs the firmware installed (attached). Save the "tar.gz" to "Downloads" and unpack it via:
```
sudo tar xvf ~/Downloads/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by aydinahmed on 2011-11-21
It gives me the response: you may not specify more than one - acrylic or --test-label????  
Thank you for your help by the way

---

### Post by praseodym on 2011-11-21
Did you copy/paste those command lines?

---

### Post by aydinahmed on 2011-12-09
No I didnt

---

### Post by praseodym on 2011-12-09
copy/paste all of these commands one by one into the terminal

---

### Post by aydinahmed on 2011-12-13
OK copied and pasted, and it lists all the files that was in the tar. Brings me to ubuntu@ubuntu:~$  . Now what?

---

### Post by praseodym on 2011-12-13
Reboot or:

```
sudo service network-manager stop
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manager start
```

---

### Post by aydinahmed on 2011-12-13
You are a beautiful person. Thank you works great.

---

### Post by aydinahmed on 2011-12-13
Oops on reboot it doesn't work

---

### Post by praseodym on 2011-12-13
Check

```
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | grep b43
```

---

### Post by aydinahmed on 2011-12-14
When I look at additional drivers broadcom start wireless driver is activated but nit currently in use???????

---

### Post by praseodym on 2011-12-14
Uninstall the STA driver after you deactivated it:

```
sudo modprobe -rfv wl b43
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -v b43
sudo service network-manager restart
```

---


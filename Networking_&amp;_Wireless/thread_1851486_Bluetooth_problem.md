---
title: "Bluetooth problem"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by rastamankg on 2011-09-28
Hi, I have a problem with sending files from my notebook to other devices via bluetooth. I managed to connect to my cell phone, but I can't send files. It just says 'Permission denied (13)'. Probably it will work with sudo, but I don't know how to open bluetooth from terminal. I have Ubuntu 11.10

---

### Post by khelben1979 on 2011-09-28
I can send files from my PC to my mobile phone over here using bluetooth, and I'm using the [Bluetooth Applet]("http://library.gnome.org/users/gnome-bluetooth/stable/gnome-bluetooth-applet.html.en"), maybe it isn't installed? (also I'm using D-Link USB adapter)

Make sure to use the same password for the mobile phone as on the Linux desktop, otherwise they will not be able to sync.

---

### Post by rastamankg on 2011-09-28
I have sent some files to another cell phone. Now, I think that the problem is in my cellphone, rather than in Ubuntu. My phone is Samsung S5260, so if someone has similar problem, please post the solution.

I have built-in bluetooth device in my Fujitsu Siemens V6545.

Thank you

---

### Post by FOSScula on 2012-03-19
same problem here.. 64bit ubuntu 11.10  can send files TO our phone (optimus V) but CANNOT receive files from PC. something about "Permission Denied(13)"  check in /var/log/messages and there is nothing..  opened "Personal File Sharing" in dash and said packages were missing... so ... installed "libapache2-mod-dnssd" and "apache2.2-bin" (thanks google)  now i can use the Personal file sharing application- no missing packages-  same problem occurs though... cant recieve files from pc to phone... ONLY from phone to pc.](*,)

---

### Post by FOSScula on 2012-03-20
[SOLVED] recieve files to/from android phone ubuntu 11.10 We were trying to connect our phones (android optimus V & HTC glacier) to/from ubuntu 11.10  first couldnt send or recieve via bluetooth with our android phones. Checked in  "personal file sharing" application.  It said there are missing packages...(the accompanying popup never said WHICH ones were missing?? just that SOME were)  installed these 2 packages >   (thank you Seapaladin! [http://ubuntuforums.org/showthread.php?t=1861725&page=4](http://ubuntuforums.org/showthread.php?t=1861725&page=4)) ```
sudo apt-get install libapache2-mod-dnssd
```* & *```
sudo apt-get install apache2.2-bin
```  mod4-win key (personal file sharing) can now use "personal file sharing" application.  ok now we can send files from our phone to pc everytime..=D> still CANNOT send files from PC to phone.  ...next... > (thanks vangop! [http://ubuntu-answers.blogspot.com/2011/11/bluetooth-on-ubuntu-1110.html](http://ubuntu-answers.blogspot.com/2011/11/bluetooth-on-ubuntu-1110.html)) ```
sudo apt-get install obexfs
```  ran ```
hcitool scan
``` from terminal. came up with NOTHING.. set our phone to 'discoverable' and ran it again.. ```
hcitool scan
``` scan found device and mac address!!=D>=D> created directory for mountpoint in /home/Public/ folder  called *phone1* ran ```
 obexfs -b MACaddress  /mountpoint/
```  Can now send files to/from pc to our android phones (optimus V & HTC glacier mytouch 4g)  and  browse phones sd card thru nautlius/thunar @ its mountpoint!!=D>=D>=D>   of course replace above MAC address with the one that would appear in *hcitool scan* and the mountpoint to folder you designate.. ie for us it looks like ```
obexfs -b 8F:72:11:77:45:16  /home/FOSScula/Public/phone1/
```

---


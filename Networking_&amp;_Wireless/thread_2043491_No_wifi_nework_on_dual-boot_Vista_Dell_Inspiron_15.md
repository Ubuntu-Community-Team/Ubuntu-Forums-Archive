---
title: "No wifi nework on dual-boot Vista Dell Inspiron 1501"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by ljmartz on 2012-08-16
> If you'd like to get your Broadcom working, please post a new thread including:     Code:
     lspci -nn | grep 0280 rfkill list all dmesg | grep b43 
I'll be happy to help.As Per your request, new thread started.

---

### Post by wildmanne39 on 2012-08-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by ljmartz on 2012-08-16
> It will download a script and create a text file in your home folder  with wireless information so we can see the condition of your wireless  at this time and the Mac address, WPA key and WEP key are removed for  your security,  then reply back  and attach the netinfo.txt file.
Thanks     Netinfo.txt file is attached.

---

### Post by wildmanne39 on 2012-08-16
Hi, click on the paper clip in the reply window then find the file and click upload and wait for the upload to complete.
Thanks

---

### Post by ljmartz on 2012-08-16
> Hi, click on the paper clip in the reply window then find the file and click upload and wait for the upload to complete.
Thanks

Sorry about that, this time the file loaded.

---

### Post by wildmanne39 on 2012-08-16
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install --reinstall linux-firmware-nonfree
```
Reboot
Thanks

---

### Post by ljmartz on 2012-08-16
> Hi, please do:
 	Code:
 	sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source


Answered yes to query to remove file.

> Then:
 	Code:
 	sudo apt-get install --reinstall linux-firmware-nonfree 
Reboot
Thanks 	

Rebooted and now I'm back.  I do have a wifi light on my laptop (something I did not have before).  Should I now disconnect ethernet and try to connect via WIFI?

---

### Post by wildmanne39 on 2012-08-16
Hi, yes! go to the right top of the screen and click on network icon and make sure enable wireless is checked you should see your network listed and be asked for a password if not reboot one more time.
Thanks

---

### Post by ljmartz on 2012-08-16
> Hi, yes! go to the right top of the screen and click on network icon and  make sure enable wireless is checked you should see your network list  and be asked for a password if not reboot one more time.
Thanks 	

Thank YOU!!!!!  After 4 days of drain bramage I finally have Ubuntu installed and my WIFi connection functioning on my laptop (this post sent from my laptop using my WIFI connection).:p:p:p

---

### Post by wildmanne39 on 2012-08-16
Your welcome!
Enjoy

---


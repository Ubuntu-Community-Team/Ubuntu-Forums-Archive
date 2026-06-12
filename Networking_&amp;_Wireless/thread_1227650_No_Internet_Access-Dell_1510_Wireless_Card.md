---
title: "No Internet Access-Dell 1510 Wireless Card"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Darren5531 on 2009-07-30
As of about 10:00 this morning I am a first time Linux user and I am having a little trouble getting my wireless to access the internet in 64-bit Ubuntu. The terminal is the only thing I have open. I can connect to my home wireless -802.11 G but when I try to access the internet it fails.

I have the Dell 1510 wireless N card in a Dell Latitude E4300.

I have searched around for the last couple hours and found some good information here:

[http://ubuntuforums.org/showthread.php?t=857532](http://ubuntuforums.org/showthread.php?t=857532)

I have tried installing the drives from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I followed the text file but I keep getting permission denied when I try to un-tar the folder. 

I checked the settings for the folder and I have read write access to the folder. 

When I go to hardware drivers it shows that I am using: Broadcom STA wireless driver.

Any suggestions?

Thanks for your time,

Darren

---

### Post by philcamlin on 2009-07-30
tar xvfz file.tar.gz
cd file_dir/
./configure
make
su -c "make install" (enter root password here)

try that :D

---

### Post by Darren5531 on 2009-07-30
I am pretty much a complete noob when it comes to this. Do I just type each line in the terminal and then hit enter? I tried doing that but it said that there wasn't a file named that. 
 
Thanks for the reply

---


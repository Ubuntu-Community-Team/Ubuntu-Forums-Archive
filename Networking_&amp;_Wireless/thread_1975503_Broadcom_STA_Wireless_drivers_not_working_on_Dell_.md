---
title: "Broadcom STA Wireless drivers not working on Dell Inspirion 1501, Ubuntu 12.04"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by JRod13 on 2012-05-07
When I go into the additional drivers section of system settings, i click activate and I receive the following error: 
 
"Sorry, installation of this driver failed.
 
Please have a look at the log file for details: /var/log/jockey.log"
 
Here is some info from *lspci -nn | grep 0280:*
 
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 
Thanks for the help....

---

### Post by praseodym on 2012-05-07
Hi,

you only need the firmware for the b43 driver for this device:
```

wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

### Post by chili555 on 2012-05-07
Please temporarily hook up the ethernet temporarily and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet. Now is it working?

---

### Post by JRod13 on 2012-05-07
Thanks for the repsonses, folks. 
 
I hooked up the ethernet but my connection toggles on/off. It says when it's on that it's running at 100 mbits/s but yet I am unable to load web pages?....

---

### Post by chili555 on 2012-05-07
You didn't say you also have a wired ethernet problem. Sorry, only one problem per customer per day.

Just kidding! With the ethernet connected, please run and post:```
dmesg | grep eth
ifconfig
```Thanks.

---

### Post by JRod13 on 2012-05-07
> **chili555 said:**
> You didn't say you also have a wired ethernet problem. Sorry, only one problem per customer per day.
 
Just kidding! With the ethernet connected, please run and post:```
dmesg | grep eth
ifconfig
```Thanks.
 
 
Haha! I actually got it working. 
 
I ran the following command:
 
sudo dpkg --configure -a

and the ethernet had a continuous connection. I then ran the commands in your previous post and got the wireless working too!
 
Thanks for your help!

---

### Post by chili555 on 2012-05-07
Excellent! Glad it's working. Please use thread tools at the top to Mark Solved.

---

### Post by dvdivx on 2012-05-07
Exact same problem here with more useless apt-get solutions. This really needs an OFFLINE solution since if the computer has no internet connection it's not going to apt-get anything.

---

### Post by chili555 on 2012-05-07
> Exact same problem here with more useless apt-get solutions.Mind if we check first? Please run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.> This really needs an OFFLINE solutionI probably have one! I don't usually propose it at the start for a laptop because the user can almost always walk over to the router and hook up.> Broadcom STA Wireless drivers not working on *Dell Inspirion 1501*

---

### Post by JRod13 on 2012-05-07
> **chili555 said:**
> Excellent! Glad it's working. Please use thread tools at the top to Mark Solved.
 
 
Done!

---

### Post by monkeysNmidgets on 2012-05-07
Chili555...  Right on with the "sudo apt-get..." instructions.  Thanks a bunch!
 
It's an interesting problem, though.  If I read the instructions right, we're downloading a small package, removing the b43 driver, and then re-adding the b43 driver.
 
To the point of someone else asking for an offline fix, could we have remove/re-add the b43 driver without the download?  Or did the Broadcom code need changing for U12.04?
 
Curiously yours...  (as my wiress is up!)

---

### Post by chili555 on 2012-05-07
The driver b43 requires firmware which is proprietary so it's not included by default in the free and open source Ubuntu install. We install the *non*free firmware package; then we unload the driver and reload it so it sees and grabs the shiny new firmware.

The offline approach usually involves me attaching a zipped firmware file to my reply, and a USB stick so it can be transferred to the internet-less computer and installed in the correct spot so the b43 driver finds it as expected. As I said, I don't usually start there, but it's an available option if needed.

---

### Post by jeb99 on 2012-09-16
> **chili555 said:**
> Please temporarily hook up the ethernet temporarily and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet. Now is it working?

This fix works perfectly for me as well (same hardware as the original poster). However, do you expect to have to do this each time you start the computer? Is there a permanent solution?

Thanks.

---

### Post by chili555 on 2012-09-16
> However, do you expect to have to do this each time you start the computer? Is there a permanent solution?Usually there is! Please try:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot. Is it working now?

---

### Post by jeb99 on 2012-09-17
> **chili555 said:**
> Usually there is! Please try:```
sudo su
echo b43 >> /etc/modules
exit
```Reboot. Is it working now?

Yes! Nice one, thanks a lot!

---

### Post by StinkySQL on 2012-09-21
Thanks Chili555 - I'm also up and running with no issues now, and I've only been on a Linux system for two days. Kinda feel in control again ;)

---

### Post by chili555 on 2012-09-21
> **StinkySQL said:**
> Thanks Chili555 - I'm also up and running with no issues now, and I've only been on a Linux system for two days. Kinda feel in control again ;)Awesome! Glad it's working. Welcome to the fascinating world of Linux.

---

### Post by cmcglath on 2012-09-24
> **chili555 said:**
> Please temporarily hook up the ethernet temporarily and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet. Now is it working?

This also fixed my problem & I really appreciate your help.

---

### Post by darksign13 on 2012-10-08
>                                                       This really needs an OFFLINE solution                                 
I probably have one! I don't usually propose it at the start for a  laptop because the user can almost always walk over to the router and  hook up.
I really, really need the off-line solution. I don't have the Internet at my house so I can only use the wifi connection at the public library. And since there is no Ethernet connections available there, I'm kind of hosed unless I can use the off-line way.

---

### Post by bkratz on 2012-10-08
> **darksign13 said:**
> I really, really need the off-line solution. I don't have the Internet at my house so I can only use the wifi connection at the public library. And since there is no Ethernet connections available there, I'm kind of hosed unless I can use the off-line way.




The b43 offline solution can be found in this posting.

[http://ubuntuforums.org/showpost.php?p=12284541&postcount=12](http://ubuntuforums.org/showpost.php?p=12284541&postcount=12)

---

### Post by fastbeagle on 2013-02-03
Thanks. Works great.

---

### Post by Affu on 2013-08-28
> **chili555 said:**
> Please temporarily hook up the ethernet temporarily and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```Detach the ethernet. Now is it working?


Thanks a lot!!! This worked for me :p

My laptop model - Dell Inspiron 1545.

---


---
title: "Broadcom 4318 Chipset issue with-in UE 2.8"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by ichase on 2010-12-22
I know there has been a million and one posts about the broadcom issue and I can assure you, I believe I have read about 80% of them. I was really hoping to find the solution with out having to submit yet another post on this subject. :)
 
Here is what I have as far as hardware goes:
Compaq Presario V2000
- PROCESSOR: Intel Pentium M 710 -- 1.4 GHz 
- RAM 2 GB
- HD 80 GIG
- Duel booting XP Pro with Ultimate Edition 2.8(I understand this is built from Ubuntu 10.10...Correct me if I am wrong)
- lspci -vnn | grep 14e4 yeilds the following:
```
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
 
I have followed to the tee this guidance: [https://help.ubuntu.com/community/WifiDocs/...ver/bcm43xx#b43 ]("https://help.ubuntu.com/community/WifiDocs/...ver/bcm43xx#b43")
 
I tried the installing b43 drivers with internet (using ethernet)
I tried installing off the DVD using the no internet option
I even tried installing the STA drivers even though I know the 4318 chipset is not mentioned as a supported chipset. (I read where someone had luck with this)
 
All of these were loaded/extracted with no errors via terminal following the guidance to the letter.
 
Now here is a problem I have not read that anyone else has run into. (maybe I just missed it)
When I go: System > Administration > Additional Drivers the only additional driver that shows up is "Software Modem"
 
I can't for the life of me figure out why the b43 and STA drivers are not showing up to activate. I can install drivers all day long, if I can't activate them, it really does become a moot point.
 
Thank you in advance for all of you that take the time to respond.
 
I wish you all the happiest of holidays and a great 2011!!!!:p
 
All the best,
 
Ian

---

### Post by chili555 on 2010-12-22
> I can't for the life of me figure out why the b43 and STA drivers are not showing up to activate. Maybe they do not show up as available to activate because they are already activated. Please post:```
sudo modprobe b43
rfkill list all
dmesg | grep b43
```Thanks.

---

### Post by ichase on 2010-12-22
Not sure what I did, but when I typed ```
Sudo modprobe b43
``` at first nothing happened, then a window popped up stating I was connected to my network.  I had previously went into Network settings typed in the SSID and the password for the network and had no such luck.  I logged in this evening, still no wireless then alas when I typed in the above I had wireless.
I was then prompted to install the b43 proprietary driver.  I now have 87% signal and it's working great as I am typing this.  Keeping fingers crossed that when I re-boot, I still have it.
I do wish I could put step by step procedures as to what I did, but I tried so many different things I am not sure exactly what fixed the issue. :popcorn:

All the best,

Ian

---

### Post by ichase on 2010-12-23
After doing further research, I seem to know what the problem was and hopefully others with similar issues can fix their own wireless broadcom issues.
 
As mentioned in the OP, I followed the guidance to the letter on downloading the firmware/drivers.  One major thing I did not do was "LOAD" the drivers.
 
That is where the
```
sudo modprobe b43
```
Came in.  Thanks again for that one chili555
 
This manually loaded the b43 driver which in turn provided me with my wireless connection.
 
Now, when you re-boot you may notice as I did that you once again do not have wireless.  By manually loading the driver:  sudo modprobe b43, you will then have your wireless back.  
 
Now, I would like not to have to manually load these everytime I log in.  So here is what I am going to do.
I am going to edit my /etc/modules file and add b43 on the last next available line.  Nothing else just b43.  This "SHOULD" in theory automatically load the driver upon boot.  I will be trying this; this evening.  Keep you posted.
 
All the best,
 
Ian

---

### Post by chili555 on 2010-12-23
> This "SHOULD" in theory automatically load the driver upon boot.And by SHOULD, we mean WILL. Post back if it doesn't work as expected.

---

### Post by ichase on 2010-12-23
Chili,
It worked like a champ.
```
 sudo gedit /etc/modules
```

You should see something like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
[COLOR=Red]b43[/COLOR] <----Add this here under all kernel modules listed.  

```

This will ensure that the b43 driver is automatically started upon boot-up so that you don't have to manually start it each time.  :)

Hopefully someone else can get their WiFi up and running using this.  :)

Thanks again chili,

Ian

---


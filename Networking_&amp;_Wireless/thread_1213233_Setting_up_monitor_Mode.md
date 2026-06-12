---
title: "Setting up monitor Mode"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by cactuska on 2009-07-14
Hi Guys,

i have a special problem. I use Ubuntu 9.4, and Asus wl-167g wireless adapter.

I try to turn my adapter into Monitor mode, but if i type iwconig wlan0 mode monitor, it replys error (8B06), says its busy. I googled it, but i cant solve it.

Thanx for your help

cactuska

---

### Post by chili555 on 2009-07-14
You probably need to take the interface down first and use sudo:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Please let us know.

---

### Post by cactuska on 2009-07-15
hi Chili555,

you have solved my problem, thanx for that, im a newbie...

But i have an other, when i set my adapter to monitor mode, iwlist says its in monitor mode, and i try to run airodump, it replys an error "Unsupported hardware linktype 803  - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'

Could you please help again to solve this issue as well?

Regards,
cactuska

---

### Post by cactuska on 2009-07-16
up

---

### Post by chili555 on 2009-07-16
> Could you please help again to solve this issue as well?Sorry, I know very little about airodump and RFMON. Hopefully, someone else will jump in here.

---

### Post by cactuska on 2009-07-16
Can someone help me to solve this problem?

---

### Post by cactuska on 2009-07-21
Please help, it is so important

thx

---

### Post by SteveONCSU on 2009-08-25
> **chili555 said:**
> You probably need to take the interface down first and use sudo:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```Please let us know.
I tried this but my network manager tries to bring it back up again.  How do I prevent this??

---

### Post by SteveONCSU on 2009-08-25
Nevermind, I don't need to know this anymore.  Kismet disables the network manager now.

---

### Post by snarehead on 2009-12-08
> **cactuska said:**
> Can someone help me to solve this problem?
 
Hi there
to solve this issue you need to download the latest version of aircrack. the version they have in apt-get is outdated and is bugged! this is how you do it.
Load up your terminal
 
_first you need the build essential's_
 
1. sudo apt-get install build-essential
 
_Then you need OpenSSL (development). It is called openssl-dev or libssl-dev depending on your distribution._
 
2. sudo apt-get install libssl-dev
 
_Then install aircrack repeat below_
 
3. sudo wget [http://download.aircrack-ng.org/aircrack-ng-1.0.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.0.tar.gz)
    
    tar -zxvf aircrack-ng-1.0.tar.gz
 
    cd aircrack-ng-1.0
 
    sudo make
 
    sudo make install
 
_Done!_

---


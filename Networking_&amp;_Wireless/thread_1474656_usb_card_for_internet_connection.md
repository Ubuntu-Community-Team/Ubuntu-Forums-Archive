---
title: "usb card for internet connection"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by hannajabali on 2010-05-06
I have a system with windows xp, and to connect to internet I use a usb card EVDO (brand ZTE) given by my provider (BSNL India).
Now I installed ubuntu 10:04 but I do not know how to make my usb card work to connect to internet (the provider gave the software only for win xp)

---

### Post by dineshs on 2010-05-06
pl post the output of ```
lsusb
```
pl see this
[http://ubuntuforums.org/showthread.php?p=9241304#post9241304](http://ubuntuforums.org/showthread.php?p=9241304#post9241304)

---

### Post by hannajabali on 2010-05-07
oreste@oreste-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 19d2:fffe ONDA Communication S.p.A. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0d49:7450 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by hannajabali on 2010-05-07
I had a look at the other post but no help
the maxtor device on the 7th line is the external harddisk on which my ubuntu is installed. the ZTE card should be the on on the 3rd line

---

### Post by dineshs on 2010-05-07
[http://www.karthikeyanc.com/blog/](http://www.karthikeyanc.com/blog/)
w.r.t the above site I suggest the following(Because you may not have wvdial installed)
First run ```
sudo modprobe usbserial vendor=0×19d2 product=0xfffe
```
Now run ```
sudo pppconfig
```
After configuring,post the output of
```
gksudo gedit /etc/ppp/peers/provider
```
You can try connecting using ```
pon provider
```

---

### Post by hannajabali on 2010-05-07
I followed the instructions.
When doing the pppconfig he was asking me to choose the port to which connected, but there was no port indicated. I chose " do it manually, and while he was suggesting /dev/ttyS1 I put instead /dev/ttyusb2.
Then I did the gedit and here is the result:

hide-password
noauth
connect  "/usr/sbin/chat -v -f  /etc/chatscripts/provider"
debug
/dev/ttyusb2
115200
defaultroute
noipdefault
user "47420909656"
remotename provider
ipparam provider

usepeerdns


Then I did the pon provider and it answered that he could not recognize /dev/ttyusb2
I changed it into ttyusb0 or ttyusb4, but same result. I tried ttyS1 and at this time the pon provider seemed to work but when I tried any internet program the answer was there is no network connection. When I did poff he said that there was no ppp connected.

Would wvdial work? in ubuntu 8:04 I used it for a slow cdma connection but this is a edvo which should be a mobile broadband.

---

### Post by hannajabali on 2010-05-07
by the way... I am in Kerala too and mine is a BSNL connection  and the usb card is ev-do AC8700 800M

---

### Post by dineshs on 2010-05-07
> **hannajabali said:**
> 
I tried ttyS1 and at this time the pon provider seemed to work but when I tried any internet program the answer was there is no network connection. When I did poff he said that there was no ppp connected.

Would wvdial work? in ubuntu 8:04 I used it for a slow cdma connection but this is a edvo which should be a mobile broadband.

1.pl post the output of
```
 dmesg | grep -e "modem" -e "tty"
```
2.You can try wvdial or gnome-ppp
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
gnome-ppp has the option to autodetect modem under setup
wvdial can do this via wvdialconf

Note You should try ttyUSB0,ttyUSB1 etc and not ttyusb0,ttyusb1 etc.Means try uppercase

---

### Post by hannajabali on 2010-05-08
I tried changing ttyUSB0 using the capital letters, at this point doing pon is accepted but nothing happens and no internet program works.
using wvdial he recognises it as ttyUSB0 analogic modem, but when trying to connect he gives error saying that maybe username or password be wrong. Of course are right since are given by the provider and work fine in Windows.
I even found a dialler for ubuntu 8.04 for the card, but when I try installing it it gives error (it is a packet .deb and I install it clicking on it, process starts but after a while it gives the error)

ecco il risultato di dmesg
oreste@oreste-desktop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[   24.320857] USB Serial support registered for GSM modem (1-port)
[   24.321347] option 4-1:1.0: GSM modem (1-port) converter detected
[   24.322314] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[   24.322349] option 4-1:1.1: GSM modem (1-port) converter detected
[   24.323247] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[   24.323280] option 4-1:1.2: GSM modem (1-port) converter detected
[   24.323428] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[   24.323460] option 4-1:1.3: GSM modem (1-port) converter detected
[   24.323774] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB3
[   24.323798] option: v0.7.2:USB Driver for GSM modems

---

### Post by pdc on 2010-05-08
you could try using 

> ttyUSB2

instead of ttyUSB0 in the wvdial script

it has worked for others

---

### Post by hannajabali on 2010-05-09
no results

---

### Post by dineshs on 2010-05-09
> **hannajabali said:**
> I tried changing ttyUSB0 using the capital letters, at this point doing pon is accepted but nothing happens and no internet program works.

You mean connected ?Then pl try this on a terminal and post the result after connecting
```
ping 4.2.2.1 -c5
```
BTW did you try to install gnome-ppp?

---

### Post by dineshs on 2010-05-10
> **hannajabali said:**
> 
using wvdial he recognises it as ttyUSB0 analogic modem, but when trying to connect he gives error saying that maybe username or password be wrong. Of course are right since are given by the provider and work fine in Windows.

Your tel no cannot have 8 digits.I think your username is wrong.
> user "47420909656"

---


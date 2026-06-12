---
title: "How to get  WPC54G ver 3.1 to work in natty"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by jordie9 on 2011-08-04
I have an old ibm thinkpad R40. I did a fresh install of natty. Cannot get wireless or wired to work. I just want the wireless to work first if possible. So I have no Internet access. Can't upgrade etc. I am a noob and need to be hand held and walked through process. Thanx for any and all help.

J

---

### Post by chili555 on 2011-08-04
Mr. HandHold is right here. Please open the terminal on that old R40 and run and post:```
lspci -nn | grep 0280
```Doesn't your R40 have an internal wireless card?

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by jordie9 on 2011-08-04
Well thanx Mr. HH lol 

03:00.0 Network controller [0280] : Broadcom Corp BCM4318 [Airforce One 54g] 802.11g Wireless LAN  Controller [14e4:4318] (rev 02)

The 0280 above is in red.

Jordie

---

### Post by chili555 on 2011-08-04
Here is a file that you can download to any computer. Transfer it on a USB key or similar and drag and drop it to the desktop. Right-click it and select Extract Here. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Your wireless should now be working.

---

### Post by jordie9 on 2011-08-04
Walked over plugged in cable... says you are now disconnected from internet. Eth0 not working.

---

### Post by chili555 on 2011-08-04
I edited my post. Please read again.

---

### Post by jordie9 on 2011-08-04
After sudo rmmod -f b43 

I get "no file or directory " But when I try sudo mkdir /lib/firmware/b43 again I get : file exists

---

### Post by chili555 on 2011-08-04
So did you go ahead and move the files over from your desktop?

---

### Post by jordie9 on 2011-08-04
I did the sudo modeprobe b43 thing and I have Internet access.  Thanx, thanx,thanx. Got a chill up my leg when the applet started working. Many many thanx Chili. You are very helpful and kind. Makes me wanna learn this to help others! And I will! thanx again

Jordie

---

### Post by chili555 on 2011-08-04
Awesome, sir. Would you please use thread tools at the top and Mark Solved?

---

### Post by jordie9 on 2011-08-04
Do I have to put in modprobe b43 every time I start? Upon restart it did not come on automatically. Tho that is checked in wireless box.

---

### Post by nm_geo on 2011-08-04
> **jordie9 said:**
> Do I have to put in modprobe b43 every time I start? Upon restart it did not come on automatically. Tho that is checked in wireless box.

chili is detained 

try this

```
sudo su 
echo b43 >> /etc/modules 
exit
```Three separate lines ..
He taught me that :P

---

### Post by jordie9 on 2011-08-05
And you are a great student. It worked! thanx mucho. And I hope Chili is "released" soon. Thanx all!

---


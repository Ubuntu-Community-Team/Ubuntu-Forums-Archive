---
title: "n00b asking for help auditing own network."
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by fozbolt on 2009-08-09
ok so im a noob to linux and this is kinda hard but maybe you guys can help me out. im running ubuntu 9.04 on my new macbook that is partitioned and im running OSX on the other partition. im trying to audit my home network but im running into some hardcore obstacles. one thing im not sure if its a problem or not is that my wifi card is set to the eth1 port(again not sure if thats a problem or not). also whenever i go to run the program aireplay to perform a packet injection test it gives me this-

socket(PF_PACKET) failed: Operation not permitted
This program requires root privileges.

when i go to try and set my card in monitor mode i get this response-

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.

can someone tell me how i can give myself root priveliges. i also cant really tell if i need to patch my drivers or get updated drivers for my card to support the packet injection.

---

### Post by philcamlin on 2009-08-09
sudo is root 
so id i want to run something as root liek updates or something i would type

sudo apt-get update
if i type 
apt-get update it will yell at you saying its not root 

so try running whatever your doing with sudo in front
if its an application go into terminal and type 
sudo *name of program goes here*
it will then ask you for your password. type it in and then your running root

after you are root privelages you can then do what you want !

---

### Post by MadHatter21 on 2009-08-09
If you tell us what it is you are trying to do then we might be able to help more. If you are trying to get into monitor mode then airmon-ng might help a little by doing,
```
sudo airmon-ng start wlan0
```

This should start into monitor mode as the same interface name(wlan0) or something else like mon0 ath0 etc.

Good luck,
MadHatter21

---

### Post by fozbolt on 2009-08-09
ahhhh thanks guys. :) keep a look out though ill prolly be making another post here in a few minutes.

---


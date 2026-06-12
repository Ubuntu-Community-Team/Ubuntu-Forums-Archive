---
title: "broadcom WiFi card with scizofrenia"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by brujoand on 2006-05-11
I have a dell inspiron 5150 with 3,06ghz intel P4 and a broadcom BCM4306 wireless. Im running ubuntu 5.10. I've installed the windows driver with ndiswrapper and ndiswrapper says that the hardware is present. But when running iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

In other words, the wireless card isnt found.. I hate broadcom and all but this is just lame, and im not even shure its broadcoms fault..  Anybody who knows whats wrong or how I can fix it? 
Please help me! :)

tnx

---

### Post by kb3hkg on 2006-05-11
There seem to be lots of issues with Broadcom within linux, especially on dell systems. I have yet to get mine working either and am currently stuck in the same place you are with it. I have yet to see a solution for this.

---

### Post by towsonu2003 on 2006-05-11
try other drivers- they are listed in the ndiswrapper web site.

---

### Post by deathbyswiftwind on 2006-05-11
I have the broadcom 4306 and it wasnt bad to get it setup. Id recommend switching to dapper and then the setup of it is alot easier. In dapper all you have to do is blacklist the linux driver and then install the new one with breezy I had to do everything on this page [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=howto+broadcom]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=howto+broadcom")

I dunno dapper is official in a month anyways.

---

### Post by brujoand on 2006-05-15
the howto got me closer. Ndiswrapper recogninses my hardware, but iwconfig says the the are no wireless extensions. and wlan0 does not appear in the network connections window. Do I need to activate my card in any way? I suspect that it is fond by ndiswrapper, but not by iwconfig because it has status off. Any body? help please:)

---

### Post by towsonu2003 on 2006-05-15
[QUOTE=GrimmVarg]the howto got me closer. Ndiswrapper recogninses my hardware, but iwconfig says the the are no wireless extensions. and wlan0 does not appear in the network connections window. Do I need to activate my card in any way? I suspect that it is fond by ndiswrapper, but not by iwconfig because it has status off. Any body? help please:)[/QUOTE]
did you try other drivers from the ndiswrapper website? also, did you "sudo modprobe ndiswrapper" after you were done setting it up?

---

### Post by brujoand on 2006-05-15
yes both, but i could not find bcmwl5a driver, only the bcmwl5.

---

### Post by brujoand on 2006-05-15
Yohooo!! i downloaded the sourcecode for ndiswrapper and compiled it.. and weheey.. my wifi card is running and life is great !! if u need help with this, then.. 

this is the good shit: [http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)

---


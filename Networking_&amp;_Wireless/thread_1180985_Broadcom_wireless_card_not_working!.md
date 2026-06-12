---
title: "Broadcom wireless card not working!"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by babybash on 2009-06-07
Please can somebody help me ive tried linux before now and got very frustrated as i could not get my wireless working so i gave up for a while and now im trying again!!

I can connect to the internet via cable not a prob but i cant get my wireless card up and running i have been looking around the forums and im getting very cunfused as of where to start.

My wireless card is a broadcom bcm4310. Please would anybody have the time and patience to help me out.

Thankyou :popcorn:

---

### Post by narn1234 on 2009-06-07
Hello, have you tried the wireless setup areas? Like [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)


Also, you might have to use Ndiswrapper, and the help is [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)


I can help with some specifics, but start there!

---

### Post by babybash on 2009-06-07
hi i will give them a go thankyou ill post bak on how it goes!!

---

### Post by babybash on 2009-06-07
Hi ive had a look and found i if im right in thinking i can download the driver from broadcom!
But i need to know if i need the 32bit driver or 64 bit how do i find this out??

---

### Post by superprash2003 on 2009-06-08
depends on which version of ubuntu you installed.. 32bit or 64bit?

---

### Post by Ayuthia on 2009-06-08
You can check the following from the Terminal:
```
uname -m
```If it shows x86_64, then it is 64-bit.

However, if you have a working internet connection in Ubuntu, you should try running an update in Ubuntu first:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
It looks like you have not updated yet because you are still showing a 4310 card instead of a 4312.  Ubuntu comes with the Broadcom STA module built-in, but it did not work well in 8.04 without the updates.  Once updated, you should be able to activate the card by going into System->Administration->Hardware Drivers.

---


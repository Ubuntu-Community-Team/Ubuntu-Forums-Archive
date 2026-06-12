---
title: "wired connection but no internet"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by anthony.c on 2010-06-01
At the end of my third day trying to sort this out so I will REALLY appreciate any time you spend helping me.
 
When I unplug the ethernet cable from this laptop and plug into my Ubuntu 9.10 Desktop I get a wired connection automatically but I have no internet connection in Mozilla.
 
Please, any help you can offer will be appreciated.

---

### Post by jazzgossen on 2010-06-01
One thing it could be is if your ISP is blocking changes of MAC addresses. That has happened to me a few times. If so, you might have to wait up to several hours before you can connect to the Internet with the other computer.

---

### Post by Iowan on 2010-06-01
To what does the other end of the cable connect?
Some modems might need to be power cycled. It's possible to spoof a MAC address, but that doesn't seem like a fix. A router *might* help - it would present a constant MAC to ISP/modem.

---

### Post by anthony.c on 2010-06-02
Ok thank you so much for getting back to me.  The other end of the cable connects to  the dsl modem. I cant find "network manager" on gnome. Could that be a problem?? I installed Ubuntu from a DVD that was included in the Ubuntu User magazine. Could that also be a problem??
I am loving Ubuntu and am so happy to have given MS the flick.
 
 
Thanks Again.

---

### Post by dineshs on 2010-06-02
Can you post the output of
```
ifconfig -a
```and
```
ping 4.2.2.1 -c5
```

---

### Post by jazzgossen on 2010-06-03
> **anthony.c said:**
> I cant find "network manager" on gnome. Could that be a problem??
If you don't have network-manager, then yes, that would be a problem. It should be one of the icons in the tray (at the right of the upper panel). "sudo apt-get install network-manager" should fix that.

> 
 I installed Ubuntu from a DVD that was included in the Ubuntu User magazine. Could that also be a problem??

No, I can't imagine why it would be.

Do you also have another OS on the desktop machine? If so, you could try to run that to see if the problem is with your ISP not allowing to change computers or with Ubuntu.

---

### Post by Iowan on 2010-06-03
Sometimes you can recover Network Manager by right-clicking the top panel and adding a Notification Area. It (Network Manager) should also be checked in System>Preferences>Startup Applications

---

### Post by anthony.c on 2010-06-04
I can't thank you enough for your help. I waited until the next day to try again and I can now ping past the ADSL Modem and I can even ping a number different websites.
 
 However the problem now is that I can only view google web pages and no other pages will load. I still haven't recovered Network Manage though as I am yet to get back to the computer after reading that advice. As I always say "Any help will be most appreciated."

---

### Post by dineshs on 2010-06-04
Please see if this link can help
[http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506)

---

### Post by anthony.c on 2010-06-13
I have solved the problem thanks to a link in the Mozilla forum. My machine wasn't coping with IPv6 part of the Mozilla features. Once I disabled it in Terminal it all now works fine. Thanks for your help.

---

### Post by sammyko on 2010-06-25
Anthony, 
How and what did you do in the Terminal?

Regards

Sammy, The newby

---


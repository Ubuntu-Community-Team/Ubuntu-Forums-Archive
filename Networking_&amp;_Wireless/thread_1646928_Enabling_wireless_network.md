---
title: "Enabling wireless network"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by XlWeeDslX on 2010-12-16
i cant seem to get my wireless up and running it was working fine yesterday and i boot it up now and no wireless, it says its disabled i had a look around and couldnt find away to enable it.
i have looked around as much as possible, u have superuser rights (every thing enabled) and checked all my connections.
i did iwconfig and i get this:

         wlan0      
          IEEE 802.11bg  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off

my hardware is:
Atheros Communications Inc. AR5001 Wireless Network Adapter.

anyone have any ideas on whats wrong??

---

### Post by grahammechanical on 2010-12-16
Have you tried right clicking the network icon and scrolling down the menu until you come to Enable wireless and then clicking? I know it sounds like the most obvious suggestion but who knows, it might just be the answer. 

regards.

---

### Post by XlWeeDslX on 2010-12-17
> **grahammechanical said:**
> Have you tried right clicking the network icon and scrolling down the menu until you come to Enable wireless and then clicking? I know it sounds like the most obvious suggestion but who knows, it might just be the answer. 

regards. 

Yeh i know lol but its shaded out it wont let me click on it
anyone else have any ideas?

---

### Post by Kernelingus on 2010-12-17
Tell us what it says in /etc/NetworkManager/nm-system-settings.conf

---

### Post by XlWeeDslX on 2010-12-18
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:1d:72:67:68:7c,

[ifupdown]
managed=false

---

### Post by LOBD on 2010-12-18
I have the same problem too.

---

### Post by xircon on 2010-12-18
```
sudo gedit /var/lib/NetworkManager/NetworkManager.state

```

Edit everything to say true and not false, then reboot.  Did you recover from a failed suspend?

---

### Post by corncob on 2010-12-19
> **XlWeeDslX said:**
> i cant seem to get my wireless up and running it was working fine yesterday and i boot it up now and no wireless, it says its disabled i had a look around and couldnt find away to enable it.

anyone have any ideas on whats wrong??

This was exactly my problem the other day.  After much fiddling around without any success I finally rebooted both the modem and router (pulled their plugs) at the same time.  Suddenly, wireless was working again.

---

### Post by crystalclear on 2010-12-19
I have lots of questions.  If I need to post somewhere else please tell me...I have a sony laptop, I bought used..model #PCG-9H4L..on back   when opened it says PCG-FR130....when plugged in it says operating system not found....I have searched for many hours for a solution and found out about ubuntu operating system....I don't have much memory left in my compaq computer. I have an external hard drive...could this os be downloaded on an external hard drive and then burn a cd? or can a flash driver be used? I am a real novice..need detailed instructions...also I am on a network with my husbands computer..att uverse...can I connect to our network with a different os and not change things there?  I have been reading in the forums, It sounds like you haveto "format" thinmgs after installing ubunto os...I would have no idea how to do that....aldo I have no idea how much ram this sony laptop has.....after burning and installing this os....is there steps I need to know ...the laptop has a cd drive, but I'm not even sute it works....when you boot a cd, does that mean you just put in in and start it? also I did put a cd in it and od cours heard nothing....thats on reason I asked about a flash driver to install the os???????the sony orginally had windows xp home edition in it.  My os on my dest top compaq is windows media edition, and my husbands just bought a mac so he has safari.....I thought this info would be imp for info about the network.......Please help, I would like to bring this sony back to life if I can......thanks in advance.....

---

### Post by corncob on 2010-12-19
> **crystalclear said:**
> I have lots of questions.  If I need to post somewhere else please tell me...I have a sony laptop, I bought used..model #PCG-9H4L..on back   when opened it says PCG-FR130....when plugged in it says operating system not found....I have searched for many hours for a solution and found out about ubuntu operating system....I don't have much memory left in my compaq computer. I have an external hard drive...could this os be downloaded on an external hard drive and then burn a cd? or can a flash driver be used? I am a real novice..need detailed instructions...also I am on a network with my husbands computer..att uverse...can I connect to our network with a different os and not change things there?  I have been reading in the forums, It sounds like you haveto "format" thinmgs after installing ubunto os...I would have no idea how to do that....aldo I have no idea how much ram this sony laptop has.....after burning and installing this os....is there steps I need to know ...the laptop has a cd drive, but I'm not even sute it works....when you boot a cd, does that mean you just put in in and start it? also I did put a cd in it and od cours heard nothing....thats on reason I asked about a flash driver to install the os???????the sony orginally had windows xp home edition in it.  My os on my dest top compaq is windows media edition, and my husbands just bought a mac so he has safari.....I thought this info would be imp for info about the network.......Please help, I would like to bring this sony back to life if I can......thanks in advance.....

It would be best to start your own thread on this but, to get you started, yes, you can download Ubuntu to an external hard drive and burn it to a CD from there.  Then, with the CD in the Sony, turn it on and it should boot up from the CD.  If not, go into the BIOS Setup and, in the boot menu, change the first boot device to the CD.  Then follow the on-screen instructions.  It can run from the CD so you can try it first before installing if you want.  I don't know about this formating you mentioned -- it formats the hard drive during the install and is ready to run.  Ubuntu will need at least 250 meg of RAM to install but there are lighter versions of Linux that could bring the Sony back to life.  Yes, you can put it on a pen drive but the Sony will have to be able to boot from it.

---

### Post by crystalclear on 2010-12-19
thanks corn cob, I'm going to try and burn the cd. This is my first time here so I need to go and read how to post and find the answers...I'm sure I'm have many questions after burning the cd......

---

### Post by corncob on 2010-12-19
> **crystalclear said:**
> thanks corn cob, I'm going to try and burn the cd. This is my first time here so I need to go and read how to post and find the answers...I'm sure I'm have many questions after burning the cd......

You'll get more answers if you post them to the "Absolute Beginner's Talk" section of the forum, [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) .  Click on "New Thread" after you log in.  Also, you might read "The Ubuntu Pocket Guide".  There's a free pdf download at [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---


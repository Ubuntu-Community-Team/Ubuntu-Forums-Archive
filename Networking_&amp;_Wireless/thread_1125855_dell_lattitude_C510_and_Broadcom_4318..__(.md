---
title: "dell lattitude C510 and Broadcom 4318..  :("
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2009-04-14
After going through this now 3 times, I really thought I had this whole wireless thing licked in Ubuntu.. apparently, I shouldn't be thinking!

I aquired this lattitude and wiped windows as soon as I got it home. Now that I have Ubuntu working, I want to get the internal wireless running. I referred to a few guides and settled on [this one]("http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto").. none were perfect and I have become pretty comfortable with Ubuntu, so I figured I could muddle through this.

I downloaded bcm4318.all.tar.gz to desktop, extracted it, and ran:
```
me@home:~/Desktop$ sudo ./ndiswrapper_setup
```

Even though it told me none of the preferred versions of Ubuntu were detected, I chose to continue.. it felt right :) it even told me to post a [log file]("http://pastie.org/446814") for help. Obviously, something was not working, but it seems like the wireless card is detected and shows to be working to some extent, no?

lspci:
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


So I thought I'd look at the network manager but I couldn't remember how to activate it even though my system tells me it is installed. At this point I need some guidance. I'm not exactly sure what to do next. 

Thanks in advance.

---

### Post by Ayuthia on 2009-04-15
From the log, it looks like the application was unable to find ndiswrapper to install.  Do you have a working internet connection in Ubuntu?  If so, you need to run:
```
sudo apt-get update
```so that the repositories are updated.

Instead of trying ndiswrapper first, you might try to see if you can get the b43 driver to work.  If you have a working internet connection, go into System->Administration->Hardware Drivers and activate the Broadcom b43 driver.

---

### Post by sp0nge on 2009-04-15
Well that's just too easy for a linux system ;)

So I did some research.. and took your advice which has allowed me to be sure the card works.. but I remember reading somewhere that the stock driver only allows for 11mbps whereas ndiswrapper significantly increases speed...

Well the stock driver is working. I guess there is something to be said for "if it aint broke..." but how is it that I'm less that 3 feet from the wireless AP but only connected @ 66%? Yet the other laptop here that runs the compat wireless drivers is at 98% from the same position.. The stock driver works. I'll concede that point. But part of the reason I chose to stick with Ubuntu and *nix in general is the performance and reliability. 

Did I do something wrong with ndiswrapper? Are there different steps needed to get it working with 8.10?

---

### Post by Ayuthia on 2009-04-15
I just prefer that people try the native driver first only because it is the easiest to install.  If you don't like it, it is not that hard to change to ndiswrapper.  However, it is more difficult to go the other way around (ndiswrapper to b43).

Now that you have a working connection and I am guessing that you have made some updates.  If you have, you should be able to run that script again.  If you still have problems, please come back and you can post the log again and we can try to see what is happening.  Worst case, we can most likely get you back on track if something goes wrong.

---

### Post by sp0nge on 2009-04-16
Flawless.. Thanks for helping me understand! A good lesson learned though. I let myself slip into the habit of trusting the update notifier but apparently it's not perfect.. I think I'll cron the update/upgrade process to ease the need to worry about it. 

Again, thanks for the help~!

---


---
title: "converting someone to ubuntu only sticking point modem"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by teaker1s on 2006-06-15
driving me mad as the only sticking point is getting a 56k dialup modem to work.
following hsfpci setup it states that all is setup and package installed -if it doesn't work then modem not supported. reboot and told ppp0 not-avaliable

so I try a intel 539ep source driver as stated to use by intel-follow the instructions and low and behold it won't install because it doesn't like kernel version.

have till tomorrow to figure it out or they want win 2000 reinstalled.:rolleyes: 

any suggestions

---

### Post by mscman on 2006-06-15
You could always upgrade the kernel...

---

### Post by teaker1s on 2006-06-15
version on intel's site would need older kernel and break loads of things

---

### Post by zxee on 2006-06-16
Is it an option to get an external modem? Most of those are supported and if you live in or near a large city chances are you have some kind of 2nd hand computer store that might have a couple. Of course there's always ebay but you indicate you're on a tight schedule.

---

### Post by teaker1s on 2006-06-16
hi, it's several things.
1) the computer is old and xp wouldn't run-their choice not mine and because they've had loads of windows related malware they are prepared to try ubuntu.
2) it's a favour so spending money on it not something I want to do.
3) must have it back by sunday as they are back from holiday and that was the agreement

so far I've got the intel modem to dial out and connect,but it looses carrier signal-I believe it could be a baud problem tried gnome ppp .
can't see how to put in it's location in manually to test with kppp and manual states if it's not there file a wish list bug

---

### Post by zxee on 2006-06-16
In my experiance dapper's gnome-ppp is broken, or at least it has big problems. Kppp is usually better to use-don't know how you loaded it in ubuntu cause you would need kde libraries +.
there are how-to's on setting up dial up but basically use pppconfig from a shell make sure your user is allowed to dial out that is in the advanced section of the pppconfig script. Then try using modem monitor. You can get that applet by right clicking on the upper or lower panel/menu bar and selecting add to panel-you have to scroll down the list of items to find it.
Also you said the computer is old. If it has less then 256MB ram ubuntu won't work on it. You might want to try an earlier version or a different distro on it.

---

### Post by teaker1s on 2006-06-16
celeron 500mhz and 131 mb runs quite reasonably surprisingly. tried symlinking so I can use dev/modem and kppp won't access it
tried pppconfig and modem monitor and it still does the same thing -any ideas where I go from here?

it's turned out to be the fact that intel haven't updated their driver for 2.6kernal

---

### Post by Matchless on 2006-06-16
Hi,
    Not sure if you have had a look at the wiki dialupmodemhowto, but assuming you have, the symlink should work and Kppp should be able to query the modem. I have  had an Intel536ep working on dapper kubuntu with Kppp. What could be a problem is that winmodems use you processor and may be a bit heavy on an older computer such as the Celeron 500 mentioned, but I am not sure what exactly will or will not work in CPU power and ram size.  I have found Kppp very finicky and also influenced by the lan card settings around your ip, gateway and dns. What works is lan card on dhcp, leave default gateway empty, leave DNS empty and leave static hosts as was installed.
Now set your modem via Kppp for Dynamic IP, Disable auto config hostname, static gateway to 196.168.0.1, enable assigns default route to this gateway, automatic DNS, do not disable existing DNS servers during connection. 
This works for me, but may be slightly different for your ISP It is also very important that you go to /etc/ppp/peers/kppp-options and remove the #noauth comment to noauth and sett Kppp to "pap".
If this does not work you can try using pon and poff and make an icon on the desktop to connect and disconnect! 
Good luck

---


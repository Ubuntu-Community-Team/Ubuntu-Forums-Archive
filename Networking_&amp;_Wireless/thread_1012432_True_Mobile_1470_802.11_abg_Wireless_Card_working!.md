---
title: "True Mobile 1470 802.11 a/b/g Wireless Card working!!!"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by Tweakbl on 2008-12-15
Hello,I am new to Linux,although I have installed it several times in the past in Virtual machines and fiddled with it.
I just installed Xubuntu on my Dell C640 without any trouble.

The only thing that did not work out of the box was the Dell True Mobile 1470 802.11 a/b/g Wireless Card.I bought it separately just for this machine.
As I understand it.ALOT of people have had troubles with these Broadcom cards.

Edit:I actually Blacklisted the default driver for not working.CODE:**echo 'blacklist bcm43xx'** 
Then rebooted,
After Reboot,Go to ADD/Remove and Update your package info.then run Hardware Drivers Update,it automagically fixed my wifi not working issue.I had forgot I blacklisted.:p

I did however notice that before I blacklisted it that the default driver was installed just not working properly.At the command line it told me [with the **lshw** and **lsmod** commands]that it was a Broadcom chipset.

Anyway it is working now.I am going to reinstall for practice and to be sure it works smooth again.Thank You's to the Dev's of FWcutter!
Also thanks to all the posters to this forum for helps.Good help links-----
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)
[http://ubuntuforums.org/showthread.php?t=766560&highlight=truemobile](http://ubuntuforums.org/showthread.php?t=766560&highlight=truemobile)

EDIT:Just reinstalled,blacklisted,ran hardware update.It works really well.:)

Running Xubuntu 8.10 Ibex

---


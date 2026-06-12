---
title: "Wireless drivers/functionality suddenly disappeared - Kubuntu 9.1 HP TX1000 laptop"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by mothergoose729 on 2010-04-18
I switched my girlfriend laptop from windows 7 to Kubuntu 9.4, then upgraded to karmic koala. I was able to, through the hardware manager, install a software modem driver, and a firmware unwrapper driver for her broadcom 4.X series wireless adapter. Whenever I attempted to install the broadcom 4.1, 4.2. ect driver itself a package update would fail, but wireless functionality still worked nonetheless.

My girlfriend has a TX1000 HP laptop, similar to this one:

[http://reviews.cnet.com/tablet-pcs/h...-32305764.html](http://reviews.cnet.com/tablet-pcs/h...-32305764.html)

Product number in the bios is GA648UA#ABA
System Board ID is 30BF

The wireless drivers she needs are proprietary.

This worked for a while, although seemingly at random her wireless would go out, and her analog sound driver for her Nvidia chipsets would too. Usually logging out of the KDE environment and back in fixed the issue. Now wireless is completely gone; using a hard ethernet core to the router still works. Even connected to the internet, the proprietary drivers that used to be available in the hardware manager aren't there anymore. Right before the driver disappeared, I updated the system with all the latest round of updates, and installed the base package and some plugins for VLC. I don't know how to role back packages to see if an update killed the wireless, I uninstalled the VLC software but that didn't help.

Wireless is checked enabled on my taskbar, and I have checked my bios and haven't found any setting to disable the wireless adapter. Anything networking related has been enabled.

At this point I am rather frustrated with the stability of Kubuntu overall and would prefer a hard solution that will permanently fix the problem. Any help would be great thanks :)

---

### Post by mothergoose729 on 2010-04-18
bump?

---

### Post by mothergoose729 on 2010-04-19
Last bump. Anyone have any clues :(

---

### Post by Favux on 2010-04-19
Hi mothergoose729,

This is a good thread for TX1000 wifi:  [http://ubuntuforums.org/showthread.php?t=1292862](http://ubuntuforums.org/showthread.php?t=1292862)

Notice the last couple posts suggesting hardware failure.  It would help if  you had a Windows partition to check it on.  Basically the TX1000 is notorious for running hot and this apparently can cook the wifi.  If so you can get a usb wifi dongle.

For more info. see:  [http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Problems-with-pavilion-tx1000-s-wireless/m-p/8613](http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Problems-with-pavilion-tx1000-s-wireless/m-p/8613)
and an anecdote:  [http://ubuntuforums.org/showpost.php?p=8731734&postcount=1](http://ubuntuforums.org/showpost.php?p=8731734&postcount=1)

Good luck!

---


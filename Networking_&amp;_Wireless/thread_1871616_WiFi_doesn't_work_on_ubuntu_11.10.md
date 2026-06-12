---
title: "WiFi doesn't work on ubuntu 11.10"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by Davis Bre on 2011-10-29
Hi all!

Recently I have installed Ubuntu 11.10. on my Lenovo B560. And now mi wifi doesn't work, with Windows it worked fine. I have an atheros 8131 network card. I have tried a lot, but even a wifi ligt doesn't shine. Could anyone help me, I'am completely beginner.

Davis

---

### Post by jackdale on 2011-10-29
You may have tried this already, but you didn't mention it, so I'll ask:

Have you tried going to system settings and under the Hardware category selecting Additional Drivers?  This utility will search for proprietary drivers that might get your card working (obviously you'd need to be connected to the web via ethernet).

From what I can gather, there's not very good support for your particular card by Debian (and therefore Ubuntu).  However, if the above does not work, try having a look at this (long) trouble shooting guide:

[https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html]("https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html")

---

### Post by Davis Bre on 2011-10-29
My Broadcom wireless driver has been activated some time ago. But I still can't enable wireless. And I have had tried ndiswrapper but I couldn't run it, and I have tried Windows wireless driver program, but it shoots out an error: Not a valid driver .inf file.

---

### Post by JRRCPA on 2011-10-29
Thanks you help me getting my wireless conenction to work again

---

### Post by Davis Bre on 2011-10-29
I took a look to the troubleshoot guide. Everything seems to be ready to go. Any ideas what can I do? Or it's pointless because of not very good support for my card?

---

### Post by jackdale on 2011-10-30
I'm afraid that I've reached the limit of what I could suggest.

However, I would have thought that ndiswrapper might have done the job.

From what I understand about ndiswrapper you have to make sure that:

The windows driver is for Windows XP
I think this means that you have to be using the 32bit version as 64bit (Vista and W7) has not been implemented in ndiswrapper.
I'm not sure if this also means that you also have to use 32bit Ubuntu.

Perhaps there are others that use ndiswrapper that might help troubleshoot?

---

### Post by varunendra on 2011-10-30
Hello Davis, and welcome to the forums :)

As far as I could find, atheros 8131 is an Ethernet card, not a wireless one. And since you say you have "activated" your "broadcom" wifi driver, I am assuming it is a broadcom wireless and you have 'activated' that driver from the "Additional Drivers" option. Accordingly, please try the following :
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
then
```
sudo apt-get install firmware-b43-installer b43fwcutter
```

If this doesn't help, please post outputs of:
```
lsmod
cat /etc/modprobe.d/blacklist.conf | grep b43
ls -l /etc/modprobe.d/bl*
```

---

### Post by Davis Bre on 2011-10-31
Thanks, but it didn't worked. But luckily, I have found solution here: [http://ubuntuforums.org/showthread.php?t=1871781](http://ubuntuforums.org/showthread.php?t=1871781)

---


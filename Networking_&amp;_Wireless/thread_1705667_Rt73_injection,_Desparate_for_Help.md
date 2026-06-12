---
title: "Rt73 injection, Desparate for Help"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by psulinux24 on 2011-03-12
Hello,
first as a disclaimer I would definitely qualify as a n00b,  so I'd appreciate concise, detailed help.  

I'm trying to get a USB wireless adapter, TP-TLink 321NG working.  Out of the box plugging the adapter in I see rt2800usb via lsmod,  which I understand to be broken.   I also understand there to be issues with network manager which I have uninstalled in place of wicd.

I cannot seem to install succesfully on various versions of Ubuntu i've tried,  currently working with 9.10,  which unfortuantely is kernel >= 31, leading to problems with rt73.ko failed to load, which I've been unable to resolve.  

I have tried the .deb obtained from here"  [http://ubuntuforums.org/showthread.php?p=10110342](http://ubuntuforums.org/showthread.php?p=10110342)   which seems to successfully install, but despite it's claims my main blacklist.conf file seems unaffected (though there are new files along the lines of rt73-blacklist.conf.

In any case, I now get a new rt73 via lsmod, which I attempt to load vs modprobe.  

However ifconfig still results in  wlan0  (my understanding is rausb0 is what I am looking for to indicate success.

Could someone please help? I'm willing to install any Ubuntu version necessary, I just want to get this working!!!

---

### Post by wilee-nilee on 2011-03-12
Here is a link not sure if this will help.
[http://ubuntuforums.org/showthread.php?t=1674129](http://ubuntuforums.org/showthread.php?t=1674129)

Additionally I would if it was me download a later Ubuntu release and see if the driver that will run it is in a later kernel. You can check it from the live cd.

---

### Post by psulinux24 on 2011-03-12
> **wilee-nilee said:**
> Here is a link not sure if this will help.
[http://ubuntuforums.org/showthread.php?t=1674129](http://ubuntuforums.org/showthread.php?t=1674129)

Additionally I would if it was me download a later Ubuntu release and see if the driver that will run it is in a later kernel. You can check it from the live cd.

I started with 10-10, went down to 10-4, then back further when online research revealed issues with kernels > 31. 

The closest I have gotten just now involved following this:[http://ubuntuforums.org/showthread.php?t=1178790](http://ubuntuforums.org/showthread.php?t=1178790) step by step.  But still had a few problems:

step 1: he says using jaunty run sudo apt-get install wicd.

This didn't work for me wicd, was not found, I add had to add source via synaptic package manager.  Why would this be different from me, then the author's post if we're both in jaunty?


Anyhow also that aside, once I complete everythign I run iwconfig and now see 
pan0


which still isn't rausb0, and still isn't recognized by aircrack-ng

Anyone can help further? have I finally gotten close?

---


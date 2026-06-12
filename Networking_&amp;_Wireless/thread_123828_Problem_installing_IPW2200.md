---
title: "Problem installing IPW2200"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by azuro on 2006-01-31
I've downloaded the driver and tried to install it.  When I try to compile the driver, I got the following error:

```
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jcsmith/ipw2200-1.0.3 MODVERDIR=/home/jcsmith/ipw2200-1.0.3 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
``` 

I've been following the instructions in [this]("http://www.ubuntuforums.org/showthread.php?t=26623") thread and I've installed these packages: build-essential, gcc, linux-headers.  

What should I do now?

---

### Post by audax321 on 2006-01-31
What computer do you have? I got a HP DV1000 and the IPW2200 B/G Wireless Card worked out of the box... Those directions you are following are for Hoary. The card should work in Breezy fine, with maybe a few small quirks.

The only problem I ran into was solved here: 
[http://ubuntuforums.org/showthread.php?t=75612](http://ubuntuforums.org/showthread.php?t=75612) (see first post by xMetaRidley).

---

### Post by azuro on 2006-01-31
I'm just trying to update my drivers.  My current driver work with Open and WEP wireless connection, but I'm trying to configure it to connect to my school wireless which uses PEAP-MSCHAPv2.  

According to the instructions the school provides, the wireless uses WEP and the key is provided.  It uses PEAP-MSCHAPv2 authentication.  

I've installed wpasupplicant and modified a few files and still couldn't get it to work.  Any ideas on how to configure it??

---

### Post by audax321 on 2006-01-31
Unfortunately I don't know much about WPA Supplicant. I just use the basic WEP security. However, I came across this if it helps:

[http://www.linuxquestions.org/questions/showthread.php?t=279387](http://www.linuxquestions.org/questions/showthread.php?t=279387)

---


---
title: "Modem Drivers"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by vzx on 2005-12-19
I ran scanModem and it told me that I needed the slamr driver.
I downloaded that (in Windows) from [http://linmodems.technion.ac.il/packages/smartlink/slamr_for_Ubuntu_kernel-2.6.10-5-386_ONLY.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/slamr_for_Ubuntu_kernel-2.6.10-5-386_ONLY.tar.gz) and unzipped it.
Within the zip Usage.txt says:
> After login to a console as
# su - root
cd into this folder/
Then try driver loading:
# modprobe ./slamr.ko


That didn't work. I noticed that in the DialupModemHowto there were preliminary packages that were required, but it tells you to download them with Synaptic, Adept, aptitude or apt-get, but I am not online in Ubuntu yet. So what is the address where I can download these packages? I could presumably download them from within Windows, install them in Ubuntu and then install the drivers. Is there some other point I am missing?

---

### Post by Lambert on 2005-12-20
You can download the packages from here. You'll have to check to make sure you have all dependencies. If not you'll need to download and install the missing dependencies first.

[http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)

---


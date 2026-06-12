---
title: "Wireless not working on Samsung N210"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by afroldy on 2010-07-24
Hello.
I know a post on this topic has come up before, but:
 
a) it's marked as solved, so people don't seem to be too interested now, and
b) I posted in it and got no response.
 
So, I hope I'm not breaking some rule by posting this thread. Tell me if I am :-)
 
 
I bought a Samung N210 last week, installed Ubuntu Netbook Remix on it, and have not been able to get the wireless working. Apparently this is down to needing an updated driver, which I obtained from Realtek. I installed the driver, following the instructions in their email perfectly:
 
**Just kindly remind, please install by the below steps.**
**The following is the installing steps:**
**1. Change to the driver directory**
**2. sudo su**
**3. make**
**4. make install**
**5.reboot**
**6. ./wlan0up or ./wlan1up**
 
**Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`**
**2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).**
 
Everything goes fine up to step 6, where I type in ./wlan0up and get the following error message:
 
**cp: cannot create regular file `/etc/acpi/events/RadioPower.sh': Permission denied**
**insmod: can't read 'r8192e_pci.ko': No such file or directory**
 
Following note 1 and 2 on the email instructions has no effect. I emailed realtek about it and got this response:
 
**Please check you system is 32bit or 64bit first. **
**If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delete it first before install:** 
 
**1) cd /lib/modules/2.6.3x.xx.xx/**
**2) find -name "r8192e_pci.ko"**
**3) delet all the r8192e_pci.ko**
**4) install our RTL8192E driver**
**5) reboot.**
 
I'm not sure if Ubuntu Netbook Remix is 32 or 64 bit, but I tried this anyway, and it had no effect. I don't know if
 
a- Ubuntu Netbook Remix is 32 or 64 bit, and so I don't know if it would have any effect anyway, and
b - if I have to delete everything before trying this last step and then reinstalling on top, or even reinstalling ubuntu completely.
 
Any advice guys? Either on the original problem, or my questions at the end? Hopefully someone who has got the wireless working on the N210 will be able to help me out. Thanks in advance!

---

### Post by afroldy on 2010-08-02
Sorry to bump guys, but I've had no luck. I've tried various methods outlined in these posts:

[http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1499820](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1499820)

and keep getting the same results. Can anyone help?

---

### Post by mr_simmo on 2010-08-16
just to echo this, I'm having the same, exact issues. 

Also have tried the methods outlined in the other threads, but to no avail....
If there is anyone out there who can help with this, I can offer my undying gratitude and love. 

Thanks!

---

### Post by cosmicappuccino on 2011-01-02
Hi, I'm having exactly the same problem, too...

Did either of you eventually find a solution, or can anyone else offer any advice please?

---

### Post by jeandk on 2011-01-05
Hello,

I want to buy a N210 and install ubuntu, but as I see, there are some problems.
Is it a temporarely problem?
Cuz if I buy a N210 it's preferable to be solved :-(

---

### Post by cosmicappuccino on 2011-01-05
Although this is not a *solution* to the problem, this may be useful: I have now installed Lucid Lynx and the wireless works fine. (I had to install a driver, but this worked first time.)

So it isn't impossible to use Ubuntu on the N210 :)

---

### Post by jeandk on 2011-01-06
I see ,I see,

Well yeah.

Ubuntu is quite new to me.
So would like to learn on a working pc :p without failures .

Are there often updates?

Like updates that solve this problems. :confused:

---


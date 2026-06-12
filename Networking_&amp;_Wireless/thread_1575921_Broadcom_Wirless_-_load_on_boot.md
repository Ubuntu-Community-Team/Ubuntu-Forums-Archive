---
title: "Broadcom Wirless - load on boot"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by spd_demon on 2010-09-16
Hi all,
 
Just recieved an HP 5103 that has a BCM4313 14e4 4727 wireless card. I had a heck of time finding a driver but finally did and installed it. This is on Ubuntu Netbook Remix 9.10.
 
However, it seems I have to load the driver everytime and can't get it to load during boot. I'm an Ubuntu/Linux newbie so any help would be appreciated.
 
Thanks.

---

### Post by MaindotC on 2010-09-16
Describe the steps you took to get the driver installed.  Are you using ndiswrapper?  If you are using the b43 driver did you modprobe it?

---

### Post by spd_demon on 2010-09-16
Yes sorry should have mentioned that. So I compiled the driver which creates the module wl.ko however there is a prerequisite step. 
 
So when I reboot and lose the wireless I do:
 
1. modprobe lib80211
2. insmod wl.ko
 
As soon as those two commands are completed, wireless comes alive. But again, when I reboot I have to repeat the commands to make it work again.

---

### Post by bkratz on 2010-09-16
did you do this part of the instructions?

3: Setup to always load at boot time.

The procedure to make a module load at boot time varies from distro to
distro.  Consult the docs for your specific distro to see how.  The 
following seems to work for my setup on Fedora and Ubuntu.  Check your 
docs to see the procedure for your distro.

Follow these steps to have the driver load as part of the boot process:

# load driver as described above
# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless 
# depmod -a

---

### Post by spd_demon on 2010-09-16
Yes I did try that as per the instructions and I get:
 
"cp: target '/kernel/drivers/net/wireless' is not a directory"

---

### Post by spd_demon on 2010-09-16
I check the spacing of the command and I had a space after uname and /kernel.
So when I put it together i get the error:
 
"cp: cannot create regular file '/lib/modules/uname -r/kernel/drivers/net/wireless': No such file or directory"

---

### Post by MaindotC on 2010-09-16
removed

---

### Post by bkratz on 2010-09-16
> **spd_demon said:**
> I check the spacing of the command and I had a space after uname and /kernel.
So when I put it together i get the error:
 
"cp: cannot create regular file '/lib/modules/uname -r/kernel/drivers/net/wireless': No such file or directory"



This posting should help you

[http://ubuntuforums.org/showpost.php?p=8556440&postcount=2](http://ubuntuforums.org/showpost.php?p=8556440&postcount=2)


Here is the whole thread
[http://ubuntuforums.org/showthread.php?p=8556440#post8556440](http://ubuntuforums.org/showthread.php?p=8556440#post8556440)

---


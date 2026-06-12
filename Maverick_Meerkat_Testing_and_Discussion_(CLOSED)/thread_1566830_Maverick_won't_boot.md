---
title: "Maverick won't boot"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by clickwir on 2010-09-02
Was running Kubuntu Lucid 64bit just fine. Went and upgraded to Maverick today. Can't get past a semi-purple screen on bootup. I see the GRUB menu, then 2 seconds later I get the semi-purple screen and it hangs there for about a minute or two, then the monitor goes to sleep. Have to press the RESET button to reboot and try something else. 

I try pressing ALT+F1 to get a console screen and get nothing. Tried ALT+CTRL+F1, same, nothing. I haven't used them in a while on Ubuntu, don't know if Ubuntu removed that shortcut or not.

I rebooted in RECOVERY MODE and tried to load X in Failsafe Mode but that doesn't seem to work either. I'm using an ATI 4830 video card.

---

### Post by QIII on 2010-09-02
It wasn't a good idea to upgrade to Maverick, since it is a development version that just came out in Beta today.

I started testing it the day the repos were available -- on a different machine than my "daily use" machine.

"Update" or install?  Upgrading with video drivers installed is a good way to beg for problems.  Sometimes it does not go well.  While I don't recommend upgrading at all -- reinstall instead -- if you do it is sometimes best to uninstall video drivers and reinstall them after updating.

Do you have a separate /home partition?  You may be able reinstall Lucid.

---

### Post by rburkartjo on 2010-09-02
click i am having a similar problem

---

### Post by oldfred on 2010-09-03
For Lucid & Maverick I have had to do this with my Nvidia card:
I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
*ERROR* Forcing to 32M GART size
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)

---

### Post by QIII on 2010-09-03
I think oldfred is pretty much on track there for the ATI card.

My Maverick machine has Intel graphics, so I can't test this.  Hopefully the old way of purging fglrx, reinstalling the mesa (et al) drivers and then reconfiguring xorg might work.  (If you want to try that, we can give you the details.)

If so, that might get you to the desktop, and you could see if the proprietary ATI driver will install and work on Maverick.  It may not.  AMD/ATI has been doing a great job of getting the very latest drivers tuned up and ready to come out with the release version of Ubuntu (they usually do that before the drivers are even available to anyone else.  They seem to have a sweet spot for Ubuntu.)  But that happens right before release and the driver may not yet be available for the Beta.

But I still have to say:  

It's just not a good idea to upgrade with proprietary drivers installed (uninstall them first).  

Rather than upgrading, it's a good idea to have a separate /home partition and reinstall fresh (being sure not to mess with your /home partition -- which you should have saved somewhere safe just in case you do!)  

Most of all, it's really not a good idea to upgrade or install a development OS on your daily driver (unless you multi-boot).  Things can and will break as the work continues on getting them ready for release.  That'll likely leave you in the position  you are in.  We've all done things like that and regretted it, I assure you.  Lesson learned.

---

### Post by VMC on 2010-09-03
> **clickwir said:**
> Was running Kubuntu Lucid 64bit just fine. Went and upgraded to Maverick today. Can't get past a semi-purple screen on bootup. I see the GRUB menu, then 2 seconds later I get the semi-purple screen and it hangs there for about a minute or two, then the monitor goes to sleep. Have to press the RESET button to reboot and try something else. 

I try pressing ALT+F1 to get a console screen and get nothing. Tried ALT+CTRL+F1, same, nothing. I haven't used them in a while on Ubuntu, don't know if Ubuntu removed that shortcut or not.

I rebooted in RECOVERY MODE and tried to load X in Failsafe Mode but that doesn't seem to work either. I'm using an ATI 4830 video card.

Next time your in a "freeze" situation tyr first```
 Alt+PrtScr+b
``` and see if tht reboots your system.

Seeing you have an ATI video I can't be of much help.

 I do have a laptop 32-bit ATI, and I edit grub this way: At the tail end of the linux line I add *radeon.modeset=0 xforcevesa*. The reason for xforcevesa is I can't use frame buffer otherwise.

---

### Post by coffeecat on 2010-09-03
> **VMC said:**
> Next time your in a "freeze" situation tyr first```
 Alt+PrtScr+b
``` and see if tht reboots your system.

Just using 'b' might lead to filesystem corruption because that doesn't unmount partitions or sync data. Better is AltGr+PrtScr+ r-e-i-s-u-b. See:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

Also, I believe on some machines the Alt key won't work with this (iirc this has happened to me) and you have to use AltGr.

---

### Post by jppr on 2010-09-03
I did 2 days ago fresh Kubuntu 10.10 amd64 installation and system run without problems. I have Nvidia 9400 GT card but I run system nouveau-driver and without problems ;)

---

### Post by clickwir on 2010-09-03
I've not been running the ATI driver for a couple releases now. So I'm just using whatever is detected and used automatically.

I'm going to recover mode and run a netroot and do an update. See what that does.

---

### Post by clickwir on 2010-09-03
Just did an update. Same thing. I see on my screen for a half second UBUNTU 10.10 and the dots . . . . 

but that goes away very quickly and then I just get the purple-ish screen and can't do anything.

Alt+SysReq+R-E-I-S-U-B does work at killing everything, I get a black screen and it goes to sleep, syncing and unmounting... then rebooting. 

I'm assuming the boot up process is trying to switch over to Plymouth? and failing. It's not falling back to something that does work.

I've no idea how to troubleshoot Plymouth.

---

### Post by clickwir on 2010-09-03
Bug, looks like others have it too.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598322](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598322)

Adding "radeon.modeset=0" to grub after "quiet splash" has got me to boot.

---

### Post by ranch hand on 2010-09-03
There is a good fix available for plymouth but the devs haven't let the fact that it is no good have them scrap it.

When you boot did you try editing the menu  entry to not have splash in the instruction string?  This will many times allow you to boot.

You need to hit  e  to edit the entry and then Ctrl + x to boot with your edited version.

If that hasn't done the trick you could replace both splash and quiet with nomodeset and try that.

Great boot manager.

---

### Post by VMC on 2010-09-03
> **clickwir said:**
> Just did an update. Same thing. I see on my screen for a half second UBUNTU 10.10 and the dots . . . . 

but that goes away very quickly and then I just get the purple-ish screen and can't do anything.

Alt+SysReq+R-E-I-S-U-B does work at killing everything, I get a black screen and it goes to sleep, syncing and unmounting... then rebooting. 

I'm assuming the boot up process is trying to switch over to Plymouth? and failing. It's not falling back to something that does work.

I've no idea how to troubleshoot Plymouth.
When you see grub menu type 'e' for Maverick kernel and then remove the *"quiet"*  word from the "linux" line and see what messages come across your screen.

---

### Post by ssam on 2010-09-04
i think mine is the same issue.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376)

---


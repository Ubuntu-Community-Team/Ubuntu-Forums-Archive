---
title: "upgrade leads to nauveau issue &quot;No native mode, forcing panel scaling&quot;"
date: 2012-11-04
forum: Mythbuntu
---

### Post by davidstoll on 2012-11-04
I've seen lots of threads regarding this issue.  The main resolution seems to be to add
"GRUB_CMDLINE_LINUX_DEFAULT="drm_kms_helper.poll=0"
to the /boot/grub/grub.cfg and then run
sudo grub-mkconfig -o /boot/grub/grub.cfg

It doesn't seem to be helping.  I just upgraded to 11.04 (on my way to 12.04).  I have this thing configured and need to avoid a complete re-install.

I have an Nvidia card.

I would really appreciate your help.

Thanks!

---

### Post by nickrout on 2012-11-04
> **davidstoll said:**
> I've seen lots of threads regarding this issue.  The main resolution seems to be to add
"GRUB_CMDLINE_LINUX_DEFAULT="drm_kms_helper.poll=0"
to the /boot/grub/grub.cfg and then run
sudo grub-mkconfig -o /boot/grub/grub.cfg

It doesn't seem to be helping.  I just upgraded to 11.04 (on my way to 12.04).  I have this thing configured and need to avoid a complete re-install.

I have an Nvidia card.

I would really appreciate your help.

Thanks!I assume your subject line refers to the nouveau open source driver.

Why are you using it? The proprietary driver is what you really want for a myth box.

---

### Post by davidstoll on 2012-11-04
> **nickrout said:**
> I assume your subject line refers to the nouveau open source driver.

Why are you using it? The proprietary driver is what you really want for a myth box.

I was using proprietary driver and didn't change anything except to upgrade.

---

### Post by nickrout on 2012-11-04
> **davidstoll said:**
> I was using proprietary driver and didn't change anything except to upgrade.you need to give far more information. What did you upgrade from and what did you upgrade to? How did you accomplish this update (commandline, a gui update tool etc), where do you see this message and what effect is it having on your system?

---

### Post by davidstoll on 2012-11-04
> **nickrout said:**
> you need to give far more information. What did you upgrade from and what did you upgrade to? How did you accomplish this update (commandline, a gui update tool etc), where do you see this message and what effect is it having on your system?

10.10 32bit to 11.04.  The update manager in the gui gave me the option.

When the system is booting up, before it gets to a gui now, it gives me that error every few seconds...filling up the screen after a few minutes with the same text, just a different time stamp.  X doesn't start.

---

### Post by nickrout on 2012-11-04
> **davidstoll said:**
> 10.10 32bit to 11.04.  The update manager in the gui gave me the option.

When the system is booting up, before it gets to a gui now, it gives me that error every few seconds...filling up the screen after a few minutes with the same text, just a different time stamp.  X doesn't start.Actually I recall a problem a while ago where the solution involved blacklisting the nouveau driver, but the details elude me.

How about:

```
sudo aptitude install nvidia-current
```?

---

### Post by davidstoll on 2012-11-06
> **nickrout said:**
> Actually I recall a problem a while ago where the solution involved blacklisting the nouveau driver, but the details elude me.

How about:

```
sudo aptitude install nvidia-current
```?

I did try the blacklisting, but it didn't help.
My nidia-current are current.

Even before this issue, sometimes if I rebooted the machine, it would get to a point in the boot process (just before loading xwindows) where the screen would blink a couple of times and then freeze.  I would have to reboot like 10 times and then it would finally come up.  It would just sometimes get in a strange mood, other times I could reboot without any problem.  Other people have just said that sometimes these drivers can be flaky.

I actually was able to get to a command prompt using recovery mode and do a dist upgrade hoping another update might get me over this hump (I wanted to get to 12.04 anyway).

I can get to the point where I see the nvidia logo, it blinks as if it is just about ready to go to the gui and then blinks again to the nvidia logo, etc.  It just keeps going through that loop over and over.

In rescue mode it looks as if the file system is mounted as read only.  I can remount as rw (manually after each reboot to recovery mode) and it seems fine, but I still have the gui loading issue.

I was going to purge the nvidia drivers, but I don't have a "drop to command line as root with networking", so if I purge them, I won't be able to get them back.  I also tried renaming the xorg.conf file and also tried to recreate it, but no luck there either.

I'm not sure if the "upgrade" options are all that reliable.

---

### Post by nickrout on 2012-11-06
> **davidstoll said:**
> I did try the blacklisting, but it didn't help.
My nidia-current are current.

Even before this issue, sometimes if I rebooted the machine, it would get to a point in the boot process (just before loading xwindows) where the screen would blink a couple of times and then freeze.  I would have to reboot like 10 times and then it would finally come up.  It would just sometimes get in a strange mood, other times I could reboot without any problem.  Other people have just said that sometimes these drivers can be flaky.

I actually was able to get to a command prompt using recovery mode and do a dist upgrade hoping another update might get me over this hump (I wanted to get to 12.04 anyway).

I can get to the point where I see the nvidia logo, it blinks as if it is just about ready to go to the gui and then blinks again to the nvidia logo, etc.  It just keeps going through that loop over and over.what does /var/log/Xorg.0.log tell you?> 

In rescue mode it looks as if the file system is mounted as read only.  I can remount as rw (manually after each reboot to recovery mode) and it seems fine, but I still have the gui loading issue.

I was going to purge the nvidia drivers, but I don't have a "drop to command line as root with networking", so if I purge them, I won't be able to get them back.What? What about ctrl-alt-f1>   I also tried renaming the xorg.conf file and also tried to recreate it, but no luck there either.

I'm not sure if the "upgrade" options are all that reliable.
You don't say! I would blow away the existing OS and install 12.04 from scratch. After backing up whatever you need of course (if it's frontend only that is probably nothing).

---

### Post by davidstoll on 2012-11-07
nickrout, you already know this, but I'm just putting this in for reference.

Blew away OS, but now I have a video issue...

[http://ubuntuforums.org/showthread.php?p=12341767&posted=1#post12341767](http://ubuntuforums.org/showthread.php?p=12341767&posted=1#post12341767)

---


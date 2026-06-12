---
title: "CALL FOR TESTING: i8xx Legacy Driver"
date: 2010-08-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Catharsis on 2010-08-01
> **Christopher James Halse Rogers]Hello intrepid X adventurers!

The wonderful world of i8xx freezes probably needs no introduction. What does need introduction is the xserver-xorg-video-intel driver in [ppa:raof/aubergine](https://edge.launchpad.net/~raof/+archive/aubergine). This construction of Chris Wilson's re-introduces a GEM-less UMS codepath, which should work around the GTT incoherency problems.

This needs testing &#8212 said:**
> 
Source: [https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000905.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000905.html)

[QUOTE=Bryce Harrington]If we fail to see sufficient interest in helping with doing testing, then that's going to make it very hard to justify putting Canonical time into supporting 8xx chips going forward.

Frankly, we're really on the verge of dropping support for 8xx, this was kind of an unexpected surprise to see upstream attention at providing a new solution, but it is really going to need strong community backup to support it.
Source: [https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000909.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000909.html)

**[size=+1]Instructions[/size]**

[list=1]
[*]Remove any graphics workarounds that might interfere with testing. The common i8xx workarounds you might have enabled are listed [here](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

[*]Install the xserver-xorg-video-intel and libdrm packages:
```
sudo add-apt-repository ppa:raof/aubergine
sudo apt-get update && sudo apt-get upgrade
```
Note: This will leave libdrm-nouveau1 as held-back. DO NOT force that upgrade; it will break things.

[*]i8xx users should test the UMS codepath by adding 'nomodeset' or 'i915.modeset=0' (they do they same thing) to their GRUB_CMDLINE_LINUX_DEFAULT line:
```
gksudo gedit /etc/default/grub
sudo update-grub
```
All other Intel graphics users should test for regressions using the default KMS path.

[*]Test the driver for a few days. Important testcases include changes in: the boot behavior, frequency of freezes, playing a video file in Totem, watching a YouTube video, and enabling Full Screen in either Totem or YouTube.

[*]Subscribe to the [Ubuntu-x Mailing List](https://lists.ubuntu.com/mailman/listinfo/ubuntu-x). Then post your results to the list by sending an email to [email]ubuntu-x@lists.ubuntu.com[/email] with your experiences using the new driver as well as your specific chipset (lspci | grep VGA). If new or different bugs are experienced, it would be useful to find them in Xorg.0.log or dmesg, and then attach those log files to the email along with their explanations.
[/list]

Thank you for taking the time to help improve Ubuntu. i8xx graphics issues were one of the major bugs in the Lucid Lynx release and caused many of us with these chipsets to either downgrade or change distros. So for those with these chipsets, this is your opportunity to help solve the i8xx issues and get a workable, usable Ubuntu system once again. Happy testing, and good luck!

---

### Post by jerrylamos on 2010-08-01
Thanks for your efforts.  

This is i845G on IBM ThinkCentre A30. running Maverick:
Linux version 2.6.35-13-generic (buildd@palmer) (gcc version 4.4.5 20100723 (prerelease) (Ubuntu/Linaro 4.4.4-7ubuntu3) ) #18-Ubuntu SMP Sat Jul 31 01:45:46 UTC 2010
Been running fine with i915.modeset=0 and Driver Vesa.  As far as I'm concerned as an ordinary user that combination would be a good solution.

I followed directions to put on the legacy i8xx driver, then:

i915.modeset=1 booted, that's what I'm using here.

nomodeset as suggested in this forum booted to blank screen. I've got i915_error_state, Xorg.0.log, dmesg in a tar file I could add to a launchpad bug - any bug in particular, example #541492?

i915.modeset=0 booted to blank screen.  I've got a tar for that one too.

Thanks again,

Jerry

---

### Post by jerrylamos on 2010-08-01
Just for giggles, on this i845G with i915.modeset=1, I did Ctrl-Alt-F1 and got the typical KMS screen, logged in O.K., then switched back to Gnome GDM.  Success!  Entering this reply now.

I've never been able to do that with i845 before.

Thanks again,

Jerry

p.s. haven't compared speed with vesa yet.  I'm just glad it's working.

---

### Post by Starks on 2010-08-01
No negative side-effects on i945gm. 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS,  943/940GML Express Integrated Graphics Controller (rev 03) 

How does this solution differ from Glasen's KMS-based solution?

---

### Post by jerrylamos on 2010-08-01
What's amazing, with the same level of Maverick in my previous post, ati radeon mobility 7500 won't boot with KMS on.  I have to use radeon.modeset=0 for that one.  ati radeon Xpress 200 does work with KMS....

Obviously we need a lot more combinations of hardware and Ubuntu to test....

Jerry

---

### Post by Catharsis on 2010-08-01
> **Starks said:**
> No negative side-effects on i945gm. 

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS,  943/940GML Express Integrated Graphics Controller (rev 03) 

How does this solution differ from Glasen's KMS-based solution?

This legacy driver reverts back to before KMS was introduced (and when i8xx used to work, using UMS). David Vetter's GTT Incoherency Patch just tries to fix the GTT memory mapping in the KMS side, but it's still not a great fix and also doesn't solve the problem for everyone.

Thanks for testing.

---

### Post by Catharsis on 2010-08-01
> **jerrylamos said:**
> Thanks for your efforts.  

This is i845G on IBM ThinkCentre A30. running Maverick:
Linux version 2.6.35-13-generic (buildd@palmer) (gcc version 4.4.5 20100723 (prerelease) (Ubuntu/Linaro 4.4.4-7ubuntu3) ) #18-Ubuntu SMP Sat Jul 31 01:45:46 UTC 2010
Been running fine with i915.modeset=0 and Driver Vesa.  As far as I'm concerned as an ordinary user that combination would be a good solution.

I followed directions to put on the legacy i8xx driver, then:

i915.modeset=1 booted, that's what I'm using here.

nomodeset as suggested in this forum booted to blank screen. I've got i915_error_state, Xorg.0.log, dmesg in a tar file I could add to a launchpad bug - any bug in particular, example #541492?

i915.modeset=0 booted to blank screen.  I've got a tar for that one too.

Thanks again,

Jerry

I got a blank screen on my i855 too. I'm curious if anyone can boot using it.

Did you get a chance to look over the logs? The system never generated an Xorg.0.log for my UMS boot, so I'm curious if the Xorg.0.log you captured is from the previous boot (just check the kernel parameters at the top of the log).

Just remember to post your results to the Ubuntu-x list once you're done testing. The devs don't read forums, so I'd hate for your efforts to be in vain :)

---

### Post by jerrylamos on 2010-08-02
i845G booted fine, default linux line just "quiet", no xorg.conf so it is defaulting to the i8xx Legacy Driver.

It's running KMS by default and I can switch to command line with Ctrl-Alt-F1, log in, exit, and switch back to the Gnome gdm with Ctrl-Alt-F7 just like it is supposed to.

Now this is Maverick Alpha 2 2.6.35-13 which has some growing pains example gedit starts with some errors:
(gedit:1463): GLib-GObject-WARNING **: invalid (NULL) pointer instance
(gedit:1463): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
and then goes on to work O.K.

I haven't done a whole lot of testing but this is the best intel functioning since Intrepid with its compiz troubles.  I don't use compiz so I don't care about that.

Thanks, Jerry

---

### Post by jerrylamos on 2010-08-04
I think this is the driver I'm successfully using:
Version: 2:2.12.0+legacy20100714-0~raof2
for whatever that might mean to someone....Alpha 3's coming up, run for the trenches.

Jerry

---

### Post by Catharsis on 2010-08-04
> **jerrylamos said:**
> I think this is the driver I'm successfully using:
Version: 2:2.12.0+legacy20100714-0~raof2
for whatever that might mean to someone....Alpha 3's coming up, run for the trenches.

Jerry

I thought you said it booted to a black screen when you disabled KMS. Is that not true anymore??

---

### Post by dmizer on 2010-08-04
> **Catharsis said:**
> Source: [https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000905.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000905.html)


Source: [https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000909.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-July/000909.html)

**[size=+1]Instructions[/size]**

[list=1]
[*]Remove any graphics workarounds that might interfere with testing. The common i8xx workarounds you might have enabled are listed [here](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

[*]Install the xserver-xorg-video-intel and libdrm packages:
```
sudo add-apt-repository ppa:raof/aubergine
sudo apt-get update && sudo apt-get upgrade
```
Note: This will leave libdrm-nouveau1 as held-back. DO NOT force that upgrade; it will break things.

[*]i8xx users should test the UMS codepath by adding 'nomodeset' or 'i915.modeset=0' (they do they same thing) to their GRUB_CMDLINE_LINUX_DEFAULT line:
```
gksudo gedit /etc/default/grub
sudo update-grub
```
All other Intel graphics users should test for regressions using the default KMS path.

[*]Test the driver for a few days. Important testcases include changes in: the boot behavior, frequency of freezes, playing a video file in Totem, watching a YouTube video, and enabling Full Screen in either Totem or YouTube.

[*]Subscribe to the [Ubuntu-x Mailing List](https://lists.ubuntu.com/mailman/listinfo/ubuntu-x). Then post your results to the list by sending an email to [email]ubuntu-x@lists.ubuntu.com[/email] with your experiences using the new driver as well as your specific chipset (lspci | grep VGA). If new or different bugs are experienced, it would be useful to find them in Xorg.0.log or dmesg, and then attach those log files to the email along with their explanations.
[/list]

Thank you for taking the time to help improve Ubuntu. i8xx graphics issues were one of the major bugs in the Lucid Lynx release and caused many of us with these chipsets to either downgrade or change distros. So for those with these chipsets, this is your opportunity to help solve the i8xx issues and get a workable, usable Ubuntu system once again. Happy testing, and good luck!

Unfortunately this driver is not working for my system.

Machine boots. I hear the logon drums several times, then the whole machine locks. I am unable to SSH in, and the machine does not respond to ping.

From lspci ->
```
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
```

Currently running Lucid.

---

### Post by Catharsis on 2010-08-04
Yeah, I'm having a feeling that it freezes on everyone at boot. Just don't forget to post those results to the ubuntu-x mailing list.

---

### Post by jerrylamos on 2010-08-05
> **Catharsis said:**
> Yeah, I'm having a feeling that it freezes on everyone at boot. Just don't forget to post those results to the ubuntu-x mailing list.

Does not freeze at boot for me on Maverick Alpha 2, i845G video graphics using driver Version: 2:2.12.0+legacy20100714-0~raof2 as installed at the beginning of this thread.  Runs fine for what I do.

My boot line in /etc/default/grub only says "quiet" and I have no xorg.conf.

Various combinations do not work, blank screen, with i915.anything or modeset/nomodeset.  I don't do any of those with the i8xx legacy driver.  They break on this pc.

Do note xorg.conf specifying Driver "vesa" and i915.modeset=0 do work, but I prefer the i8xx legacy driver defaulting on linux boot line and defaulting on /etc/X11.  I haven't tried any video performance tests.

Alpha 3, here it comes....

Jerry

---

### Post by jerrylamos on 2010-08-05
> **Catharsis said:**
> Yeah, I'm having a feeling that it freezes on everyone at boot. Just don't forget to post those results to the ubuntu-x mailing list.

Does not freeze at boot for me on Maverick Alpha 2, i845G video graphics using driver Version: 2:2.12.0+legacy20100714-0~raof2 as installed at the beginning of this thread.  Runs fine for what I do.

My boot line in /etc/default/grub only says "quiet" and I have no xorg.conf.

Various combinations do not work, blank screen, with i915.anything or modeset/nomodeset.  I don't do any of those with the i8xx legacy driver.  They break on this pc.

Do note xorg.conf specifying Driver "vesa" and i915.modeset=0 do work, but I prefer the i8xx legacy driver defaulting on linux boot line and defaulting on /etc/X11.  I haven't tried any video performance tests.

Alpha 3, here it comes....

Jerry

---

### Post by dmizer on 2010-08-05
> **Catharsis said:**
> Yeah, I'm having a feeling that it freezes on everyone at boot. Just don't forget to post those results to the ubuntu-x mailing list.

I will, but first I'd like my machine back. How can I revert? "Occasionally crashing" is far far better than "doesn't work at all" :)

---

### Post by Catharsis on 2010-08-06
> **jerrylamos said:**
> Does not freeze at boot for me on Maverick Alpha 2, i845G video graphics using driver Version: 2:2.12.0+legacy20100714-0~raof2 as installed at the beginning of this thread.  Runs fine for what I do.

My boot line in /etc/default/grub only says "quiet" and I have no xorg.conf.

Various combinations do not work, blank screen, with i915.anything or modeset/nomodeset.  I don't do any of those with the i8xx legacy driver.  They break on this pc.

Do note xorg.conf specifying Driver "vesa" and i915.modeset=0 do work, but I prefer the i8xx legacy driver defaulting on linux boot line and defaulting on /etc/X11.  I haven't tried any video performance tests.

Alpha 3, here it comes....

Jerry

You're not testing the legacy driver unless you're booting with nomodeset or i915.modeset=0. So yes, the legacy driver is booting you to a blank screen.

The "legacy driver" we're testing is just a git snapshot of the most recent xserver-xorg-video-intel with the addition of the UMS code from before GEM was introduced (Jaunty-ish). If you want the same KMS experience, all you have to do is enable the xorg-edgers PPA for that; it has nothing to do with the legacy part of the driver, since the legacy part is the UMS part.

---

### Post by Catharsis on 2010-08-06
> **dmizer said:**
> I will, but first I'd like my machine back. How can I revert? "Occasionally crashing" is far far better than "doesn't work at all" :)

Enter grub by holding down Shift while booting, select your regular kernel and press 'e' to edit it. Then replace 'i915.modeset=0' with 'i915.modeset=1'. That should get you to a desktop.

Then install the ppa-purge package from xorg-edgers and use it to remove the xorg-edgers and raof/aubergine PPAs:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update && sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
sudo ppa-purge ppa:raof/aubergine
```

Then you can make the i915.modeset=1 change permanent by editing /etc/default/grub again and replacing i915.modeset=0 with i915.modeset=1:
```
gksudo gedit /etc/default/grub
sudo update-grub
```

---

### Post by Starks on 2010-08-09
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ4NQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ4NQ)

I got referenced in a Linux tabloid.

"Someone that had tested out this UMS driver with a newer Intel 945GM IGP reported no apparent regressions."

---

### Post by jerrylamos on 2010-08-09
> **Catharsis said:**
> You're not testing the legacy driver unless you're booting with nomodeset or i915.modeset=0. So yes, the legacy driver is booting you to a blank screen.


Catharsis, this is what I have running:

Maverick A3
jerry@linux:~$ cat /proc/version
Linux version 2.6.35-14-generic (buildd@rothera) (gcc version 4.4.5 20100728 (prerelease) (Ubuntu/Linaro 4.4.4-8ubuntu1) ) #19-Ubuntu SMP Mon Aug 2 01:43:35 UTC 2010

jerry@linux:~$ ./IntelDriver
dpkg -s xserver-xorg-video-intel | grep Version
Version: 2:2.12.0+legacy20100802-0~raof1

jerry@linux:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

less /boot/grub/grub.cfg
...
  linux   /boot/vmlinuz-2.6.35-14-generic root=UUID=14be8439-e5cd-4bd9-b65c-78b315e2020b ro   quiet

Looks to me like the legacy driver is running.  How do you verify it on your setup?

By the way, Ctrl-Alt-F1 gets the little bitty KMS print where I can log on, do something, exit, and Ctrl-Alt-F7 back to this message.

Jerry

---

### Post by Catharsis on 2010-08-09
> **Starks said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=ODQ4NQ](http://www.phoronix.com/scan.php?page=news_item&px=ODQ4NQ)

I got referenced in a Linux tabloid.

"Someone that had tested out this UMS driver with a newer Intel 945GM IGP reported no apparent regressions."

Yeah, I saw that too. We're all famous now :P

---

### Post by Catharsis on 2010-08-09
> **jerrylamos said:**
> Catharsis, this is what I have running:

Maverick A3
jerry@linux:~$ cat /proc/version
Linux version 2.6.35-14-generic (buildd@rothera) (gcc version 4.4.5 20100728 (prerelease) (Ubuntu/Linaro 4.4.4-8ubuntu1) ) #19-Ubuntu SMP Mon Aug 2 01:43:35 UTC 2010

jerry@linux:~$ ./IntelDriver
dpkg -s xserver-xorg-video-intel | grep Version
Version: 2:2.12.0+legacy20100802-0~raof1

jerry@linux:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

less /boot/grub/grub.cfg
...
  linux   /boot/vmlinuz-2.6.35-14-generic root=UUID=14be8439-e5cd-4bd9-b65c-78b315e2020b ro   quiet

Looks to me like the legacy driver is running.  How do you verify it on your setup?

By the way, Ctrl-Alt-F1 gets the little bitty KMS print where I can log on, do something, exit, and Ctrl-Alt-F7 back to this message.

Jerry

Yes, the -intel driver is running. But with only 'ro quiet', you're booting into KMS which is the exact same thing as the current -intel driver in Maverick. The only thing that got legacy-fied is the addition of the UMS path, which is only activated if you force it with either 'nomodeset' or 'i915.modeset=0'. Since you're doing neither, you're booting into the regular KMS, which hasn't been touched in this driver compared to the current -intel.

---

### Post by Starks on 2010-08-09
If that's the case, then I'd like to amend my statement that the i945GM works perfectly with the  legacy driver. It does, but only when using KMS. 

Using nomodeset leads to a blank screen.

---

### Post by jerrylamos on 2010-08-10
> **Starks said:**
> If that's the case, then I'd like to amend my statement that the i945GM works perfectly with the  legacy driver. It does, but only when using KMS. 

Using nomodeset leads to a blank screen.

Starks,

Same here.  Used to be on some previous versions i915.modeset=0 enabled operation O.K., and without KMS.

Lately on Maverick, i915.modeset=0, i915.modeset=1, nomodeset all lead to blank screen.  Something's busted in the modeset code.

Jerry

---

### Post by jerrylamos on 2010-08-11
i8xx legacy driver kinda slow on this kinda slow 2.0 gHz Celeron integrated video graphics intel i845G:

GtkPerf   
i8xx________51.86 seconds 
A3 default___43.75 seconds

i8xx driver:

2:2.12.0+legacy20100802-0~raof1

Default Maverick A3 driver:

2:2.11.0-1ubuntu2

They are both running with KMS on.

Jerry

---

### Post by Starks on 2010-08-11
*never mind*

---

### Post by Catharsis on 2010-08-12
> **jerrylamos said:**
> Starks,

Same here.  Used to be on some previous versions i915.modeset=0 enabled operation O.K., and without KMS.

Lately on Maverick, i915.modeset=0, i915.modeset=1, nomodeset all lead to blank screen.  Something's busted in the modeset code.

Jerry

I'd make sure there's nothing else toggling KMS for you. i915.modeset=1 is the default setting in Maverick, so explicitly setting that shouldn't change anything at all. You're saying the legacy driver boots correctly with the default mode settings, but not when you set i915.modeset=1? Did you make any initramfs scripts or anything?

---

### Post by jerrylamos on 2010-08-12
> **Catharsis said:**
> I'd make sure there's nothing else toggling KMS for you. i915.modeset=1 is the default setting in Maverick, so explicitly setting that shouldn't change anything at all. You're saying the legacy driver boots correctly with the default mode settings, but not when you set i915.modeset=1? Did you make any initramfs scripts or anything?

Catharsis, 

I'm a bit reluctant to put the "legacy" driver back on since it took some fiddling to get it off, including a couple cycles of "repair broken packages" and a few reboots.  I've wound up with 2:2.11.0-1ubuntu2 running O.K. with "quiet" on Maverick A3.  Taylor put some instructions on Ubuntu-X digest about how to get the legacy driver off, so I could maybe try legacy again.  On this Intel Corporation 82845G/GL[Brookdale-G]/GE I seem to be running, so I'm not sure what the legacy driver is supposed to be doing for me?

Thanks for everyone's efforts on X.

Jerry

---

### Post by slaeyer on 2010-08-20
I can confirm the driver working under Ubuntu 10.04.1 with an uptime of 3+ days.  Video playback both in flash and totem remained stable at all resolutions.  Left running after video playback test was glxgears, glmatrix screensaver (when screensaver kicked in) and world community grid full time.  Uptime was checked every 2 or so hours during the day and left alone at nite.  KMS was set to i915.modeset=1 for testing but seemed stable when turned off.

Output of lspci -nn | grep VGA:

=============
00:02.0 VGA compatible controller [0300]:
Intel Corporation 82845G/GL[Brookdale-G]/
GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
=============

I have noticed absolutely no regressions and 3D performance seemed stable at all times.  I'd say this is a good fix!

---


---
title: "Install from USB key gets worse and worse"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by recluce on 2011-03-03
With alpha1 and alpha2, the installation from the LiveCD crashed at about 75% complete when run from an USB key. Search this forum and you get a number of reports and links to the launchpad bug reports.

These bugs are closed, "fix commited". Maybe so, I couldn't tell. Because alpha3 doesn't even get that far. It crashes at about 25% with the following error log in the syslog:

```

Mar  3 21:54:35 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
Mar  3 21:54:35 ubuntu plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
Mar  3 21:54:35 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Mar  3 21:54:35 ubuntu ubiquity: dpkg: warning: parsing file '/target/var/lib/dpkg/available' near line 35967 package 'virtualbox-3.0':
Mar  3 21:54:35 ubuntu ubiquity:  error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
Mar  3 21:54:35 ubuntu ubiquity: dpkg: warning: parsing file '/target/var/lib/dpkg/available' near line 37262 package 'virtualbox-2.2':
Mar  3 21:54:35 ubuntu ubiquity:  error in Version string '2.2.4-47978_Ubuntu_jaunty': invalid character in revision number
Mar  3 21:54:36 ubuntu ubiquity: dpkg: unrecoverable fatal error, aborting:
Mar  3 21:54:36 ubuntu ubiquity:  syntax error: unknown group 'postdrop' in statoverride file
Mar  3 21:54:36 ubuntu plugininstall.py: Traceback (most recent call last):
Mar  3 21:54:36 ubuntu plugininstall.py:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 739, in do_install
Mar  3 21:54:36 ubuntu plugininstall.py:     if not cache.commit(fetchprogress, installprogress):
Mar  3 21:54:36 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
Mar  3 21:54:36 ubuntu plugininstall.py:     return func(*args, **kwds)
Mar  3 21:54:36 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 427, in commit
Mar  3 21:54:36 ubuntu plugininstall.py:     res = self.install_archives(pm, install_progress)
Mar  3 21:54:36 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
Mar  3 21:54:36 ubuntu plugininstall.py:     return func(*args, **kwds)
Mar  3 21:54:36 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 390, in install_archives
Mar  3 21:54:36 ubuntu plugininstall.py:     res = install_progress.run(pm)
Mar  3 21:54:36 ubuntu plugininstall.py:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 381, in run
Mar  3 21:54:36 ubuntu plugininstall.py:     res = pm.do_install(self.write_stream.fileno())
Mar  3 21:54:36 ubuntu plugininstall.py: SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
Mar  3 21:54:36 ubuntu plugininstall.py: 
Mar  3 21:54:36 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Mar  3 21:54:36 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Mar  3 21:54:36 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Mar  3 21:54:36 ubuntu plugininstall.py: broken packages after installation:
 
```

The GUI installer claims it will try to continue to install, but aborts right away. And yes, the message about broken packages is empty. The installation neither managed to write initrd nor the home directory, so cannot be booted at all.

Why do I get the impression that Ubuntu desperately needs to stop adding new gimmicks and concentrate on debugging and stability for a couple of releases?

Besides the general rant and expression of disappointment above, any ideas what went wrong here? 

And what the heck are those entries about "jaunty", which is still installed on a different partition of that drive? The natty installer should leave the jaunty installation well alone...

---

### Post by cariboo on 2011-03-03
Are you checking to see if the md5sum is correct, I installed from yesterdays iso, and aside from the fact that one of the hard drives in my system died and grub couldn't be installed to it, the install went well. 

Long live Maxtor hard drives:)

---

### Post by jerrylamos on 2011-03-03
?  I've done two installs from USB stick from the 02 March Daily Build onto ati radeon Xpress 200.  One install went to a hard drive, the other to a USB hard drive with four partitions.  Unity 3D works.  

Also two more installs from a CD from same .iso onto ati radeon mobility 7500 and intel i845.  Unity 3D doesn't work because of fancy code in Compiz so Classic desktop no effects work O.K.

Now of course Compiz would crash and I'd report this to launchpad.  On one of the installs the T40 Thinkpad I got a purple blotch screen with cursor.  Did:
Ctrl-Alt-F1
sudo service gdm stop
sudo service gdm start

After a bunch of hard drive accesses login came up.  

Now I did have an older USB stick which didn't work.

Jerry

---

### Post by quids on 2011-03-03
Ubuntu has worked fine for me all through Alpha releases.
Kubuntu GUI installer has worked for the first time in Alpha 3, although it was very slow loading up on my netbook

---

### Post by recluce on 2011-03-03
> **cariboo907 said:**
> Are you checking to see if the md5sum is correct, I installed from yesterdays iso, and aside from the fact that one of the hard drives in my system died and grub couldn't be installed to it, the install went well. 

Long live Maxtor hard drives:)

I downloaded the alpha3 release, not a daily build.

I just double-checked the MD5 sum both on the download and the image on the USB stick, they are all correct.

I never doubted that the natty install works for some people, it just seems to fail for a significant number. Any ideas about the log entries I posted?

---

### Post by recluce on 2011-04-02
With beta1 (the "official" release), the natty installer still crashes about 75% through the installation for me, run from USB. There are quite a number of bugs filed about this, btw.

However, the silence on launchpad is deafening, as far as developers are concerned. The forum here is no help either.

I guess it is time for me to sign off from the "natty" development releases and hope for improvement for Ubuntu 11.10. I sincerely hope that the developers will start to focus on stability and usability again, at least for 12.04 LTS. Otherwise, I really fear for Ubuntu in the long run!

---

### Post by bennachie on 2011-04-02
I've had no problems when installing Beta1 directly from USB sticks with persistence disabled. However, for some reason, the record has been a bit more patchy with persistence-enabled sticks, or when attempting to install from a running live image - in the latter case, all my computers have at least 2GB of RAM, so that seems unlikely to be the problem.

I assume that you have disconnected your machine from the Internet before commencing the installation. In my experience, even if you haven't actually ticked the boxes asking for updates and/or the installation of third-party software, leaving an Internet connection in place can cause lengthy delays, or even complete failure of the installation process. The difficulty seems mostly to affect pre-release systems.

---

### Post by Quackers on 2011-04-02
I agree with bennachie, although that hasn't been a problem for me previously. My first install of beta1 failed due to broken packages!, so I tried without internet and it flew through! On checking in gparted after the first install failed, it reported that only 1420MB was used (read installed) during the first attempt!
Incidentally, I never got alpha3 to install successfully, although I wasn't using usb.

---

### Post by recluce on 2011-04-03
> **Quackers said:**
> I agree with bennachie, although that hasn't been a problem for me previously. My first install of beta1 failed due to broken packages!, so I tried without internet and it flew through! On checking in gparted after the first install failed, it reported that only 1420MB was used (read installed) during the first attempt!
Incidentally, I never got alpha3 to install successfully, although I wasn't using usb.

I couldn't get alpha3 to install either - not even from CD. 

Thanks to you and "bennachie" for the tip with the internet connection disabled. I will try that as a final effort with natty, even though it seems counter-intuitive at first.

---

### Post by Quackers on 2011-04-03
Good luck then :-)

---

### Post by Anduu on 2011-04-03
I made several attempts before I successfully did a clean Natty install.

Tried first using a usb key and failed with the errors you get.

Second time I said heck with it and burned the daily iso.Burned at lowest speed and ran the install from an external usb dvd drive...same errors.

Finally popped the cd in my internal dvd drive and it installed without a hitch.

I haven't tried lately...ie this last week...but before the Beta there was definitely and issue with installing from any usb device.

---

### Post by recluce on 2011-04-06
I tried to install with the internet connection disabled - now I get a different installer crash.

Relatively early (after asking for user settings to import), the migration assistant crashes with the following message (couldn't cut and paste, as a requester blocked access to the "details" window):

"cannnot unmount /dev/sdb2 -- /dev/sdc1 is mounted over it on the same point"

/dev/sdb2 is my Lucid root-partition and /dev/sdc1 is my Windows System partition (not Windows partition). Installation target is /dev/sdd10 (root) and /dev/sdd9 (home).

Funny thing is, I made sure that all the check-boxes for the import of user settings are unchecked, so the "Migration Assistant" should have done or tried nothing whatsoever.

Actually, I am getting quite mad that the installer is trying to do ANYTHING on partitions it has no business with.

I suggest the Ubuntu developpers should get the installer fixed for 11.10, before adding any new gee-whiz-bang features of dubious value. Right now, the installer is a can of worms that I will not open again for 11.04 - if it starts fiddling around on partitions it is not supposed to touch, who knows what it might break there?

One final question: are they actually intending to release the installer in its current state? If so, the forums will be a zoo.

---


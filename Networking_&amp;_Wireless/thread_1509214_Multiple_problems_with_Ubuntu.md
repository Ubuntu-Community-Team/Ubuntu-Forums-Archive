---
title: "Multiple problems with Ubuntu"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by DutchPrisoner on 2010-06-14
I started noticing problems awhile back with my system being unusually slow.  Then I noticed that error messages would occur when I would attempt to do automatic updates.  When I tried to upgrade to the new 10.04 release, again error messages would occur.

But now the major problem is that I am unable to get online at all.  My wireless connection is not working.  Help!  Keep in mind that since I can't get online, I won't be able to share my logs to show where the errors may be.  If someone could first help me to do something to at least get online, then I can share logs to find the other problems.

Thanks!

---

### Post by rukiaEnix on 2010-06-14
if you are using wireless, now use wire :p, or the wire connection doesn't work either?
and about the updates I think that sometimes they give more problems instead of solving them. I say it in experience -.-

---

### Post by DutchPrisoner on 2010-06-14
OK, so I was able to get my computer online with a wired connection.  What information do I need to provide for assistance  in solving my problem?

---

### Post by DutchPrisoner on 2010-06-14
Update to original message: I now have this computer online with a wired connection.  To repeat the problem, I started  noticing problems awhile back with my system being unusually slow.  Then  I noticed that error messages would occur when I would attempt to do software updates.  I think I have Ubuntu 9.10, although I think it might also have Xubuntu on the system too.  My brother did the install and I'm not sure.

At any rate, now the major problem is that I am unable to get online at all with a wireless connection.  Help!  Furthermore, I downloaded a copy of Ubuntu 10.04 to a disk.  When I run the computer with the Ubuntu 10.04 disk the same problems occur -- no ability to get wireless connection.

Thoughts?

---

### Post by rukiaEnix on 2010-06-14
mmm now this is weird. is your wireless an atheros?

---

### Post by Bucky Ball on 2010-06-14
Not weird. Not much chance of getting wireless running the Live CD if you need to install drivers.

Open a terminal (Applications->Accessories->Terminal) and paste this is:

```
sudo apt-get update
```

Then this:

```
sudo apt-get upgrade
```

Now go to System->Administration->Hardware Drivers. Do you see anything in there pertaining to wireless?

---

### Post by DutchPrisoner on 2010-06-15
> **Bucky Ball said:**
> Not weird. Not much chance of getting wireless running the Live CD if you need to install drivers.

Open a terminal (Applications->Accessories->Terminal) and paste this is:

```
sudo apt-get update
```Then this:

```
sudo apt-get upgrade
```Now go to System->Administration->Hardware Drivers. Do you see anything in there pertaining to wireless?

OK, so I followed your instructions and that worked to get my wireless connected.  Thank you! I went to Hardware Drivers and the Broadcom wireless drivers were not activated.  I activated them.

However, the NVIDIA accelerated graphics driver is not activated and when I try to activate it I get this error message:

Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.

Any further help you can offer on that?

---

### Post by Bucky Ball on 2010-06-15
You could try installing Envy from the repositories. That is an interface to help install (and remove) nvidia and ati graphics drivers. It sometimes works a treat and others causes more problems than it fixes! I would perhaps give that a go. It will also re-write your xorg.conf which is the problem you have at the moment I think. If you are using 10.04, I am not much help as I don't use it and some things have changed since 8.04 LTS.

---

### Post by DutchPrisoner on 2010-06-16
> **Bucky Ball said:**
> You could try installing Envy from the repositories. That is an interface to help install (and remove) nvidia and ati graphics drivers. It sometimes works a treat and others causes more problems than it fixes! I would perhaps give that a go. It will also re-write your xorg.conf which is the problem you have at the moment I think. If you are using 10.04, I am not much help as I don't use it and some things have changed since 8.04 LTS.

Since the earlier fix to get the drivers working, my problems have grown. Suddenly, I am now unable to log on at all to my system using the installed 9.10 version.  Error messages appear and I can't get into the Ubuntu display screen at all.  Right now I am running my system on the 10.04 disk but error messages appear when I attempt to install the wireless drivers through 10.04 (using the commands given by Bucky Ball above).  The main problem I have is that I have a lot of files attached to my 9.10 system (backed up elsewhere, but don't want to have to go to the backup)..  So my understanding is that I can't install 10.04 and retain my files on the 9.10 system.  Pretty sure I need to get it running through 9.10.

Any advice as to what I can do?  o you need the log that appears when my computer starts up (and won't start?)

---

### Post by DJonsson2008 on 2010-06-16
If you can get to the command line then you should be able to fix this.

it sounds like the Xorg.conf files need to be rolled back to work with default vesa drivers so you can
get to your desktop.

/etc/X11/xorg.conf is the file that controls your video drivers
if you get on the command line and navigate to the directory /etc/X11
and type ls you can see if any backup of your xorg.conf exists there.

you can then try copying the older copy of xorg.conf 

its said that deleting xorg.conf will revert the machine to default
video settings, i would not try that without backing up xorg.conf first
to something like xorg.conf.bak.

NOTE: you don't need Nvidea drivers to get an entry level workable higher resolution.

Then by all means focus on your connectivity issues first, before further rock and roll with Nvidea.

---


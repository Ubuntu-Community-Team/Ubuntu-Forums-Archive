---
title: "If I upgrade from 10.04 to 10.10 will i lose all my configuration ?"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Tracy177 on 2010-09-03
im talking about grub2 and burg will i lose my configuration ?  and what about my splash screnn from plymouth package?

my sound card didn't work out of the box in 10.04 i had to download 200mb of data to get it working will i lose everything would i need to reinstall sound card again?

graphic card ? would i need to reinstall drivers ?

what about conky? took me about a week to make it working and look how i want will i lose whole config ? lua and cairo ?

i also have installed many many different packages will i lose them ? and have to reinstall everything ?

what about my compiz config ?? took me a while to make it be configured properly and work properly will i lose everything ?

desktop themes( custom made) ?

---

### Post by Paddy Landau on 2010-09-03
I don't know the answers, but I will say that (1) it "should" keep all your configurations, and (2) any upgrade has a (small) chance of failure.

Therefore, the easy thing is to do a complete backup.

I recommend [CloneZilla]("http://www.clonezilla.org/"), which you can use to back up your *entire* hard disk just before you upgrade. If your upgrade fails, simply restore the hard disk using CloneZilla. You'll need an external hard drive to achieve this.

In addition to the CloneZilla backup, also do your usual backups of your data.

*EDIT* If you need a stable system, you may be wise not to upgrade until the next LTS comes along in a couple of years.

---

### Post by stmiller on 2010-09-03
You are probably safe to upgrade, but always back up your home directory first to DVD or another hard drive.

---

### Post by wilee-nilee on 2010-09-03
Maverick is in beta release you should be prepared for anything to happen. It is best to not run it alone as a single OS right now, if you want stability assured.

I always install the 1st ISO of the new testing along side a few other OS.

---

### Post by oldfred on 2010-09-03
All your user settings are in /home so you will not lose those if you have a separate /home and do not reformat it or backup and reinstall your /home with all the hidden files.

But system settings that are in /etc will be overwritten unless you separately back those up. Some say back up all of /etc but I have had trouble where old settings created bigger issues. It is best if you know what files in /etc you have modified and separately back those up.

You can also make a list of programs you have installed and easily reinstall the latest versions from that list.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by bodhi.zazen on 2010-09-04
> **Tracy177 said:**
> im talking about grub2 and burg will i lose my configuration ?  and what about my splash screnn from plymouth package?

my sound card didn't work out of the box in 10.04 i had to download 200mb of data to get it working will i lose everything would i need to reinstall sound card again?

graphic card ? would i need to reinstall drivers ?

what about conky? took me about a week to make it working and look how i want will i lose whole config ? lua and cairo ?

i also have installed many many different packages will i lose them ? and have to reinstall everything ?

what about my compiz config ?? took me a while to make it be configured properly and work properly will i lose everything ?

desktop themes( custom made) ?

You will not loose your configuration, but as has been pointed out, 10.10 is in beta and so your system may fail.

If you are not familiar with Linux / Ubuntu I advise you either dual boot 10.04 and 10.10 or wait until 10.10 is released.

---

### Post by 3rdalbum on 2010-09-04
You may be given the option to retain your system-wide customizations on a case-by-case basis for each package.

Burg will probably be overwritten. Your packages will be retained and upgraded automatically. Your home directory will be untouched. 10.10 may include a sound driver for you, but if not you would need to reinstall the old driver.

---


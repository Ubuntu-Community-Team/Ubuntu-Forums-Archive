---
title: "Python 2.7.1 removal"
date: 2010-12-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-12-08
this new package want to deinstall nvidia-common & nvidia-settings, and some others too.

So take care.

---

### Post by philinux on 2010-12-08
> **dino99 said:**
> this new package want to deinstall nvidia-common & nvidia-settings, and some others too.

So take care.

Just got the email from devel announcements.
> Tomorrow, Wednesday December 8, we'll change the default Python version in
Natty from 2.6 to 2.7.

This will be followed by a series of no-change uploads to rebuild packages
with Python 2.7.  Some parts of the archive will be uninstallable or not
upgradeable for a few days; please wait with upgrades until the rebuilds are
done, and for the next two days, also avoid bug reports about upgrade
problems.

If you find issues which are not temporary while the rebuilds are ongoing,
please report these in Launchpad, and tag them with `python27`.  We expect to
resolve the majority of such issues this year, with the remaining issues
addressed by the end of January.

If you want to help fix problems related to the Python 2.7 switch, please
submit merge proposals and requests by tagging issues with `python27'.
A ping to barry and doko on #ubuntu-devel is welcome.

Another goal for the natty release is to make the installation and removal of
python packages more robust.  This will result in some packaging changes.
Unless these changes are already made in Debian or coordinated with Debian,
please don't change the packaging.  We'll followup later how we will address
these issues.

   Barry Warsaw
   Matthias Klose

---

### Post by dino99 on 2010-12-08
wow, what a christmas gift !!!

We expect to resolve the majority of such issues this year, with the remaining issues addressed by the end of January.

---

### Post by philinux on 2010-12-08
> **dino99 said:**
> wow, what a christmas gift !!!

We expect to resolve the majority of such issues this year, with the remaining issues addressed by the end of January.

Yeah made me laugh then think ouch!

---

### Post by Quackers on 2010-12-08
Towards the end of last week there was an update which did some similar things (it removed nvidia settings) and I thought long and hard before running it. 
As I'm testing, though, I decided to run the update and reboot after it. I was relieved to see that it had no adverse effects at all on my system.
This update removes a whole host of things, including nvidia-common and nvidia-settings, as dino99 said. However, in the testing spirit :-) I ran the update and have just rebooted.
No adverse effects at all! :-)
But this is just one system - I can't vouch for yours!

---

### Post by dino99 on 2010-12-08
if you know how to swim under iced water, no problem :)

---

### Post by xebian on 2010-12-08
> **dino99 said:**
> this new package want to deinstall nvidia-common & nvidia-settings, and some others too.

So take care.

Because they depend on Python version not 2.7.1

---

### Post by Quackers on 2010-12-08
ROFL.
It's not the swimming, it's the breaking the surface ice to breath again :-) I don't want to snap my beak! :-)

I was a bit nervous though! I thought I may need to do some work to get the system back, but no! Perhaps I have been lucky, or perhaps the update just didn't do as much damage as I feared it would. I don't know.

---

### Post by coffeecat on 2010-12-08
Hmmm. Is this down to python?

apt-get dist-upgrade:

```
coffeecat@amd4-NattyAlpha:~$ sudo apt-get dist-upgrade
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 The following packages will be REMOVED 
   gnome-sudoku hplip libsyncdaemon-1.0-1 libubuntuone-1.0-1 
   openoffice.org-emailmerge pitivi python-farsight python-indicate 
   python-launchpad-integration python-papyon python-pygoocanvas 
   python-ubuntuone python-uno rhythmbox-ubuntuone-music-store software-center 
   telepathy-butterfly ubuntu-desktop ubuntu-sso-client ubuntuone-client 
   ubuntuone-client-gnome 
 The following packages will be upgraded: 
   computer-janitor computer-janitor-gtk gir1.0-freedesktop gir1.0-glib-2.0 
   indicator-application libappindicator0.1-cil libappindicator1 
   libcairo-gobject2 libcairo2 libgirepository1.0-1 libplist1 nvidia-common 
   python python-appindicator python-httplib2 python-minimal python-telepathy 
   telepathy-idle 
 18 upgraded, 0 newly installed, 20 to remove and 0 not upgraded. 
 Need to get 1,399 kB of archives. 
 After this operation, 14.7 MB disk space will be freed. 
 Do you want to continue [Y/n]?
```apt-get upgrade:

```
coffeecat@amd4-NattyAlpha:~$ sudo apt-get upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages have been kept back: 
   computer-janitor computer-janitor-gtk python python-minimal 
 The following packages will be upgraded: 
   gir1.0-freedesktop gir1.0-glib-2.0 indicator-application 
   libappindicator0.1-cil libappindicator1 libcairo-gobject2 libcairo2 
   libgirepository1.0-1 libplist1 nvidia-common python-appindicator 
   python-httplib2 python-telepathy telepathy-idle 
 14 upgraded, 0 newly installed, 0 to remove and 4 not upgraded. 
 Need to get 1,131 kB of archives. 
 After this operation, 254 kB of additional disk space will be used. 
 Do you want to continue [Y/n]?
```I thought dist-upgrade was safer than upgrade at this stage of the game. :|

I'm going to chicken out of either and have supper instead.

---

### Post by philinux on 2010-12-08
Coffeecat,

Install aptitude and use this.

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by coffeecat on 2010-12-08
@philinux, thanks. Interestingly, aptitude was already installed. I thought it was being left out of a default install now. Anyway, aptitude is giving me the same package list to upgrade as apt-get upgrade, but without telling me about the held-back packages. 

All very interesting. I shall now have supper. :)

---

### Post by Harry33 on 2010-12-08
> **dino99 said:**
> this new package want to deinstall nvidia-common & nvidia-settings, and some others too.
So take care.

There is no reason to install packages python and python-minimal yet.
No andvantages of such a procedure either.
Many important packages, like gimp, python-uno, screen-resolution-extra etc. still depend on python <2.7.
So if you upgrade python to 2.7.*, the packages mentioned will be removed.

And because screen-resolution-extra is removed, nvidia-settings depending on it, will also.
Likewise, because python-uno is removed, openoffice.org-emailmerge depending on it, will also. And so on.

But rebuilt packages (depending on python <2.8 ) I just mentioned are already uploaded and soon they can be upgraded too (and thus python is upgraded too).

This is very common during development phase alfa.

---

### Post by dino99 on 2010-12-09
Pay attention:

[http://ubuntuforums.org/showthread.php?t=1641151](http://ubuntuforums.org/showthread.php?t=1641151)

---


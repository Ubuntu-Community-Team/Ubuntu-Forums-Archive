---
title: "Is it now safe to upgrade a WUBI install from Lucid to Maverick?"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Terrycymru on 2010-09-30
The title says it all.

I am using legacy GRUB, not GRUB2, in my WUBI install of Lucid.
I am not clear whether the problems reported only refer to WUBI upgrades and GRUB2.

---

### Post by dino99 on 2010-09-30
this answer says it all: :P

wubi is for testing/playing not for working, so if you want something serious, make a real install.

---

### Post by oldfred on 2010-09-30
If you are using Ubuntu and like it, then it is time to go to a real install. Even the designer of wubi expects that:

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by Terrycymru on 2010-09-30
> **dino99 said:**
> this answer says it all: :P

wubi is for testing/playing not for working, so if you want something serious, make a real install.

Thanks dino99. So you don't know the answer to the question asked. 

WUBI has been rock solid for me for over 2 years. It suits me because it is very easily backed up and quickly reinstalled. I also use the GRUB menu for other frugal installs of Linux distros. But ...... I didn't start this thread to discuss the merits or otherwise of WUBI and frugal installs!

---

### Post by dino99 on 2010-09-30
read it again and again, you will understand it for sure, not so complicated :P

---

### Post by cariboo on 2010-09-30
According to the [release notes]("http://www.ubuntu.com/testing/maverick/beta"). It isn't recommended to upgrade a from Lucid wubi install to a Maverick wubi install.

---

### Post by Terrycymru on 2010-09-30
> **cariboo907 said:**
> According to the [release notes]("http://www.ubuntu.com/testing/maverick/beta"). It isn't recommended to upgrade a from Lucid wubi install to a Maverick wubi install.

Yes, the beta Release Notes referred to some bugs, at least one of which have now been fixed. It *appears* that the others were only relevant to GRUB2 and installs on partitions other than the Windows partition. This is what I am seeking clarification about.

---

### Post by bcbc on 2010-09-30
To answer the question, No. There is an unrelated (to wubi) upgrade bug with the gnome-keyring package that causes any upgrade to fail at this point in time. [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/651325](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/651325)

---

### Post by bcbc on 2010-09-30
> **bcbc said:**
> To answer the question, No. There is an unrelated (to wubi) upgrade bug with the gnome-keyring package that causes any upgrade to fail at this point in time. [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/651325](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/651325)

Just got notification that this bug has been fixed. So now it's totally safe to upgrade ;) 

Seriously, unless you are testing or there is something you need that is on 10.10 and not on 10.04, I wouldn't touch the beta with a bargepole.

---

### Post by Terrycymru on 2010-09-30
Many thanks for the clarification, bcbc. I'll take your advice and wait until after the final release. :)

---

### Post by tjeremiah on 2010-09-30
I use wubi as my real, work install and have been using it with 10.10 since September 4th. Works fine. I actually gave ubuntu a real partition space but something went wrong and I couldnt recover my data, so when it comes to ubuntu, i stay wubi for now. Wubi to me, even if its meant to not be use for long, works fine for long periods of time and I noticed no performance difference from wubi to a real install of ubuntu.

---

### Post by kansasnoob on 2010-09-30
In case someone else reads this, according to the RC Release Notes:

[https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Known%20issues](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Known%20issues)


> The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases. Investigation of the problems are ongoing #613288

Upgrading Wubi systems from 10.04 LTS is known to fail, and is not recommended at this time. #610898

---

### Post by bokgeneraal on 2010-10-01
Just so you know  I upgraded the wubi install of Intepid to Karmic. When I tried to uninstall Ubuntu from Windows Xp I couldn't. 
So be safe. Rather backup files and do fresh wubi install .:)

---


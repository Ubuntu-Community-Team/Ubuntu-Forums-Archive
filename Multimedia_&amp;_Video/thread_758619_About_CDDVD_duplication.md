---
title: "About CD/DVD duplication"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by satimis on 2008-04-18
Hi folks,


What will be the easy way duplicating CD/DVD on PC installed with only one CD/DVD writer. Command lines are preferred. TIA


B.R.
satimis

---

### Post by xc3RnbFO8P on 2008-04-18
You can use K3B.

---

### Post by cor2y on 2008-04-18
yep k3b , it will temporarily store the dvd on your harddrive then eject the disc it was copied from and ask you to then insert a blank one and close the drive.
Of course k3b isn't the only burning app that does this i believe gnome baker does this as well as does the new cd/dvd burning tool brasero but where k3b and brasero tops gnome baker is the ability to verify data after a burn, so you know if the burnt disc is good or not.

---

### Post by ACGarland on 2008-04-18
Incidently, it appears in Ubuntu 7.1 there may be a bug with k3b.

If you start k3b **before** inserting the CD you want to copy, then it works fine -- k3b will ask you to insert the source media and then say "use the same device for burning."

However, if you insert the source CD first and k3b isn't set up to auto-launch (e.g., you've set up 'browse non-blank CDs" as the default action), then when you start k3b and choose "copy CD", it lists the source media OK, but

1. The [Start] button remains disabled (you can't start the copy).  This is because...

2. The burn medium says "Please insert a blank CD..."

Basically, k3b seems to act as if the original image has already been read from the CD and is somewhere on the disk and thinks it is at the step of preparing to write the new image. (Having said that, the "[x] Read source image" checkbox is checked indicating somewhere in the logic it knows it hasn't.)

The workaround appears to be to always start k3b before inserting the CD (before the CD gets mounted).  Probably not a problem for many users if they don't change the default mount action for non-blank media since they'll get a dialog requesting whether to start k3b before the mount finishes.

---

### Post by satimis on 2008-04-18
Hi folks,


Thanks for your advice.


As curiosity I wonder whether it can be done on command lines.  I'm working on a server.  I won't install k3b on it but rather go to a workstation to do the job.


B.R.
satimis

---

### Post by cor2y on 2008-04-18
k3b and the rest are just frontend gui tools.
They use cmdline tools for burning like cdrdao, dvd+rw-tools, wodim.
Understanding how to do it without a gui will be challenging part.

---

### Post by satimis on 2008-04-18
> **cor2y said:**
> k3b and the rest are just frontend gui tools.

Yes, same as Firewall etc.


> 
They use cmdline tools for burning like cdrdao, dvd+rw-tools, wodim.

Wodim
[http://lwn.net/Articles/198781/](http://lwn.net/Articles/198781/)

cdrkit: Debian's fork of cdrtools
[http://lwn.net/Articles/198171/](http://lwn.net/Articles/198171/)

Tarball Index
[http://debburn.alioth.debian.org/](http://debburn.alioth.debian.org/)


$ apt-cache policy wodim```

wodim:
  Installed: 9:1.1.2-1ubuntu1
  Candidate: 9:1.1.2-1ubuntu1
  Version table:
 *** 9:1.1.2-1ubuntu1 0
        500 http://us.archive.ubuntu.com feisty-updates/main Packages
        100 /var/lib/dpkg/status
     9:1.1.2-1 0
        500 http://us.archive.ubuntu.com feisty/main Packages

```
It is running on this server.


$ apt-cache policy cdrkit```

W: Unable to locate package cdrkit

```
Whether it is included on Wodim?  Or Wodim means cdrkit:


$ apt-cache policy cdrkit-doc```

cdrkit-doc:
  Installed: (none)
  Candidate: 9:1.1.2-1ubuntu1
  Version table:
     9:1.1.2-1ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
     9:1.1.2-1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages

```
The doc hasn't been installed.


> 
Understanding how to do it without a gui will be challenging part.
I'm interested learning it.  Unfortunately there is no document for reference.


B.R.
satimis

---

### Post by andrew.46 on 2008-05-15
Hi,

For audio cds there is always cdrdao:

> **satimis said:**
> What will be the easy way duplicating CD/DVD on PC installed with only one CD/DVD writer. Command lines are preferred. TIA


I have just submitted a walkthrough for this:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

which may be of some assistance?

           Andrew

---

### Post by satimis on 2008-05-16
> **andrew.46 said:**
> Hi,

For audio cds there is always cdrdao:



I have just submitted a walkthrough for this:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

which may be of some assistance?
           

Hi Andrew,


Thanks for your walkthrough.


Can it work on data DVD and DVD installer?  TIA


B.R.
satimis

---

### Post by andrew.46 on 2008-05-16
Hi:

> **satimis said:**
> 
Thanks for your walkthrough.
Can it work on data DVD and DVD installer?  TIA

There are better tools or this. Have a look at [Making Copies of Your Favourite Linux Distro]("http://www.andrews-corner.org/burning.html#distro") This deals with dd, growisofs and cdrecord (by default this is wodim in ubuntu).

    Andrew

---

### Post by satimis on 2008-05-17
> **andrew.46 said:**
> Hi:



There are better tools or this. Have a look at [Making Copies of Your Favourite Linux Distro]("http://www.andrews-corner.org/burning.html#distro") This deals with dd, growisofs and cdrecord (by default this is wodim in ubuntu).

Hi Andrew,


Thanks for your URL.


Can I do it on the fly w/o creating ISO image?  Pipe command may help.  But I haven't figured out how to change DVD.


B.R.
satimis

---

### Post by andrew.46 on 2008-05-18
Hi again:

> **satimis said:**
> 

Can I do it on the fly w/o creating ISO image?  Pipe command may help.  But I haven't figured out how to change DVD.


I don't believe that dd or growisofs can operate this way on their own, although I can always be proven wrong :).

    Andrew

---


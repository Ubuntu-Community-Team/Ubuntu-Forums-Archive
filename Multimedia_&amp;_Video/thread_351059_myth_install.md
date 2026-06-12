---
title: "myth install"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by myb on 2007-02-01
here is the background and couple of questions from a newbie;

after doing many (6-7) ubuntu test installs, I've decided to give up xp and go with the ubuntu for real. being new to linux does not scare me at all; trial and error, forums like these help me get by, and i feel good about the accomplishments so far. I will be installing ubuntu desktop, with myth backend-frontend, I have a network storage device also, planned set up will be on a 80 gig HDD, RV6P-NB3/R7000 64MPCI, two monitors, rest of hardware specs are irrelevant for the following questions:

Q1-I did myth installs following some tutorials, they all suggest to partition the hdd doing manual partitioning at the ubuntu install stage, having partition the HDD into three parts. I followed that in some of my test installs, and ignored and had a one big partition in others. My question is why this three partitions? I will be using this box for desktop also and do not want to restrict the space for desktop usage. could I have one big partition? what are cons and pros; drawbacks in the future?

Q2- I will have two monitors; how will I setup specific monitor for myth frontend?

Q3- I would have tossed my xp box if I did not need it for quickbooks! what are my options for converting my data in QB for asoftware that will work on ubuntu- i need something better than kmymoney or sort.

thanks all in advance!

---

### Post by majoridiot on 2007-02-01
A1: although i'm sure this question alone will likely stir lively debate, you can partition your HD
however you choose, as long as the root and partition you intend to store the video on are big
enough.  when i finally settled on a backend config, i formatted for only root, swap and home
partitions, with home being the largest of all... and put my video storage in a video subdirectory.

A2: it depends on your video card and whether or not you use xinerama.  my dualhead myth
setup was on nvidia using twinview without xinerama... i ran the frontend fullscreen and it
defaulted to screen 2.  i currently run it on a three-head setup, fullscreen on #3.

---

### Post by kebes on 2007-02-01
A1: It's easy to do a one-partition install, and it works fine. No problem. Alot of people like putting "/home/" (where personal files and personal settings are stored) on its own partition, that way they can reinstall the OS without erasing personal files. You can even change to a different Linux distribution and most of your settings will be retained. However you have to plan ahead and make the partitions sensible sizes.

For something like MythTV, alot of people like putting the data for the MythTV on a separate partition. This allows you to use a filesystem optimized for myth data (really big files), which makes it run a bit faster. It also allows for restoring the operating system without erasing your recordings.

But, of course, it's up to you. For a first install there's nothing wrong with doing a one-partition install. It will work great.


A2: To do so will require some fiddling with the file "/etc/X11/xorg.conf" which stores your video settings. The primary output on the card will probably be auto-detected just fine. To set-up a second output for TV requires changing xorg.conf so that it knows you are trying to output a TV signal. If you follow a MythTV how-to, most of them explain exactly the changes you need to make.


A3: One thing you could try is running Quickbooks in "Wine", which is a Linux program that can run (some) Windows software. According to the [Wine App Database]("http://appdb.winehq.org/search.php?sSearchQuery=quickbooks"), some versions run and some don't. Wine is a project that improves rapidly, so if you install the latest version you may be able to run that software. It's worth a shot!

Another option would be to use something like QEMU to run a virtual machine that runs Windows XP inside Ubuntu. This is only an option if your computer is fairly fast, but would enable you to run a couple Windows apps when you need to.

In terms of transferring your data to a Linux financial package, I'm not really sure. Here is a list of financial software packages that will run on Linux:
[http://www.gnucash.org/](http://www.gnucash.org/)
[http://kmymoney2.sourceforge.net/index-home.html](http://kmymoney2.sourceforge.net/index-home.html)
[http://jgnash.sourceforge.net/wiki/index.php/Main_Page](http://jgnash.sourceforge.net/wiki/index.php/Main_Page)
[http://moneydance.com/](http://moneydance.com/)
[http://www.grisbi.org/](http://www.grisbi.org/)
[http://www.arachnoid.com/PLCash/index.html](http://www.arachnoid.com/PLCash/index.html)
[http://plugins.jedit.org/plugins/?Lazy8Ledger](http://plugins.jedit.org/plugins/?Lazy8Ledger)

Most of them are free and open-source, so you could try installing them and see if they suit your needs. I've never used any of them so I can't really make a recommendation.


Hope that helps.

---

### Post by myb on 2007-02-01
tyvm both of you!

---


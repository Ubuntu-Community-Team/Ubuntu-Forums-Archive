---
title: "Call for Maverick Meerkat Alpha 3 ISO Testing"
date: 2010-08-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-08-03
Main is once again in ["soft freeze"]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-August/000741.html") in preparation for Alpha 3, which is to be out this Thursday, and the third round of ISO testing in the Maverick cycle is now underway.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. During this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for Alpha 3 are now available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs. 

Note that we now have [upgrade cases]("http://iso.qa.ubuntu.com/qatracker/build/upgrade/all") to be tested, as well as [some new features]("http://ubuntutesting.wordpress.com/2010/08/03/alpha-3-iso-tracker-new-features/") in the tracker.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you're doing testing for the first time, please read the above, and remember that posting issues here is not enough; you should report your test results in the testing tracker.

If you need immediate help with testing, the best place to go is the #ubuntu-testing [IRC channel]("https://help.ubuntu.com/community/InternetRelayChat") on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-08-03
The i386 Desktop iso seems to work great. Live persistence is good, three installs went off without a hitch, and even my upgrade from Lucid worked almost flawlessly (one very minor bug).

---

### Post by bennachie on 2010-08-03
I note the comment in another thread that "stats for Kubuntu ISO testing have been less than stellar". It would be a good idea if a parallel announcement could appear on the Kubuntu forum.

---

### Post by teachop on 2010-08-03
> **kansasnoob said:**
> ...Live persistence is good...

Live persistence == usb boot, right?  How did you set up the usb stick?  I tried Startup disk creator in Lucid and also unetbootin, no luck.  Error message was "unknown keyword in configuration file" when Startup disk creator was used.

---

### Post by kansasnoob on 2010-08-03
> **teachop said:**
> Live persistence == usb boot, right?  How did you set up the usb stick?  I tried Startup disk creator in Lucid and also unetbootin, no luck.  Error message was "unknown keyword in configuration file" when Startup disk creator was used.

That's not what I do. I follow this:

> Live Session Persistence

Case ID: dls-003 
	Create a partition (on a usb stick or regular disk/image) with a label of 'casper-rw' 
	Boot machine with install media 
	Select your language for the install and press Enter 
	Select Try without any change to your computer 
	Press <F6> and add persistent to the boot command line and press enter 
	Wait for the Live session to start 
	Browse webpages in firefox. 
	Restart live image back into a persistent session 
	Browse with firefox again; awesomebar should suggest webpages that you visited in the previous session 
	

Where it says, "Create a partition (on a usb stick or regular disk/image) with a label of 'casper-rw' " I just create a small partition on my iso-testing drive to be sure persistence works.

I have not tried Live USB with Maverick yet and I saw some new updates just today:

[https://launchpad.net/ubuntu/+source/usb-creator/0.2.23/+changelog](https://launchpad.net/ubuntu/+source/usb-creator/0.2.23/+changelog)

I'm glad to see you're interested in testing :D

At times it can be challenging but it's also rewarding. I've learned a lot from folks here in the dev forums.

---

### Post by ranch hand on 2010-08-04
> **bennachie said:**
> I note the comment in another thread that "stats for Kubuntu ISO testing have been less than stellar". It would be a good idea if a parallel announcement could appear on the Kubuntu forum.
This is where we are testing 10.10.

This is where Kubuntu users have no trouble complaining about problems with the install media.

I realize that they are "special" but I really think that they could make a bit of effort on their own behalf.

---

### Post by ranch hand on 2010-08-04
Goodness, the 64 bit Desktop Live Session works really great.  Installed and did a good bit of set up from there.

Installation works great too.  Back on my main 10.10 and doing some apt-get install (chroot) to the new install.

Looking really good.

---

### Post by jerrylamos on 2010-08-05
Alpha 3 up and running on i845G intel video graphics.  Got a couple strange crashes on first boot, commented on in launchpad bug #541492, but is running O.K. with just "quiet" on linux boot line and no xorg.conf.

I haven't tried the i8xx Legacy driver.

Maybe I'll try a Maverick update....hmmm, no updates released yet.

Good go so far, Jerry

---

### Post by 23meg on 2010-08-05
Closing this one, as Alpha 3 is now [out]("http://ubuntuforums.org/showthread.php?t=1546413"). Thanks to everyone who contributed to testing!

---


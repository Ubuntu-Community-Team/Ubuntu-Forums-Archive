---
title: "Alpha 3 ISO testing very soon"
date: 2010-08-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-08-02
I see it on my calender and I will participate if at all possible, but the purpose of this post is to ask if anyone else wants to get involved at this level?

I personally enjoy knowing that I helped eliminate some bugs, and I also feel guilty when I fail to recognize one like this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

But, if you love Ubuntu and want to make it better, iso testing is a good place to show it. They recently introduced an "upgrade" section but we need knowledgeable users to participate.

There will be an official announcement regarding iso-testing tomorrow (I think) :D

---

### Post by 23meg on 2010-08-02
kansasnoob: keep rocking the ISOs. You do [a great job]("https://bugs.launchpad.net/~lbsolost/+reportedbugs?field.searchtext=&orderby=-importance&field.status%3Alist=FIXRELEASED&assignee_option=any&field.assignee=&field.bug_supervisor=&field.bug_commenter=&field.subscriber=&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&search=Search").

Everyone: Now is a good time to rsync your testing images if you haven't already, and don't want to deal with the rush at last minute; it also saves everyone some bandwidth. The dl-ubuntu-test-iso script in the ubuntu-qa-tools package is handy for this.

---

### Post by ranch hand on 2010-08-02
I am waiting with bated breath for the A3 RC ISO.  Want to check the Unity, Desktop and the DVD if it is included in this.

Upgrade, this cycle, is a waste of my time as I can't boot the 10.04 current build CD/DVDs except the ALT install and if I install with it I can only boot through recovery.  Basically I can't run 10.04 with comfort and don't care what happens with it any more.

---

### Post by crjackson on 2010-08-02
> **ranch hand said:**
> I am waiting with bated breath for the A3 RC ISO.  Want to check the Unity, Desktop and the DVD if it is included in this.

Upgrade, this cycle, is a waste of my time as I can't boot the 10.04 current build CD/DVDs except the ALT install and if I install with it I can only boot through recovery.  Basically I can't run 10.04 with comfort and don't care what happens with it any more.

That's a shame ranch hand since it's an LTS.  Lucid has given me a few headaches initially but all the workarounds have solved all my issues (that I can think of right now).  I'll keep Lucid around for a long time on my wife's and kids' machines but I always run the latest on my personal systems.  I can't resist having the latest and greatest on my machines, but my wife and kids hate change and love the dependability currently being experienced with 10.04.

I too have the Plymouth issues and I'm not especially fond of the USC (almost every time I've tried it there are problems).

You know, I've been with Maverick on my laptop since Pre-Alpha 1 and it's really been a smooth ride.  I'm slightly disappointed.

---

### Post by ranch hand on 2010-08-02
I just want to know when the ISOs for testing are going to be up.

I would think that today would have been best.  It takes time to get the buggers and then to burn and test them and install and test the install.

I think this is a good thread to start.  Kubuntu users should take note.  The stats on Kubuntu ISO testing are less than stellar.

---

### Post by kansasnoob on 2010-08-03
I already have a fresh updated Lucid installed on my iso testing drive so I can use it for testing an upgrade before I begin the iso installs.

That's actually kind of cool. I can start by using zsync to upgrade my iso, check the md5sum (even though zsync does it), then burn a new disc, perform a "live" test, and then I can do an upgrade while I'm sippin' some coffee. Following that I can do my three trial installations.

I hope by the time 11.04 is rollin' that I have a network set up so I can spin two boxes at the same time. ATM I'm using a chemical toilet because anything and everything has gone wrong with this remodel :(

---

### Post by ranch hand on 2010-08-03
Sounds to me like you should really enjoy the distraction of running ISO tests.  Keep your concentration on geek stuff and ignore the plumbers et al.

Nothing like looking for geek problems to keep your mind of things like toxic toilets.

---

### Post by 23meg on 2010-08-03
Here we go:

[http://ubuntuforums.org/showthread.php?t=1544977](http://ubuntuforums.org/showthread.php?t=1544977)

---

### Post by xebian on 2010-08-03
> **ranch hand said:**
> ... Kubuntu users should take note.  The stats on Kubuntu ISO testing are less than stellar.

Kubuntu users should get a treat.  The brand new KDE SC 4.5 release. :guitar:

It's A3 but it feels like RC for Kubuntu/KDE

---

### Post by ranch hand on 2010-08-03
Well, this is FUN.

Have only done the Live Session report on UNE (failed).  Only took 3 hours and I did get an install.  Back on an OS I can  see to tweek it a bit.

Installing xorg.edgers before I boot to the bugger so I can see what I am doing hopefully.

Might get to the Desktop version yet.  I sure hope so.

---

### Post by xebian on 2010-08-03
I could never get the UNE to work anymore.  I get to the 'try...' but that's it.  I only see a purple haze zombie. A huge disappointment.  Kubuntu netbook works just fine.

---

### Post by ranch hand on 2010-08-04
> **xebian said:**
> Kubuntu users should get a treat.  The brand new KDE SC 4.5 release. :guitar:

It's A3 but it feels like RC for Kubuntu/KDE
As you are probably aware, I can't stand KDE, just rubs me the wrong way.

I am just tickled, though, to know that there really are Kubuntu users who actually do ISO testing.  I have kept track of the testing and compared it to the complaints about the install media and am not real impressed.

I have tried to figure what the most popular DE is and that is pretty shaky info based on bad polling.  Xfce, however, does not appear to be real popular compared to KDE and Gnome.

They do not whine about how they are treated and boy do they test stuff.

---

### Post by jerrylamos on 2010-08-04
> **ranch hand said:**
> 
I have tried to figure what the most popular DE is and that is pretty shaky info based on bad polling.  Xfce, however, does not appear to be real popular compared to KDE and Gnome.

They do not whine about how they are treated and boy do they test stuff.

I've got 3 test pc's with Lubuntu installed, one with Lucid & the other two with Maverick Alpha 2.  That's LXDE desktop and chromium browser, though you can install firefox or whatever.  Firefox is just larger and slower and more familiar.

As an "ordinary user" Lubuntu does everything I want to do - internet searches & browsing, email, internet video, document writing, ... I don't do games.  I'm more familiar with huge Open Office write than ABI word tho.  I haven't tried Lubuntu's spreadsheet.

Having said all that, I spend most time on Maverick Alpha2 Gnome on four test pc's figuring that bugs would be more applicable to a wider audience.  I've got 3 nasty bugs I've reported and am tracking, and there's a couple other ankle biters that don't stop me.

Jerry

---

### Post by ranch hand on 2010-08-04
I have Lubuntu installed on here too.  Mighty nice little OS.  Hope it is "adopted" fully into the Ubuntu family pretty soon.

I do not like chromium all that well but it is fairly light and fast.

Lubuntu will run on about anything that will boot.  I have a bunch of old boxes I am playing with and it is a nice addition to the tool box.

---

### Post by ranch hand on 2010-08-04
Boy, you guys with the usb keys are a pain.  Had to retest desktop amd64 just for you.  Rebuild sucked.

Selected "continue testing", result not too bad, logged out and back in.

Did my thing and rebooted.

Had selected not to install grub on MBR.  Had no grub on MBR.

Rebooted to Live Session and fixed that.  Have chroot script on all installs, simple copy paste but what a waste of time.

First ISO was fine unless, I guess, you are one of the chosen that have access to the usb key technology.

I really need to go somewhere I can get one.

---

### Post by jerrylamos on 2010-08-04
"First ISO was fine unless, I guess, you are one of the chosen that have access to the usb key technology.  I really need to go somewhere I can get one."

There's Wall Mart for a few, TigerDirect.com to order from the internet for altogether too many choices.

Cheers, Jerry

---

### Post by ranch hand on 2010-08-05
Yup, I know.  I want to see one in my hand (grumpy geezer syndrome).  Don't like WMart and it is a good days adventure to get there and back.

One of these months.

---

### Post by IanW on 2010-08-05
I just downloaded the A3 netbook image for my EeePC, and the menu offers to install either Ubuntu Server or Enterprise Cloud?

I tried to file a bug against this, but Launchpad just times out.

---

### Post by ranch hand on 2010-08-05
I would like to congratulate the Kubuntu testers.  There were actually more tests run on the 4 common ISOs (Alt-32 & 64 and Desktop 32 & 64) than there were for Xubuntu this time.

This is great, maybe we won't be hearing so many complaints about the Kubuntu ISOs this way.

Seeing that there is quite a bit of difference in Kubuntu compared to the other Ubuntu flavors it is important that the folks that want tot use it, and have it work, actually do some testing.

There are some that do it every time but some new names are real nice to see.  More hardware tested on means better results.

---

### Post by phillw on 2010-08-05
After months of my hard-drive complaining, it did the decent thing and said it didn't want to play any longer. At least with Ubuntu things die gracefully, and with a replacement drive in I got my data transferred over.

I'm late to the party this release cycle as I've been concentrating on lubuntu 10.04. But, with the a3 of Lubuntu 10.10 due it's time to start 'playing' :D

Regards,

Phill.
P.S. whoever suggested the use of ppa-purge deserves a medal, what a wonderful item to have in the tool-kit.

---

### Post by 23meg on 2010-08-05
Alpha 3 ISO testing is now over, and the release it [out]("http://ubuntuforums.org/showthread.php?t=1546413"), so I'm closing this one.

---


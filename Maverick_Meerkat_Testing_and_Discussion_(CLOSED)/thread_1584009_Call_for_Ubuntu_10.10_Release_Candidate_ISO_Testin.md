---
title: "Call for Ubuntu 10.10 Release Candidate ISO Testing"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-09-28
With [Final Freeze]("https://wiki.ubuntu.com/FinalFreeze") in effect in preparation for the RC, which is set to be out this Thursday, ISO testing is now underway.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. During this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for the release candidate are starting to appear on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs. 

We now have [upgrade cases]("http://iso.qa.ubuntu.com/qatracker/build/upgrade/all") to be tested, as well as [some new features]("http://ubuntutesting.wordpress.com/2010/08/03/alpha-3-iso-tracker-new-features/") in the tracker.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you're doing testing for the first time, please read the above, and remember that posting issues here is not enough; you should report your test results in the testing tracker.

If you need immediate help with testing, the best place to go is the #ubuntu-testing [IRC channel]("https://help.ubuntu.com/community/InternetRelayChat") on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-09-28
This one's really rough. I'm stuck:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

I've been working on that:

[http://ubuntuforums.org/showthread.php?t=1579475](http://ubuntuforums.org/showthread.php?t=1579475)

And filing a kernel bug failed:

[http://ubuntuforums.org/showthread.php?t=1582584](http://ubuntuforums.org/showthread.php?t=1582584)

I'm feeling like a goat stuck in the mud :(

And I've dealt with a lot of that this year :)

@ mgunes,

Why the name change? (Just as friendly chit-chat).

---

### Post by MacUntu on 2010-09-28
> **kansasnoob said:**
> This one's really rough. I'm stuck:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

I don't think this bug is what's causing your problems. The output of 'xrandr -q' looks fine and you also stated, that

> Oddly the working Maverick that began with the toolchain upload has "turn_on_external_monitors_at_startup" checked in gconf and it's working OK.
:-?

---

### Post by kansasnoob on 2010-09-28
> **MacUntu said:**
> I don't think this bug is what's causing your problems. The output of 'xrandr -q' looks fine and you also stated, that


:-?

Regardless I'm just stuck.

Trying to file a kernel bug fails.

I guess I'm simply not able to figure it out or file a proper bug report so I think I'll sit this dance out :)

I'd guess I've put at least 50 or 60 hours of my leisure time into trying to figure this out and enough is enough. Of course if the devs ask for some info I'll provide it :)

---

### Post by kansasnoob on 2010-09-28
> **MacUntu said:**
> I don't think this bug is what's causing your problems. The output of 'xrandr -q' looks fine and you also stated, that


:-?

Just happened to think, when I posted that at the bug report you'll notice I said:

```
**[COLOR="Red"]Before reboot[/COLOR]** I gathered this info:

lance@lance-desktop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
   1680x1050 60.6*+ 74.9
   1600x1200 75.0 60.0
   1400x1050 74.9 60.0
   1280x1024 75.0 60.0
   1280x960 60.0
   1152x864 75.0
   1024x768 75.1 70.1 60.0
   832x624 74.6
   800x600 72.2 75.0 60.3 56.2
   640x480 72.8 75.0 66.7 60.0
   720x400 70.1
```

There is no way to get an xrandr output after the failure since X can't be initialized.

---


---
title: "My little xsplash experiment"
date: 2010-05-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-05-30
I am trying to get a version of 10.04 that runs with xsplash and its associated libs and so forth.

I do not know what I am doing unfortunately.

The plan is to have 3 OSs.  9.10, 9.01>10.04 upgrade, and 9.10>10.04 upgrade leaving xsplash et al in.

I had this under way on my single drive external enclosure but the HDD has died.

So I shifted to my sdb internal.  I had 9.10 on there with some others.  I installed 9.10 where I had 2 of the others.

I installed all my standard stuff on the 2 new ones and upgraded them to current.  I also installed bootchart on all three and will try to put the 10.04 version on the 9.10 install if things go.

The one that is to be straight up 10.04 is just finishing up right now (chroot apt type dist-upgrade).

I have the upgrade and dist-upgrade lists.

I am going to change the the sources list on the other and just do the upgrade (tomorrow) and then see if it boots.

Then I plan on trying to do the dist-upgrade selectively.

Does anyone have a clue as to if I can do this in synaptic by freezing xsplash and it dependencies?

If this step works I intend to copy the bugger to my test platform and try to step it up to 10.10.

---

### Post by Slug71 on 2010-05-30
> **ranch hand said:**
> I am trying to get a version of 10.04 that runs with xsplash and its associated libs and so forth.

I do not know what I am doing unfortunately.

The plan is to have 3 OSs.  9.10, 9.01>10.04 upgrade, and 9.10>10.04 upgrade leaving xsplash et al in.

I had this under way on my single drive external enclosure but the HDD has died.

So I shifted to my sdb internal.  I had 9.10 on there with some others.  I installed 9.10 where I had 2 of the others.

I installed all my standard stuff on the 2 new ones and upgraded them to current.  I also installed bootchart on all three and will try to put the 10.04 version on the 9.10 install if things go.

The one that is to be straight up 10.04 is just finishing up right now (chroot apt type dist-upgrade).

I have the upgrade and dist-upgrade lists.

I am going to change the the sources list on the other and just do the upgrade (tomorrow) and then see if it boots.

Then I plan on trying to do the dist-upgrade selectively.

Does anyone have a clue as to if I can do this in synaptic by freezing xsplash and it dependencies?

If this step works I intend to copy the bugger to my test platform and try to step it up to 10.10.

You might be able to uncheck the Plymouth updates in Update Manager when you make the dist upgrade. Maybe even in Synaptic too.

---

### Post by ronacc on 2010-05-30
I don't know if that will work , I think you would have to hack some debs to alter the depends .

---

### Post by ranch hand on 2010-05-30
> **ronacc said:**
> I don't know if that will work , I think you would have to hack some debs to alter the depends .
I am getting to that idea too.

Haven't got the savvy for that.   I do have the mountall deb for the one that doesn't depend on plymouth but do not think that extends to libplymouth2 and that is the real base of the problem.

---

### Post by ranch hand on 2010-05-30
> **Slug71 said:**
> You might be able to uncheck the Plymouth updates in Update Manager when you make the dist upgrade. Maybe even in Synaptic too.
That is kind of my idea to try although I haven't used Update Mangler since Hardy.

What I am actually doing is mainly in chroot using apt but the principle is the same.

I take the list it gives and paste it to gedit and then go through and try to just do the ones that I think are safe.

I thought that all of them on the apt-get upgrade list were OK but can't boot through the normal entry.  I haven't tried recovery yet.  That is next.

If that doesn't work I may reinstall 9.10 and try it again after removing the desktop meta package.

Kind of beats me but I know that in 10.04 testing I was actually getting better boot times with xsplash right before it was changed to plymouth than I ever got after that.  I do not have a clue as to if that would hold true later in testing or with the final release of 10.04.

The 10.10 stuff may not even be compatible at all.  There seems to be a lot of seemingly (to me anyway) unrelated stuff that depends on plymouth.  There were really few with xsplash and usplash.

That is one of the things that really worries me for the future with plymouth.  The more stuff that depends on something that really doesn't run very long seems kind of dangerous to me.  It seems safe to assume that folks that have problems may just be SOL as with Fedora (I can't even boot their CDs at all as the menu screen freezes when it comes up)..

Oh well I will whack at it some more just to see.

Thanks for the suggestion.  If I reinstall I will definately be doing more in the OS and probably a good bit with synaptic.

---

### Post by ronacc on 2010-05-30
I think if I was going to try I would extract the current deb using archive manager and then edit out plymouth and libplymouth2 from the control file and the rebuild the deb , ofcourse be ready for complete destruction of your install . Theres a tool in synaptic somewhere for createing debs .

 PS I have no Idea if that will work I am as lacking in savy about this as you are .

---

### Post by ranch hand on 2010-05-30
> **ronacc said:**
> I think if I was going to try I would extract the current deb using archive manager and then edit out plymouth and libplymouth2 from the control file and the rebuild the deb , ofcourse be ready for complete destruction of your install . Theres a tool in synaptic somewhere for createing debs .

 PS I have no Idea if that will work I am as lacking in savy about this as you are .
If I was real worried about ruining an install I don't think that I would enjoy testing very much.

I have gotten pretty good at rescuing the buggers with out reinstalling so maybe I am just doing this to have that opportunity more often.  Maybe I need "professional help" with my mental health.

Nah, that wouldn't be any FUN.  This is, even it it is time consuming.

---

### Post by ronacc on 2010-05-30
Heck theres 3things I n,ever claimed to be rich ,beautiful or sane :lolflag:

---

### Post by mc4man on 2010-05-30
If you wish to run without libplymouth2 then you'll need to use a mountall that doesn't use it (key word use

That would mean 1.0 or 1.1 tops, after that no libplymouth, no boot

---

### Post by ranch hand on 2010-05-30
> **mc4man said:**
> If you wish to run without libplymouth2 then you'll need to use a mountall that doesn't use it (key word use

That would mean 1.0 or 1.1 tops, after that no libplymouth, no boot
So I, somehow, have got to use the mountall from 9.10.  I think this is going to prove impossible for me to do.

There is, however, only one way to find out.

I'll give it a whack.

---

### Post by Slug71 on 2010-05-31
> **ranch hand said:**
> So I, somehow, have got to use the mountall from 9.10.  I think this is going to prove impossible for me to do.

There is, however, only one way to find out.

I'll give it a whack.

Add Karmic's repo and pull it in from there.

---

### Post by Slug71 on 2010-05-31
When we had that, i believe gconf2(irc) problem being discussed a week or so ago i installed the xfce desktop. Then i wanted to add some of the Mint stuff and since Mint xfce was a release behind, it tried to drag in Xsplash and Usplash. I was able to go and uncheck it in Synaptic. I know thats kinda the opposite of what you want but it somewhat worked. I some some flickering issues after boot like the like the loading dots from the Plymouth screen would stay flickering(loading) on my desktop. But im not sure that was related.

---

### Post by ranch hand on 2010-05-31
> **Slug71 said:**
> Add Karmic's repo and pull it in from there.
I am starting with 9.10 so that is not a problem.  I just came from there and I locked all the Xsplash depends and mountall.

I am going to have to check to see what that screws up and see what else I need to do.  I just remembered the desktop meta package, for instance, that will have to be removed.

---

### Post by ranch hand on 2010-06-01
Well, that was interesting.  So interesting that I may just have to try it again.

I used synaptic after locking some things involved with mountall and mountall, usplash and xsplash.

It did not install every upgrade, a bunch held back, but it did upgrade the kernel and looked fairly good until it removed the entire gui.

This didn't seem too bad to me until I tried to install one.  I could not get it to go at all.

I think I will, when I get time, reinstall 9.10 and try this one more time with some slight changes.  I do have serious doubts that this is something that will work and I was going to quit after this attempt but maybe I better try it again.

There is probably a way to do this if you have more knowledge than I have now but plymouth appears to be embedded a lot deeper than xsplash.

---

### Post by Slug71 on 2010-06-01
> **ranch hand said:**
> Well, that was interesting.  So interesting that I may just have to try it again.

I used synaptic after locking some things involved with mountall and mountall, usplash and xsplash.

It did not install every upgrade, a bunch held back, but it did upgrade the kernel and looked fairly good until it removed the entire gui.

This didn't seem too bad to me until I tried to install one.  I could not get it to go at all.

I think I will, when I get time, reinstall 9.10 and try this one more time with some slight changes.  I do have serious doubts that this is something that will work and I was going to quit after this attempt but maybe I better try it again.

There is probably a way to do this if you have more knowledge than I have now but plymouth appears to be embedded a lot deeper than xsplash.

Probably to do with Ubuntu's dependency hell.

Geez, i just marked Xsplash and Usplash for installation on 10.04 in Synaptic and when i marked Usplash, pretty much my whole system gets marked for Removal. Craziness!

Maybe try updating the packages individually in Synaptic?

---

### Post by ranch hand on 2010-06-01
> **Slug71 said:**
> Probably to do with Ubuntu's dependency hell.

Geez, i just marked Xsplash and Usplash for installation on 10.04 in Synaptic and when i marked Usplash, pretty much my whole system gets marked for Removal. Craziness!

Maybe try updating the packages individually in Synaptic?
This seems to be the case.

I am thinking about a number of options and going through synaptic a few at a time seems the place to start.

I would really like to have something to replace 8.04 with but 10.04 is just too scary for what we use the LTS for.  That being the case I had better try this again.

One nice thing was that it gave me a pair of partitions to install the A1 ISO test on (went very well).

---

### Post by Longinus00 on 2010-06-01
If you dislike all the extra "shiny bits" that ubuntu adds, it would much easier to simply install debian.

---

### Post by ranch hand on 2010-06-01
> **Longinus00 said:**
> If you dislike all the extra "shiny bits" that ubuntu adds, it would much easier to simply install debian.
This is always an option and  I may well be headed that way.  I had Lenny on here for a while but it didn't get enough use.  If a new version of PhatDebian on ext4 comes out I will definitely be going with it for my "secure" system.  Sid is a real consideration too.

I prefer Ubuntu.

On the other hand what I really like is an OS that boots and shuts down.

---

### Post by dino99 on 2010-06-01
have you added "debug" on boot line to trace this problem ?

---

### Post by Longinus00 on 2010-06-01
> **ranch hand said:**
> This is always an option and  I may well be headed that way.  I had Lenny on here for a while but it didn't get enough use.  If a new version of PhatDebian on ext4 comes out I will definitely be going with it for my "secure" system.  Sid is a real consideration too.

I prefer Ubuntu.

On the other hand what I really like is an OS that boots and shuts down.

What in the world is phatdebian?

---

### Post by ranch hand on 2010-06-01
[http://phatdebian.com/](http://phatdebian.com/)

The beta had no problems so it was just used as is.  I do not like the default artwork but there is lots more and quite a bit on the forum from users.

Uses the 2.6.30 kernel (I think, might be 31) so while it is on ext3 it supports ext4 very nicely for sharing data and so forth.

---

### Post by Longinus00 on 2010-06-01
> **ranch hand said:**
> [http://phatdebian.com/](http://phatdebian.com/)

The beta had no problems so it was just used as is.  I do not like the default artwork but there is lots more and quite a bit on the forum from users.

Uses the 2.6.30 kernel (I think, might be 31) so while it is on ext3 it supports ext4 very nicely for sharing data and so forth.

That webpage is very uninformative in regards as to what makes phatdebian different from debian besides a few custom backgrounds and a different kernel.

If you feel that lenny is too conservative you can always use squeeze (testing), that's where 10.04 got its packages from. Some people also pull in specific packages from sid (unstable) that they want updated versions of rather than using sid packages for their whole system.

---

### Post by ranch hand on 2010-06-01
> **Longinus00 said:**
> That webpage is very uninformative in regards as to what makes phatdebian different from debian besides a few custom backgrounds and a different kernel.

If you feel that lenny is too conservative you can always use squeeze (testing), that's where 10.04 got its packages from. Some people also pull in specific packages from sid (unstable) that they want updated versions of rather than using sid packages for their whole system.
PhD is pretty nice and that sums it up pretty well.

I have never used squeeze.  Lenny, sid and sidiux.  I didn't think much of sidux.

Squeeze I really should have a look at.

---

### Post by Mr. Picklesworth on 2010-06-01
> **Slug71 said:**
> Probably to do with Ubuntu's dependency hell.

Geez, i just marked Xsplash and Usplash for installation on 10.04 in Synaptic and when i marked Usplash, pretty much my whole system gets marked for Removal. Craziness!

Maybe try updating the packages individually in Synaptic?

So is Plymouth not working for you guys, or is this some kind of political thing?

The reason why installing USplash causes everything else to go is pretty simple, really. Every package on your system ultimately depends on upstart, which is what initializes everything; and mountall, which Upstart uses to mount filesystems during boot. For a fairly good reason (related to reliability), the mountall package presently has a hard dependency on Plymouth.

Therefore, replacing Plymouth will break everything, so all those broken packages are removed.

Note that “break” here means “no longer functioning as expected,” which in the context of *starting up your system* can be a pretty big deal. Debian likes everything to be precise :)

---

### Post by Slug71 on 2010-06-01
> **Mr. Picklesworth said:**
> So is Plymouth not working for you guys, or is this some kind of political thing?

The reason why installing USplash causes everything else to go is pretty simple, really. Every package on your system ultimately depends on upstart, which is what initializes everything; and mountall, which Upstart uses to mount filesystems during boot. For a fairly good reason (related to reliability), the mountall package presently has a hard dependency on Plymouth.

Therefore, replacing Plymouth will (as far as apt is concerned) break everything, so all those broken packages are removed.

Plymouth works fine for me. On 2 boxes so far and have 2 more to try it on.

---

### Post by ranch hand on 2010-06-01
> **Mr. Picklesworth said:**
> So is Plymouth not working for you guys, or is this some kind of political thing?

The reason why installing USplash causes everything else to go is pretty simple, really. Every package on your system ultimately depends on upstart, which is what initializes everything; and mountall, which Upstart uses to mount filesystems during boot. For a fairly good reason (related to reliability), the mountall package presently has a hard dependency on Plymouth.

Therefore, replacing Plymouth will (as far as apt is concerned) break everything, so all those broken packages are removed.
Well I guess as far as anything but a testing install then it is off to Debian.

It is too bad that plymouth is that deeply embedded because it pretty much breaks everything too.

It is a dirty shame that the new LTS was saddled with this extremely crappy boot manager.  Was really looking forward to replacing my "secure" OS, Hardy, with this but there is no way.

It is a great release.  Well, it would be if you could depend on it to boot and to shut down.

All because we have to have plymouth because it is so wonderful.  Yep, sure is, if you are one of the lucky folks that it will work for.

Works great for my son by the way.  He boot in about 15 seconds and it shuts down fast.  I wish it did for me.  9.04 boots fast compared to this and I do not need to use Alt+Sysreq+b to shut it down.

This is a real bummer.

---

### Post by Slug71 on 2010-06-01
> **ranch hand said:**
> Well I guess as far as anything but a testing install then it is off to Debian.

It is too bad that plymouth is that deeply embedded because it pretty much breaks everything too.

It is a dirty shame that the new LTS was saddled with this extremely crappy boot manager.  Was really looking forward to replacing my "secure" OS, Hardy, with this but there is no way.

It is a great release.  Well, it would be if you could depend on it to boot and to shut down.

All because we have to have plymouth because it is so wonderful.  Yep, sure is, if you are one of the lucky folks that it will work for.

Works great for my son by the way.  He boot in about 15 seconds and it shuts down fast.  I wish it did for me.  9.04 boots fast compared to this and I do not need to use Alt+Sysreq+b to shut it down.

This is a real bummer.

What graphics card is your Stable system using? Is the one in your sig?
Our laptop(Acer) with ATI Radeon Express 1250 plays fine with Plymouth. I did a 9.10->10.04 upgrade with it.

And ive done both the upgrade as mentioned above as well as a clean install on my desktop(GF6600) using the the nouveau driver.

When i get our Netbook(Acer) back from our sister in law im gonna do the upgrade to that too and will post the results.

---

### Post by ranch hand on 2010-06-01
All my installs are on the one box (4 working HDDs).

The stable releases are on sda anb sdb (internal).

Testing is on a dual HDD external enclosure and when running it the internals, at least sda, are turned off in bios due to paranoia.

I am not buying new hardware to run an OS that should run fine on what I have.  If you look at the ABT on General Help forums you will see that I am not alone.

I love Ubuntu and am, right now pretty depressed.  I just am totally bummed that I am going to have to find a different distro to actually use.

This just really sucks.  I do not get depressed much but right now I really feel like it really sucks to be me.

---

### Post by Slug71 on 2010-06-01
> **ranch hand said:**
> All my installs are on the one box (4 working HDDs).

The stable releases are on sda anb sdb (internal).

Testing is on a dual HDD external enclosure and when running it the internals, at least sda, are turned off in bios due to paranoia.

I am not buying new hardware to run an OS that should run fine on what I have.  If you look at the ABT on General Help forums you will see that I am not alone.

I love Ubuntu and am, right now pretty depressed.  I just am totally bummed that I am going to have to find a different distro to actually use.

This just really sucks.  I do not get depressed much but right now I really feel like it really sucks to be me.

Do you get the same issues on your internal drives?

---

### Post by ranch hand on 2010-06-01
> **Slug71 said:**
> Do you get the same issues on your internal drives?
Yes.  In spite of the fact that my external is USB I can't really tell the difference in performance, seems the same on any install.

---

### Post by cariboo on 2010-06-01
Closed by request.

---


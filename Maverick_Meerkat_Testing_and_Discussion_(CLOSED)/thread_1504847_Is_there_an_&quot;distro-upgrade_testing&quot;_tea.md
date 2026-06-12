---
title: "Is there an &quot;distro-upgrade testing&quot; team?"
date: 2010-06-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-06-08
I'm just wondering if there is a separate upgrade and/or update testing team. I've been doing iso-testing fairly reliably for some time and I believe I have helped with squashing a few bugs or at least getting them documented in the release notes.

I do know you can test "proposed" updates and if you follow the changelogs you can easily report to the proper bug report if you suffered any success or failure/regression.

But this bug is driving me nuts:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Of course I reported it, and I identified it as a duplicate of at least two others. I even got bold and subscribed Colin Watson!

I got bolder and posted this on Ayatana:

> In order to cut to the chase look here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

There are many internal links there to explore!

The problem is simple! At some point towards the end of the Lucid development cycle we changed from offering just "drive MBR's" for grub install points to "ALL DEVICES", yet we said:

"The grub-pc package is being upgraded. This menu allows you to select which devices .....................................", and  then:

"If  .............. unsure .............. install to all of them". Some fairly good screenshots linked to here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/15](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/15)

This behavior has been catastrophic for noobs and anyone not paying close attention!

I was bold enough to subscribe Colin Watson here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/17](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/17)

I would not "step outside of the ilnes" if I didn't feel I'd otherwise exhausted all other options. But, IMHO, this is a distro killer!

If there ever was a bug that deserved a lot of attention this is it!


This is absolutely killing people that upgrade from Karmic or Hardy to Lucid! It even effects Wubi users!

Now a Mod might say this isn't Maverick related but it certainly is! What we've done wrong in the past helps us improve in the future.

---

### Post by kansasnoob on 2010-06-09
I guess there's not:

[https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

Should there be?

---

### Post by kansasnoob on 2010-06-10
So, should we form a distro-upgrade team?

Anyone else willing?

---

### Post by cariboo on 2010-06-10
I don't think there is really a need for one, if done correctly upgrades work very well. From what I've seen a good many failed upgrades are because of user problems. We could probably use a a good set of instructions on how to do an upgrade, although very few people would read them until their upgrade failed.

I'm in the process of upgrading from a fresh install of Jaunty to Lucid, the first thing I found is that if you aren't fully up-to-date, you will be offered a partial upgrade, How many posts have we seen where that has happened?

More once the upgrade finishes.

---

### Post by ranch hand on 2010-06-10
There actually was a period of testing for the upgrade of 8.04 to 10.04 and that was pretty understandable and they did a great job tweeking 8.04.4 for that upgrade.

If you think about it we are really testing the up grade now.  I am not sure what else really needs tested for the upgrades, except in the case of LTS>LTS.

---

### Post by kansasnoob on 2010-06-11
> **cariboo907 said:**
> I don't think there is really a need for one, if done correctly upgrades work very well. From what I've seen a good many failed upgrades are because of user problems. We could probably use a a good set of instructions on how to do an upgrade, although very few people would read them until their upgrade failed.

I'm in the process of upgrading from a fresh install of Jaunty to Lucid, the first thing I found is that if you aren't fully up-to-date, you will be offered a partial upgrade, How many posts have we seen where that has happened?

More once the upgrade finishes.

If that were all true we wouldn't have this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

It has nothing to do with a partial upgrade!

I'd like to know the history of iso-testing.

My time will be limited for a few months which is why I'm tossing this out for thought and discussion within the community.

---

### Post by kansasnoob on 2010-06-11
> **ranch hand said:**
> There actually was a period of testing for the upgrade of 8.04 to 10.04 and that was pretty understandable and they did a great job tweeking 8.04.4 for that upgrade.

If you think about it we are really testing the up grade now.  I am not sure what else really needs tested for the upgrades, except in the case of LTS>LTS.

I remember you mentioning that and I also tested ATM.

I had almost nothing to do with it but that testing resulted in this release note:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

My point is that if we had distro-upgrade testing set up similar to iso-testing we'd eliminate more bugs before release.

I'm silly tired right now but I hope that makes sense.

---

### Post by ranch hand on 2010-06-11
Those are good points.  I will have to think about it a bit more.

---

### Post by cariboo on 2010-06-11
> **kansasnoob said:**
> If that were all true we wouldn't have this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

It has nothing to do with a partial upgrade!

I'd like to know the history of iso-testing.

My time will be limited for a few months which is why I'm tossing this out for thought and discussion within the community.

That problem hasn't shown up on any of the upgrades I've done so far, mind you, I haven't upgraded from Hardy to Lucid yet, that'll be my next project after the current one is done. I'm using really ancient and barely usable hardware for this so it's taking a while, at the start of the Lucid upgrade it said it was going to take 16 hours, after 45min it was down to 7 hours.

We can't hold everyone's had during the upgrade process, but from what I've seen, the system in place now comes pretty close.

---

### Post by kansasnoob on 2010-06-12
> **cariboo907 said:**
> That problem hasn't shown up on any of the upgrades I've done so far, mind you, I haven't upgraded from Hardy to Lucid yet, that'll be my next project after the current one is done. I'm using really ancient and barely usable hardware for this so it's taking a while, at the start of the Lucid upgrade it said it was going to take 16 hours, after 45min it was down to 7 hours.

We can't hold everyone's had during the upgrade process, but from what I've seen, the system in place now comes pretty close.

I actually failed to see it when I tested upgrades from Karmic to Lucid, in fact I reported these ten days prior to release:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/567015](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/567015)

[https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/567010](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/567010)

And as I said in the first one:

> You should be aware I'm only doing this as a test because **I've seen some reports on the forums of grub2 installing to all mbrs and partitions** during an upgrade so I wanted to check it out myself. **[COLOR="Red"]That was not the case for me.[/COLOR]**

That's why in the bug report that's caused me to think an "upgrade-team" could be useful I said in comment #7:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

> I'm part of the problem because **I blew it off for weeks blaming it on "the bug between the chair and the keyboard"** so you can blame me for not more aggressively pursuing this throughout iso-testing and upgrade testing. ...............
It could have been sooner if I'd done a better job of testing and **remembering to put my "noob" shoes on** ;^(

The problem is quite simple. This is what the update presents you with:

[ATTACH]160187[/ATTACH]

As you can see all drive **and partition** designations are presented, and the text says, "If you're unsure which drive is designated as boot drive .............. **[COLOR="Red"]it is often a good idea to install grub to all of them[/COLOR]**".

Quite simply **[COLOR="Red"]most noobs don't know the difference between a drive designation and a partition designation[/COLOR]**. I've found this to be the case even with some users that have been around for months or even years.

In Karmic we displayed only drive designations which was much safer and saner IMHO. It's also still that way in Squeeze. Then in the rare case when someone wants to install grub 2 to a partition they have to use the terminal post-installation but I think that's reasonable since it's almost never wise to install grub 2 to a partition.

As it is I've seen literally hundreds of Windows users install grub 2 to their Win partition and totally hose things. About 90% to 95% have been able to recover either by using Testdisk, their Win recovery/installation disc, or Meierfra even has an old link up with tar.gz's of the Windows files. Sadly the other 5% mess things up even further and end up having to recover data and reinstall Windows :(

This is why I think an actual "upgrade-testing" team would be useful. I blew it, but if we announced upgrade testing in a similar manner as iso-testing I think what one person overlooks another might see. I do realize it's much more time consuming. I have fast internet (I can download a CD iso in about 17 minutes) but it still takes about 90 minutes to perform most upgrades.

Of course I could just do a sort of "informal" testing notification here and see if anyone else cares to jump in, but I think what makes iso-testing so successful is that when a bug gets the iso-testing "tag" it gets developer attention very quickly, whereas just silly old me reporting a bug may take weeks or months to get some attention.

---

### Post by cariboo on 2010-06-12
kansasnoob, we are not average users, most of the people I run into, don't have more than two hard drives in their computer, and I very rarely see computers with more than one operating system installed during my daily travels. The odd person has an external hard drive. supposedly used for backups, but even with the ease of setting backups up, virtually no one does it on a regular basis. In your case with 9 partitions on one drive, and 3 on the other, that could lead to problems if you install grub on each partition.

The problem is that most new users can't differentiate between a hard drive or a partition no matter what operating system they are using. How do you educate the user before they try to install Ubuntu. 

As you say the majority of users that have problems can solve the problem with help from the forums, and the other few that can't, are going to have problems until they have the system set for them, whether by directions here or from a friend.

The one thing that many of us forget, is that it is estimated that there are about 12,000,000 Ubuntu users, if the partitioning problem was as big a problem as you say, the forums would have been overloaded when Lucid was released.

I don't want to belittle the problem, and it does need to be fixed, but isn't that what iso tesing is for?

---

### Post by kansasnoob on 2010-06-12
> **cariboo907 said:**
> kansasnoob, we are not average users, most of the people I run into, don't have more than two hard drives in their computer, and I very rarely see computers with more than one operating system installed during my daily travels. The odd person has an external hard drive. supposedly used for backups, but even with the ease of setting backups up, virtually no one does it on a regular basis. In your case with 9 partitions on one drive, and 3 on the other, that could lead to problems if you install grub on each partition.

The problem is that most new users can't differentiate between a hard drive or a partition no matter what operating system they are using. How do you educate the user before they try to install Ubuntu. 

As you say the majority of users that have problems can solve the problem with help from the forums, and the other few that can't, are going to have problems until they have the system set for them, whether by directions here or from a friend.

The one thing that many of us forget, is that it is estimated that there are about 12,000,000 Ubuntu users, if the partitioning problem was as big a problem as you say, the forums would have been overloaded when Lucid was released.

I don't want to belittle the problem, and it does need to be fixed, but isn't that what iso tesing is for?

Clearly we live in different worlds. At least 80% of the people I've converted to Ubuntu want to dual boot. Quite simply they want to hang on to what they know works (even if it works poorly) until they're sure something new works.

Furthermore when you say:

> In your case with 9 partitions on one drive, and 3 on the other, that could lead to problems if you install grub on each partition.

You're totally missing the point!

That was a shot of MY machine at one point in time with the intention of showing the problem.

Most of the problems seen reported on the forums have been from folks booting only one Windows and one Ubuntu, thus the reason they know little to nothing about Linux, partitioning, etc. 

They installed Ubuntu previously and it worked well enough to keep a dual-boot. The upgrade to Lucid hosed their Windows OS and they're PO'ed. In some cases they lost data!

But, honestly, we really "disconnect" when you say:

> but isn't that what iso tesing is for?

NO! An upgrade/update has nothing to do with the iso! An iso is an image that's used to "install" an OS!

Upgrades and updates are a totally different animal. Clean install vs. upgrade :confused:

Totally unrelated other than the intended outcome.

---

### Post by ranch hand on 2010-06-12
> **kansasnoob said:**
> Clearly we live in different worlds. At least 80% of the people I've converted to Ubuntu want to dual boot. Quite simply they want to hang on to what they know works (even if it works poorly) until they're sure something new works.

Furthermore when you say:



You're totally missing the point!

That was a shot of MY machine at one point in time with the intention of showing the problem.

Most of the problems seen reported on the forums have been from folks booting only one Windows and one Ubuntu, thus the reason they know little to nothing about Linux, partitioning, etc. 

They installed Ubuntu previously and it worked well enough to keep a dual-boot. The upgrade to Lucid hosed their Windows OS and they're PO'ed. In some cases they lost data!

But, honestly, we really "disconnect" when you say:



NO! An upgrade/update has nothing to do with the iso! An iso is an image that's used to "install" an OS!

Upgrades and updates are a totally different animal. Clean install vs. upgrade :confused:

Totally unrelated other than the intended outcome.

I have to agree with where the problem is here.  I have "helped" on at number of these cases of MS/Ubuntu.  As I know little of the MS system sometimes this has been a struggle (oldfred has taught me more about MS than I ever wanted to know).

This problem is very common in both ABT and General help, much too common.  I have been good and not suggested just deleting the MS stuff from their HDD (this is called restraint).

Instructing folks to basically blow their MS install out of the water, while appealing to me, is not a real good thing to be doing.  The poor buggers want it on there and in many, if not most, cases it is their primary OS.  They are not happy about this.

---

### Post by plun on 2010-06-13
> **cariboo907 said:**
> 

I don't want to belittle the problem, and it does need to be fixed, but isn't that what iso tesing is for?

This challenge is a big one... we have several users within the Swedish LoCo with broken Grub and Windows.  For everyone which are hit by this bug more users stays away from Ubuntu.:cry:  also opens for Ubuntu-FUD.

It seems also affect some new installs with broken Windows....

So this is bad, bad and must be resolved as soon as possible !

I also noticed that "slangasek" now classifies this bug with "High" and Triaged.

> ** Also affects: grub2 (Ubuntu Maverick)
   Importance: High
       Status: Triaged



---

### Post by taavikko on 2010-06-13
> **plun said:**
> This challenge is a big one... we have several users within the Swedish LoCo with broken Grub and Windows.

Same in Finnish-LoCo.

Usual upgrade errors are also:
window managers b0rked /* cleaning up home usually suffices */
graphics b0rked

So this upgrade-testing should receive some love.

---

### Post by kansasnoob on 2010-06-14
OK, some help :)

Ronald McCollam replied at Ayatana and we're moving this request/idea to "ubuntu-qa@lists.ubuntu.com", so I need to make time to craft a decent proposal there.

That's why it's helpful to thrash through some of this here at the forums first. Cariboo907's friendly disagreement makes me see what needs to be clarified in my request.

Until I get my mind around this a bit better you can have a look here:

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-qa](https://lists.ubuntu.com/mailman/listinfo/ubuntu-qa)

June archives here:

[https://lists.ubuntu.com/archives/ubuntu-qa/2010-June/subject.html](https://lists.ubuntu.com/archives/ubuntu-qa/2010-June/subject.html)

The testcases home page:

[http://testcases.qa.ubuntu.com/](http://testcases.qa.ubuntu.com/)

---

### Post by 23meg on 2010-06-14
There isn't currently such a team, but by joining the general [testing team]("https://launchpad.net/~ubuntu-testing"), you're signing up as a volunteer to receive calls for upgrade testing when the development branch is ready for such testing.

Upgrade testing is particularly suited for test automation, which is why [automated testing]("https://wiki.ubuntu.com/AutoDistUpgradeTestingSpec") of all upgrade paths is performed as well, the output of which you'll find [here]("http://people.canonical.com/~mvo/automatic-upgrade-testing").

---

### Post by darkod on 2010-06-14
Sorry if this is inappropriate, but just one recent example:

> Has ANYONE done ANY testing on the Ubuntu 10.04 update being offered to  users?
 
I just finished getting my system bootable because the upgrade trashed  my PC. Fortunately I dual boot Windows 7 and Ubuntu so I was able to get  my machine running with the Windows 7 disc.
 
#1. WHY can't the update prompt me for the needed details BEFORE  starting? It runs for 15 minutes, then stops - waiting for some input.  Then it runs a while longer and stops, etc. ad infinatum. 
 
#2. GRUB2 - Why can't this stupid piece of crap determine where it  should be upgrading. WHY does it tell you to install on ALL the drives  in a system? I'm doing an UPGRADE, so just UPGRADE what's already there.  DON'T install new copies on other drives and at least tell me if there  are multiple locations available for updates.
 
...anyhow. I don't have time to try and recover what the upgrade tried  to do. Any work that I had committed to running under Linux is not going  to eat my time.

---

### Post by wilee-nilee on 2010-06-14
Not only do the distro upgrades show the install to all partitions gui, but the grub2 upgrade from 1,97-1.98 also showed that gui.

It is a faulty design to suggest installing in every partition, without some help popup that is simple enough for even the uninitiated can understand. It would be as simple as if you haven't installed in a partition don't do it now and a short description of the difference between sda sda1-which is the mbr and which is a partition.

It never caught me but I know where grub goes.

---

### Post by kansasnoob on 2010-06-16
> **23meg said:**
> There isn't currently such a team, but by joining the general [testing team]("https://launchpad.net/~ubuntu-testing"), you're signing up as a volunteer to receive calls for upgrade testing when the development branch is ready for such testing.

Upgrade testing is particularly suited for test automation, which is why [automated testing]("https://wiki.ubuntu.com/AutoDistUpgradeTestingSpec") of all upgrade paths is performed as well, the output of which you'll find [here]("http://people.canonical.com/~mvo/automatic-upgrade-testing").

Thanks for that info. I did now subscribe to the Testing Team.

I see my message did get posted:

[https://lists.ubuntu.com/archives/ubuntu-qa/2010-June/001072.html](https://lists.ubuntu.com/archives/ubuntu-qa/2010-June/001072.html)

Somehow the formatting was awful, I'm not the brightest bulb on the tree, but hopefully I got the point across.

To summarize:

#1: Regarding that specific bug, I blew it! More testers might have caught it. Even if I had caught it would it have been addressed with the same urgency without the QA "stamp of approval".

#2: IMHO the iso-testing format is super great! I think you've all got that down to almost a true science! I think we manage to get a lot of bugs addressed using that format.

#3: Without a formal "QA stamp" bugs tend to fall into oblivion and that does make sense because some bugs are limited to very few scenarios, specific hardware, etc. IMHO QA has shown it's very capable of determining what's critical and what's not.

So, I guess, in the long run I'm saying that QA does such a good job they need a heavier work load ;)

Sadly I can't give you all a pay raise.

---

### Post by plun on 2010-07-21
Thank you Kansasnoob that you didn't give up with the Grub 2 mess.

Just a disaster with dual boot users with a complete mess, I hope that the fix also fixes new installs....

Lucid 10.04.1 is delayed but your bug is there... Thanks again !:D

---


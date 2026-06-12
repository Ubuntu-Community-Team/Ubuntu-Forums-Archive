---
title: "Change in grub 2 package upgrade behavior"
date: 2010-06-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-06-23
I noticed following package upgrades of "grub-common" and "grub-pc" on both the 21st and today (the 23rd) that grub 2 automatically "installs" to the mbr of the drive. I thought so on the 21st because when I rebooted much later I was no longer getting my "custom menu" that I use in Karmic.

I multi-boot, currently Maverick on sda1 and:

Found Linux Mint 9 Isadora (9) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.04 LTS (10.04) on /dev/sda12
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04 LTS (10.04) on /dev/sda3
Found Ubuntu 10.04 LTS (10.04) on /dev/sdb2

So I already had a grub 2 mbr, although it was assigned to /dev/sda2 (Karmic), but following the updates sda1 had the mbr. Now, this is no big deal to me because I only need to boot into Karmic again and run "grub-install /dev/sda", but I wonder what kind of a storm this might create with Windows users?

Or those using a totally different bootloader like Easy BCD, legacy grub, lilo, or whatever Mac uses?

I noticed that Steve Langasek made some changes to this bug report of mine:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Specific to Maverick:

> Changed in grub2 (Ubuntu Maverick):
status: 	Triaged &#8594; Invalid 

So I probably need to start a new bug report specific to Maverick but I'd like to gather more info first. Specifically, has anyone else noticed this if using a different bootloader?

I don't have Windows on this machine so I can't really test anything Windows related ATM, but I wonder for instance if someone had Windows on /dev/sda and Ubuntu on another drive (internal or external) what happens?

Anyway I'd really like to hear from anyone on this issue. The sooner we can gather info the better.

---

### Post by kansasnoob on 2010-06-23
I left the following comment on that existing bug report:

> 

@ Steve Langasek,

I noticed in Maverick that upgrades of the packages "grub-common" and "grub-pc" on both the 21st and 23rd resulted in Maverick's grub 2 "grabbing" the mbr of /dev/sda with no user interaction whatsoever.

To be a bit more specific I multi-boot and currently I have Karmic's grub 2 in charge of booting, but the aforementioned package upgrades automatically resulted in Maverick's grub 2 installing to the mbr of /dev/sda.

I don't currently have Windows installed so I can't see what would happen if, for instance, I had a Windows mbr on /dev/sda and grub 2 on /dev/sdb. Does grub 2 now just automatically install to /dev/sda always?

As I think about this there is testing I can do such as installing lilo or legacy grub to various mbrs and then trying some test installs followed by updating the aforementioned packages.

Or maybe the grub 2 devs could briefly explain the new behavior?

I did start a thread at the forums to hopefully gather more info:

[http://ubuntuforums.org/showthread.php?t=1516153](http://ubuntuforums.org/showthread.php?t=1516153)

I realize this is a different issue (totally different behavior) so if this is a bug (and it may not be) I anticipate the possible need for a new bug report.

My time is seriously limited ATM but I will try my best to set aside whatever time is needed to address this issue. I'd think it's far from critical since Maverick is still in early alpha testing.


Hopefully one of the devs will take the time to explain the new behavior.

---

### Post by ronacc on 2010-06-23
thanks I'll add my me too , I also multi boot off multiple drives and this could really screw me . For instance right now I am booting maverick off of sabayons mbr on sda and maverick is on sdc3&4 with its grub in the partition , lucid is on sdc1$2 an it "owns" the mbr of sdc .

---

### Post by ranch hand on 2010-06-23
I noticed the auto installation the other day and again today.  As all my custom files are the same it gives me the same menu with a different background.  This is not a problem for me.

It could be a very large problem for a bunch of folks.

I am in the middle of cleaning up some storm damage around here and do not have time to file on this one.

If it is filed on, please leave a link so I can join in.

Got to go fire up the chain saw.

---

### Post by kansasnoob on 2010-06-23
> **ranch hand said:**
> I noticed the auto installation the other day and again today.  As all my custom files are the same it gives me the same menu with a different background.  This is not a problem for me.

It could be a very large problem for a bunch of folks.

I am in the middle of cleaning up some storm damage around here and do not have time to file on this one.

If it is filed on, please leave a link so I can join in.

Got to go fire up the chain saw.

I'm in a similar situation. That is very limited time :p

No recent storm damage but I had a small kitchen fire many moons ago and my living room basically became my kitchen. So getting my kitchen back in order has become an absolute priority!

Even a piggy like me gets tired of living like a pig after a while :lolflag:

I just figured that a thread about this would allow us to share our experiences. I'm puzzling over how exactly to test this without a total reinstall :confused:

I'm hoping that just "reconfigure" will result in the same behavior. Hopefully some evening I'll have a chance to explore a bit more.

---

### Post by dino99 on 2010-06-23
to me grub2 is better than before, but:

first cold boot always fail (kernel panic)

second cold boot: boot fast without trouble but reboot dont work at all.

3 hdds
- pata1: xp
- pata2: lucid32, maverick32, grub2 on mbr (maverick)
- sata1: jaunty64, grub2 on mbr (maverick)

have no custom configs, grub menu is always updated as it might, no matter which distro is used

*** when i have (had) some issues with grub2, i always remove/purge grub-pc then reinstall from synaptic ***

---

### Post by philinux on 2010-06-23
I had this set up.

Grub2 installed to mbr sda, lucid, and installed to sdb1 pbr for maverick. Chainloading from sda.

After today's update it seems it's changed like you describe. Although everything is booting as before.

---

### Post by Nr90 on 2010-06-23
Hmm I had a custom bootloader (BURG).
After todays update it did the same you described, so I get regular grub when booting.
That's fine.

However when looking at my list of kernels to select the newest one appears to be 2.6.35-5-generic , however I just updated and downloaded the current one which should be 2.6.35-6 which does not show.
Any ideas?

Sorry if this is a thread steal/derail.

---

### Post by Slug71 on 2010-06-23
> **Nr90 said:**
> Hmm I had a custom bootloader (BURG).
After todays update it did the same you described, so I get regular grub when booting.
That's fine.

However when looking at my list of kernels to select the newest one appears to be 2.6.35-5-generic , however I just updated and downloaded the current one which should be 2.6.35-6 which does not show.
Any ideas?

Sorry if this is a thread steal/derail.

2.6.35-5 is the latest.

---

### Post by ronacc on 2010-06-23
there has often been a similar situation with the install disk , where it would ONLY install grub to the MBR of SDA , this is the first time I've seen it with an update though .

---

### Post by autocrosser on 2010-06-23
One thing I noted is that the structure of /etc/grub.d/05_debian_theme (I think this is wrong--away from my install--but look thru grub.d) has changed--My custom theme went back to the black/white cruft....As soon as I get home tonight I'll post what I did to get things back to normal.

It "looks" like this is the pre-prep to allow themes in grub--we shall see.......I needed to create a folder in /usr/share (I'll post where tonight) & put my .png images there---do a bit of hunting & you will see it......

---

### Post by 23meg on 2010-06-23
Colin Watson [wrote about]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") recent changes to GRUB 2 a few days ago. I was thinking of stickying it temporarily; looks like it might be needed. 

This bit is probably relevant to the problems some people are having:

[QUOTE=Colin Watson]If you had set up GRUB 2 to be automatically chainloaded from GRUB Legacy (which happens automatically on upgrade from the latter to the former), never got round to running upgrade-from-grub-legacy  once you confirmed it worked, and then later ran grub-install  by hand for one reason or another, then the core image you installed by hand would never be updated and would eventually fall over the next time the core/modules interface changed.[/QUOTE]

Please read [the whole post]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") if your bootloader has been problematic recently, or after upgrading to Maverick, or if you're interested in testing GRUB 2 in general.

---

### Post by kansasnoob on 2010-06-23
> **ronacc said:**
> there has often been a similar situation with the install disk , where it would ONLY install grub to the MBR of SDA , this is the first time I've seen it with an update though .

That's really a whole different thing. I believe, even with legacy grub, that the default has always been /dev/sda during installation. To me that makes perfectly good sense.

I'm not talking about the installer (ubiquity) but rather update procedures. While I know how to make things work regardless, many noobs don't!

I just want to make Ubuntu as noob friendly now as it was to me with Gutsy :)

---

### Post by VMC on 2010-06-23
I always do a manual install, and un-tick the advance section so it doesn't write to the mbr. I've never had a problem using it that way, and haven't used auto install in a long time.

---

### Post by wilee-nilee on 2010-06-23
> **VMC said:**
> I always do a manual install, and un-tick the advance section so it doesn't write to the mbr. I've never had a problem using it that way, and haven't used auto install in a long time.

I think the a topic is the grub update/upgrade that happened lately.

---

### Post by kansasnoob on 2010-06-23
> **23meg said:**
> Colin Watson [wrote about]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") recent changes to GRUB 2 a few days ago. I was thinking of stickying it temporarily; looks like it might be needed. 

This bit is probably relevant to the problems some people are having:



Please read [the whole post]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") if your bootloader has been problematic recently, or after upgrading to Maverick, or if you're interested in testing GRUB 2 in general.

Stepping onto the bold side I believe Colin Watson has detached from "end user reality" long ago!

I've tried very hard to work with Colin since the introduction of grub 2 and quite simply it seems to either go Colin's way or no way at all.

With 10.04 the result was disastrous!

In the meanwhile we that truly care about noobs try to deal with bad decisions.

---

### Post by ranch hand on 2010-06-23
And it is a bugger to do if you know as little about MS boot loaders as I do.

I suspect most MS users are as ignorant about it as I am or more so.  This really makes the grub problem, to me, rather urgent.

---

### Post by kansasnoob on 2010-06-23
> **wilee-nilee said:**
> I think the a topic is the grub update/upgrade that happened lately.

Correct!

This has nothing to do with installation!

It has only to do with updates and upgrades!

How can I make that more clear?

The title of this thread says "package upgrade"!

Look, I'm doing the best I can, and it appears that the grub 2 dev just doesn't like me. That's possible because I argued about getting a newer grub 2 package in Karmic.

Regardless of the reason grub 2 upgrades went to heck in a hand basket with Lucid! This should not have happened!

I'm partly responsible because I failed to recognize this behavior earlier, but still today no fix is committed!

Now we have ridiculous behavior in Maverick!

I actually think I'm done with this. It's not a big deal to me and I'm tired of fighting.

I can easily restore the mbr when and where I please so I'm thinking I just can't deal with Colin's negligence any longer.

---

### Post by wilee-nilee on 2010-06-23
> **kansasnoob said:**
> 

With 10.04 the result was disastrous!

In the meanwhile we that truly care about noobs try to deal with bad decisions.

You said it, I like to see people having a choice, and the ability to run multiple OS.

---

### Post by kansasnoob on 2010-06-23
> **23meg said:**
> Colin Watson [wrote about]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") recent changes to GRUB 2 a few days ago. I was thinking of stickying it temporarily; looks like it might be needed. 

This bit is probably relevant to the problems some people are having:



Please read [the whole post]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") if your bootloader has been problematic recently, or after upgrading to Maverick, or if you're interested in testing GRUB 2 in general.

I'm an end user with limited skills. I'd guess most folks that use Ubuntu are in the same category.

I understand about 10% of what Colin is saying there, or maybe less! But I would like everyone's experience with dual-booting Ubuntu and Windows to be as enjoyable as it was for me about 2 1/2 years ago. 

Sadly that's not the case! I've personally helped dozens, and witnessed hundreds, of Windows users that experienced this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

At this point I truly feel I'm just done with it!

What else can I do?

---

### Post by ronacc on 2010-06-23
> **kansasnoob said:**
> That's really a whole different thing. I believe, even with legacy grub, that the default has always been /dev/sda during installation. To me that makes perfectly good sense.

I'm not talking about the installer (ubiquity) but rather update procedures. While I know how to make things work regardless, many noobs don't!

I just want to make Ubuntu as noob friendly now as it was to me with Gutsy :)

I realize that this is a different situation , I was just remarking that sometimes the installer ( ubiquity ) acts the same way . And by the way the installer does present you with the choice to either not install grub or else to install it to a different drive , on the last page before the install begins is a box labeled "advanced" if you click that , that is where the choices for grub are, unfortunately ubiquity dosen't always pay attention to your choice .

---

### Post by kansasnoob on 2010-06-23
> **ronacc said:**
> I realize that this is a different situation , I was just remarking that sometimes the installer ( ubiquity ) acts the same way . And by the way the installer does present you with the choice to either not install grub or else to install it to a different drive , on the last page before the install begins is a box labeled "advanced" if you click that , that is where the choices for grub are, unfortunately ubiquity dosen't always pay attention to your choice .

AFAIK ubiquity has always chosen /dev/sda unless the user clicked on "advanced" and I think that's fine.

The upgrade/update behavior was good in Karmic, but in Lucid it changed to "allowing" installation to all pbr's!

Now in Maverick it seems to either be always /dev/sda or maybe anywhere it detects a grub 2 mbr :confused:

Regardless I'm pretty much done with this for a while. I get tired of having to explain the obvious and never getting anywhere.

---

### Post by seeker5528 on 2010-06-23
> **kansasnoob said:**
> I noticed following package upgrades of "grub-common" and "grub-pc" on both the 21st and today (the 23rd) that grub 2 automatically "installs" to the mbr of the drive. If you previously selected a location on a clean install of Ubuntu, or reconfigured grup-pc and chose something other than the default, then during a later upgrade grub gets installed somewhere that was not selected, then I would call that a bug.
 
> So I already had a grub 2 mbr, although it was assigned to /dev/sda2 (Karmic), but following the updates sda1 had the mbr.

The MBR is it's own entity at the beginning of the drive, sda1 and sda2 would each have their own BR, but at no time would they "have the MBR".

> Now, this is no big deal to me because I only need to boot into Karmic again and run "grub-install /dev/sda",

If you manually told grub to install to something other than the default location at some point but did not reconfigure grub-pc and choose that same location as the desired location either by running synaptic, finding grub-pc in the list, selecting it, then choosing 'configure' on the packages menu, or by opening a terminal window and typing:

```
sudo dpkg-reconfigure grub-pc
```

Then that wouldn't be a bug in grub-pc.

>  but I wonder what kind of a storm this might create with Windows users?

Typically a non-issue if they are sticking with the default and installing grub to /dev/sda.

> I noticed that Steve Langasek made some changes to this bug report of mine:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

Specific to Maverick:

So I probably need to start a new bug report specific to Maverick but I'd like to gather more info first.

If in Maverick it no longer asks you where you want to install grub and/or no longer suggests that if you don't know the answer just install it everywhere, that would make the bug invalid for Maverick, correct? 

> I don't have Windows on this machine so I can't really test anything Windows related ATM, but I wonder for instance if someone had Windows on /dev/sda and Ubuntu on another drive (internal or external) what happens?

Windows has to be on a partition, so it would not be on /dev/sda.

If Windows doesn't control the MBR, some updates will fail with certain versions of Windows Vista or Windows 7. This can make it more convenient to have more than one hdd with Windows on the secondary drive so you can switch the boot to that when needed, but that's not Grub's problem.

If you ran 'grub-install' to manually install grub somewhere different than where grub-pc is configured to install grub and didn't reconfigure grub-pc, then it's not grub's fault if a later update goes to the location grub-pc is configured for and not the location you manually installed grub to.

With more recent desktop machines things get a little more complicated as more and more HDD boot priority gets changed automatically in the BIOS as HDDs are added or removed, making things all that much more unpredictable.

This stuff definitely could use some improvement, but from this thread, I'm not 100% sure what the complaints are.....

If people did a clean install and selected somewhere other than /dev/sda.

Or whether things were set up later and.....

If grub-install or some other manual method was used to get grub installed to the desired location, which may be a necessary step.

If people reconfigured grub-pc to remove locations they don't want grub installed to and add the locations they do.

And in which of these situations did a problem result during a later update?

Later, Seeker

---

### Post by ranch hand on 2010-06-23
@seeker5528
I have, personally, done my best to help new users correct their MS boot sector from default installs of grub2 (which I love).

This is not an issue with me.  I only use Linux.  I think MS is for simple minded folks that like to be insulted by their OS.

While this is an attitude that I expect from me it does not stop me from trying to help these folks.  They may wake up.

These problems have occurred with clean installs of 10.04 and upgrades from 9.10.  It is not a non issue for the folks involved.  There has been no custom installs of grub involved.  This has been where the installer or the upgrade has put it.

---

### Post by ronacc on 2010-06-23
> **kansasnoob said:**
> AFAIK ubiquity has always chosen /dev/sda unless the user clicked on "advanced" and I think that's fine.

The upgrade/update behavior was good in Karmic, but in Lucid it changed to "allowing" installation to all pbr's!

Now in Maverick it seems to either be always /dev/sda or maybe anywhere it detects a grub 2 mbr :confused:

Regardless I'm pretty much done with this for a while. I get tired of having to explain the obvious and never getting anywhere.

yes it has always DEFAULTED to the mbr of SDA , what I said was that even if you manually selected another drive or partition it would ignore you and put it on sda anyway ( not always but sometimes ) . I usually select NO GRUB and just put a boot stanza where I want it (not for noobs ) unless sda happens to be my target drive that go around .( ubiquity is not always good about finding your other installs ).

---

### Post by wilee-nilee on 2010-06-23
> **seeker5528 said:**
> If you previously selected a location on a clean install of Ubuntu, or reconfigured grup-pc and chose something other than the default, then during a later upgrade grub gets installed somewhere that was not selected, then I would call that a bug.
 


The MBR is it's own entity at the beginning of the drive, sda1 and sda2 would each have their own BR, but at no time would they "have the MBR".



If you manually told grub to install to something other than the default location at some point but did not reconfigure grub-pc and choose that same location as the desired location either by running synaptic, finding grub-pc in the list, selecting it, then choosing 'configure' on the packages menu, or by opening a terminal window and typing:

```
sudo dpkg-reconfigure grub-pc
```

Then that wouldn't be a bug in grub-pc.



Typically a non-issue if they are sticking with the default and installing grub to /dev/sda.



If in Maverick it no longer asks you where you want to install grub and/or no longer suggests that if you don't know the answer just install it everywhere, that would make the bug invalid for Maverick, correct? 



Windows has to be on a partition, so it would not be on /dev/sda.

If Windows doesn't control the MBR, some updates will fail with certain versions of Windows Vista or Windows 7. This can make it more convenient to have more than one hdd with Windows on the secondary drive so you can switch the boot to that when needed, but that's not Grub's problem.

If you ran 'grub-install' to manually install grub somewhere different than where grub-pc is configured to install grub and didn't reconfigure grub-pc, then it's not grub's fault if a later update goes to the location grub-pc is configured for and not the location you manually installed grub to.

With more recent desktop machines things get a little more complicated as more and more HDD boot priority gets changed automatically in the BIOS as HDDs are added or removed, making things all that much more unpredictable.

This stuff definitely could use some improvement, but from this thread, I'm not 100% sure what the complaints are.....

If people did a clean install and selected somewhere other than /dev/sda.

Or whether things were set up later and.....

If grub-install or some other manual method was used to get grub installed to the desired location, which may be a necessary step.

If people reconfigured grub-pc to remove locations they don't want grub installed to and add the locations they do.

And in which of these situations did a problem result during a later update?

Later, Seeker

:lolflag::lolflag::lolflag:
You have no clue your just arguing for arguments sake, I wont even bother to explain it too you.

---

### Post by bcbc on 2010-06-24
> **kansasnoob said:**
> 
I don't have Windows on this machine so I can't really test anything Windows related ATM, but I wonder for instance if someone had Windows on /dev/sda and Ubuntu on another drive (internal or external) what happens?

Anyway I'd really like to hear from anyone on this issue. The sooner we can gather info the better.

I just ran the updates - grub-pc and grub-common included - and didn't have any changes to my MBRs. 

I have maverick on an external drive in partition /dev/sdb10, and I purposely installed the bootloader on /dev/sdb from a lucid install on /dev/sdb9 before running the updates.

I also have a grub2 on /dev/sda pointed to a a karmic install on /dev/sda5 which was not affected.

---

### Post by VMC on 2010-06-24
> **ronacc said:**
> I realize that this is a different situation , I was just remarking that sometimes the installer ( ubiquity ) acts the same way . And by the way the installer does present you with the choice to either not install grub or else to install it to a different drive , on the last page before the install begins is a box labeled "advanced" if you click that , that is where the choices for grub are, unfortunately ubiquity dosen't always pay attention to your choice .

Ronacc, that's what I was commenting about. But apparently this topic is on the grub2 upgrade and not the install portion.

Usually though whenever you "touch" grub anything it try's to update the MBR. That's why I keep my grub belonging to another partition other than the one I test on. That way I avoid any updated grub coming along and trying to re-write mbr.

---

### Post by kansasnoob on 2010-06-25
@ seeker5528,

Perhaps I abbreviated parts of my explanation somewhat poorly. I'm fully aware of what an MBR is. To clarify, I multiboot several OS's largely for testing purposes.

Karmic is installed on /dev/sda2 and controls boot so when I said it "had" the mbr I simply meant "Grub 2 was installed in the MBR of /dev/sda and looked on the same drive in partition #2 for /boot/grub."

After the aforementioned updates in Maverick which is on /dev/sda1 "Grub 2 was installed in the MBR of /dev/sda but now looked on the same drive in partition #1 for /boot/grub."

So the update procedure resulted in Maverick "silently" installing it's grub2 to the mbr of /dev/sda. That's no big deal to me because I know that I only need to boot into Karmic and run 'grub-install /dev/sda'.

I'm just trying to learn what exactly the new behavior is and what will happen in different scenarios.

Specifically you asked:

> Windows has to be on a partition, so it would not be on /dev/sda.

My point was that it's not uncommon for someone to have Windows on /dev/sda (which partition doesn't matter), it's working perfectly, and they want to install Ubuntu on a different drive (internal or external doesn't really matter), but they want to leave the Win MBR alone on /dev/sda.

They would, of course, always want to leave the MBR alone on /dev/sda regardless of OS if installing Maverick to an external, eh? So I'm wondering what this new update/upgrade behavior will do in such scenarios?

Also, in reference to my mentioning Steve Langasek marked that old bug invalid for Maverick you said:

> If in Maverick it no longer asks you where you want to install grub and/or no longer suggests that if you don't know the answer just install it everywhere, that would make the bug invalid for Maverick, correct? 

Where do I suggest otherwise? In fact I said, "So I probably need to start a new bug report specific to Maverick but I'd like to gather more info first." And if you read the bug report I say there, "I realize this is a different issue (totally different behavior) so if this is a bug (and it may not be) I anticipate the possible need for a new bug report."

My hope is to gather info from other end users so we don't end up with a poor outcome after final release, like people reporting that their mbr is changed after certain updates.

---

### Post by kansasnoob on 2010-06-25
> **VMC said:**
> Ronacc, that's what I was commenting about. But apparently this topic is on the grub2 upgrade and not the install portion.

Usually though whenever you "touch" grub anything it try's to update the MBR. That's why I keep my grub belonging to another partition other than the one I test on. That way I avoid any updated grub coming along and trying to re-write mbr.

> That's why I keep my grub belonging to another partition other than the one I test on. That way I avoid any updated grub coming along and trying to re-write mbr.

But, that's exactly what happened in my case :D

Karmic was controlling boot but after the updates Maverick had taken over. Now, that was no big deal because I needed only boot into Karmic using Maverick's boot menu and then use 'grub-install' to have Karmic take control again.

I'm just curious what will happen in different scenarios :confused:

Particularly if someone has a Win MBR on /dev/sda? Or a legacy grub mbr, or Mac? Or what if Maverick were on /dev/sdb? Would it then "grub-install" to sdb silently, or still sda?

That's why I thought it would be good to discuss this here and try to monitor various behaviors and outcomes.

---

### Post by philinux on 2010-06-25
I'm fully up to date. Via chroot from lucid.

I posted my boot info script output back in this thread. Now I'm not seeing a change.

I have grub on sda mbr in lucid and mav grub on sdb1 pbr. I used the advance option on install.

Lucid grub is still in control with a chainload to sdb.

---

### Post by dino99 on 2010-06-25
> **kansasnoob said:**
> But, that's exactly what happened in my case :D

Karmic was controlling boot but after the updates Maverick had taken over. Now, that was no big deal because I needed only boot into Karmic using Maverick's boot menu and then use 'grub-install' to have Karmic take control again.

I'm just curious what will happen in different scenarios :confused:

Particularly if someone has a Win MBR on /dev/sda? Or a legacy grub mbr, or Mac? Or what if Maverick were on /dev/sdb? Would it then "grub-install" to sdb silently, or still sda?

That's why I thought it would be good to discuss this here and try to monitor various behaviors and outcomes.

As devs dont think as users does, and badly designed this grub2 installation (= reinstall, upgrade and so on), its a pain to continously repeat how to install it correctly and how to repair when user have followed the default process, and mainly ignore what will happen to their other bootloaders if any).

So how to do better ? i only see a "sticky" about this on most of these forums: general help, absolute beginners, update/upgrade, laptop (maybe some others) hoping the newbies come here first before installation.

To me the good location is where ubuntu is installed, no need confusion(s).

---

### Post by VMC on 2010-06-25
> **kansasnoob said:**
> ...
Karmic was controlling boot but after the updates Maverick had taken over. Now, that was no big deal because I needed only boot into Karmic using Maverick's boot menu and then use 'grub-install' to have Karmic take control again.

...

Now I fully understand what your/our issue is! I haven't done any updates as of yet. Just reload from iso using zsync. Now I'll have to try it.

So you never get the maintainers menu asking for directions?

---

### Post by seeker5528 on 2010-06-25
> **kansasnoob said:**
> Karmic is installed on /dev/sda2 and controls boot so when I said it "had" the mbr I simply meant "Grub 2 was installed in the MBR of /dev/sda and looked on the same drive in partition #2 for /boot/grub."

After the aforementioned updates in Maverick which is on /dev/sda1 "Grub 2 was installed in the MBR of /dev/sda but now looked on the same drive in partition #1 for /boot/grub."

So the update procedure resulted in Maverick "silently" installing it's grub2 to the mbr of /dev/sda. That's no big deal to me because I know that I only need to boot into Karmic and run 'grub-install /dev/sda'.

So the question there is.... Was the Maverick installation ever set up to install grub into the MBR, was it set up to install grub to the partition Maverick is on, or was it set not to install grub anywhere.

If it was set to install on the Maverick partition or not to be installed anywhere and the update cause it to be installed in the MBR, then clearly that is unwanted behavior.

If when Maverick was installed it was set to install grub to the MBR and when Karmic was installed it was set to install Grub to the MBR, then there is a conflict and having an update to grub in one or the other or both of these cause grub to be installed to the MBR again would not be out of line. If they are both grub 2 then in one or the other of these you would preferably use the package management tools to reconfigure the grub-pc package to select which MBR or partition you want grub installed to. Just using grub-install for within the distribution that you want controlling the MBR is not enough.    

> I'm just trying to learn what exactly the new behavior is and what will happen in different scenarios.

I have no issue with that, but to have a clear picture you need a little history and not just a snapshot of how things were just before and just after the update in question.

> My point was that it's not uncommon for someone to have Windows on /dev/sda (which partition doesn't matter), it's working perfectly, and they want to install Ubuntu on a different drive (internal or external doesn't really matter), but they want to leave the Win MBR alone on /dev/sda.

When you start throwing multiple drives in there things start to get more complicated.

If they are all SATA or all PATA, shouldn't be an issue, the same things apply as do above.

If your HDDs are a mix of SATA and PATA, then what is SDA one time may not be SDA another time depending on which subsystem gets detected first. I don't know if > Unless anything new shows up, that just leaves the problems that were already understood. Today, I posted a patch to generate stable device names in device.map by default. If this is accepted, then we can do something or other to fix up device.map on upgrade, switch over to /dev/disk/by-id names in grub-pc/install_devices  at the same time, and that should take care of the vast majority of this kind of upgrade bug. [(previously linked to)](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems) is a complete solution to that, but if nothing else it does sound like it should alleviate many problems during upgrades/updates. And should also help with...

> They would, of course, always want to leave the MBR alone on /dev/sda regardless of OS if installing Maverick to an external, eh? So I'm wondering what this new update/upgrade behavior will do in such scenarios?

And yes I would expect most people when installing to an external drive would want grub installed to the MBR of that drive.

Being external does bring other questions to mind, but if it has already been set up and working and configured where to install grub to, an update should not cause grub to be installed somewhere else.

> My hope is to gather info from other end users so we don't end up with a poor outcome after final release, like people reporting that their mbr is changed after certain updates.

Information is good if there is enough to understand the chain of events leading in to the situation in question and if hardware or some other factor outside of grub may have contributed to the situation.

Later, Seeker

---

### Post by psusi on 2010-06-25
Huh?  Grub has always been reinstalled when it was upgraded -- it kind of has to.  If you dpkg-reconfigure the grub-pc package, you can change where it is configured to install the MBR to.

---

### Post by kansasnoob on 2010-06-26
@ Seeker,

First of all thanks for your input :)

> Was the Maverick installation ever set up to install grub into the MBR, was it set up to install grub to the partition Maverick is on, or was it set not to install grub anywhere.

Well, this Maverick was upgraded from Lucid on 05/22/2010 and, since it's on /dev/sda1, I would guess that "that Lucid" had control of boot when originally installed.

I almost never install grub (legacy or grub 2) to a partition. There's rarely an actual need to do so. Grub 2 is IMHO far superior to Easy-BCD, GAG, or anything else.

> Just using grub-install for within the distribution that you want controlling the MBR is not enough. 

Well, that's a new one to me :p

This is exactly why I began a discussion here rather than filing a new bug report, although Colin Watson did request more info following my comment on the old Lucid bug report.

Up until now I have always just used "grub-install" to change which OS's grub 2 controls boot. So, just now, I used "dpkg-reconfigure":

```
lance@lance-desktop:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-6-generic
Found initrd image: /boot/initrd.img-2.6.35-6-generic
Found linux image: /boot/vmlinuz-2.6.35-5-generic
Found initrd image: /boot/initrd.img-2.6.35-5-generic
Found linux image: /boot/vmlinuz-2.6.35-4-generic
Found initrd image: /boot/initrd.img-2.6.35-4-generic
Found linux image: /boot/vmlinuz-2.6.35-3-generic
Found initrd image: /boot/initrd.img-2.6.35-3-generic
Found linux image: /boot/vmlinuz-2.6.35-2-generic
Found initrd image: /boot/initrd.img-2.6.35-2-generic
Found linux image: /boot/vmlinuz-2.6.34-5-generic
Found initrd image: /boot/initrd.img-2.6.34-5-generic
Found linux image: /boot/vmlinuz-2.6.34-4-generic
Found initrd image: /boot/initrd.img-2.6.34-4-generic
Found Linux Mint 9 Isadora (9) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.04 LTS (10.04) on /dev/sda12
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04 LTS (10.04) on /dev/sda3
Found Ubuntu 10.04 LTS (10.04) on /dev/sdb2
done

```

And of course I had to select the expected defaults, then this familiar "device-install" dialog appears:

[ATTACH]161613[/ATTACH]

As you can see there /dev/sda was selected by default, I then deselected it and continued, and of course had to confirm that I wanted to continue without installing the bootloader.

During the second "updates" (and anticipating this change in behavior from the first time) I snapped this screenshot before even beginning this discussion:

[ATTACH]161614[/ATTACH]

As you can see there it only said, "Setting up grub-pc ........... installation finished .....", so it had "silently" installed grub to the mbr of /dev/sda without requesting whether or not to do so.

So, if it's as simple as using "dpkg-reconfigure" to make an OS's grub 2 know where (or whether) it should be installed to any device during future updates/upgrades, I suppose that is acceptable behavior. I do still wonder though what this behavior will be like in various other scenarios :confused:

For instance it's not at all uncommon for someone installing Ubuntu to an external drive the first time to "miss" the Advanced option during installation and then have to recover the Windows MBR on the internal, and it's common practice to just use "grub-install" to install grub 2 to the MBR of the external. I believe most documentation will reflect that.

I actually preferred the behavior in Karmic where you'd be presented with the option of being able to select ONLY drive designations during updates/upgrades, but OTOH I can see the benefit of having most users not have to make any decision.

Anyway, I'm going to reboot to check things out for sure, then "dpkg-reconfigure" again and see what the repeat behavior is.

---

### Post by oldfred on 2010-06-26
This supposely was fixed for Lucid.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)

The dpkg was a work around mentioned in above bug. It is supposed to save into /var/cache/debconf/config.dat. Not sure if it is the same for Maverick.

---

### Post by philinux on 2010-06-26
My dual boot is working fine after this grub2 upgrade. But how do I remove, or do I not bother, grub from the sdb1 pbr.

```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
   partition #1 for /boot/grub

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 17056447 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

---

### Post by kansasnoob on 2010-06-26
> **psusi said:**
> Huh?  Grub has always been reinstalled when it was upgraded -- it kind of has to.  If you dpkg-reconfigure the grub-pc package, you can change where it is configured to install the MBR to.

I'm not suggesting otherwise :)

The behavior in Karmic was to display only drive "device-names" during package updates or a dist-upgrade.

The behavior in Lucid was to display drive **and partition** "device-names" during package updates or dist-upgrades and that was disastrous :(

The current behavior in Maverick is to "silently" install grub ........... not sure how the "where or if" are determined ............. which is the reason for this thread, and I think Seeker is totally helping educate me on that :D

Look, I largely blame myself for not recognizing this bug sooner:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

In post #7 there I say:

> I'm part of the problem because I blew it off for weeks blaming it on "the bug between the chair and the keyboard" so you can blame me for not more aggressively pursuing this throughout iso-testing and upgrade testing.

Therefore I intend to be diligent in following grub 2 development to avoid such a thing in Maverick (and hopefully see a fix applied in the first "point-release" of Lucid).

The reason for this thread is to hopefully learn more so I can be as helpful as possible in correcting/preventing grub 2 related bugs. I always try to make clear that I'm just an end user with no actual tech training of any sort (other than Auto/Diesel many moons ago).

Colin Watson does great and I hope I've never come across as suggesting otherwise. IMHO successful development requires not only a capable developer like Colin, but also dummies like me to test and ask dumb questions, and I must also ask myself from time to time, "would I have understood this when I first discovered Ubuntu"?

---

### Post by kansasnoob on 2010-06-26
> **philinux said:**
> My dual boot is working fine after this grub2 upgrade. But how do I remove, or do I not bother, grub from the sdb1 pbr.

```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
   partition #1 for /boot/grub

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 17056447 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

AFAIK there's no need to bother, but I may learn I'm wrong.

---

### Post by philinux on 2010-06-26
I be interested to know why, in my case, maverick grub did not take over.

My custom lucid grub is still in charge.

---

### Post by ranch hand on 2010-06-26
You do not want to remove the grub files fro m sda1.

The grub installed on the MBR gets its information from the files on sda1.   Those are the files that will be upgraded and then installed on the MBR (again) to upgrade it.

---

### Post by kansasnoob on 2010-06-26
> **23meg said:**
> Colin Watson [wrote about]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") recent changes to GRUB 2 a few days ago. I was thinking of stickying it temporarily; looks like it might be needed. 

This bit is probably relevant to the problems some people are having:



Please read [the whole post]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/06/21#2010-06-21-grub2-boot-problems") if your bootloader has been problematic recently, or after upgrading to Maverick, or if you're interested in testing GRUB 2 in general.

My earlier comment (#20) sounded a bit harsh, sorry :redface:

But, quite simply, Colin is so technically superior to me that it's like trying to understand the radiologists report of my latest MRI :confused:

By the time my neurologist translates it I sort of understand ............ only "sort of" ;)

---

### Post by kansasnoob on 2010-06-26
OK, following up on Seeker's advice, it appears that having run "dpkg-reconfigure grub-pc" and making the proper selections results in defaulting to the proper behavior :guitar:

I will however try some different scenarios as time allows, and hopefully we can all monitor the behavior as development proceeds.

So, if this behavior stands "as-is", I'd guess reinstalling grub 2 needs to be done with "dpkg-reconfigure" rather than "grub-install" to ensure that the preferred behavior is saved as default.

That certainly seems simple enough.

---

### Post by philinux on 2010-06-26
> **ranch hand said:**
> You do not want to remove the grub files fro m sda1.

The grub installed on the MBR gets its information from the files on sda1.   Those are the files that will be upgraded and then installed on the MBR (again) to upgrade it.

I didn't mean the files I meant grub installation of the Partition Boot Record.

---

### Post by seeker5528 on 2010-06-26
> **kansasnoob said:**
> So, if this behavior stands "as-is", I'd guess reinstalling grub 2 needs to be done with "dpkg-reconfigure" rather than "grub-install" to ensure that the preferred behavior is saved as default.

Don't know if doing a reconfigure will cause grub to be installed or if it just changes the location where the packaging scripts will install it when you upgrade the packages.

You might still have to run grub-install after doing the reconfigure in between the times when there is a newer package available.

If you do a reconfigure just before installing newer packages, then the newer grub should be installed in the desired locations.

Later, Seeker

---

### Post by ranch hand on 2010-06-26
> **philinux said:**
> I didn't mean the files I meant grub installation of the Partition Boot Record.
Sorry, you still do not need do any thing about it as long as it is not bothering any thing.

Just pretend it isn't there and it won't hurt a thing.  Removing it would be a real pain and may screw something.

---

### Post by kansasnoob on 2010-06-26
> **seeker5528 said:**
> Don't know if doing a reconfigure will cause grub to be installed or if it just changes the location where the packaging scripts will install it when you upgrade the packages.

You might still have to run grub-install after doing the reconfigure in between the times when there is a newer package available.

If you do a reconfigure just before installing newer packages, then the newer grub should be installed in the desired locations.

Later, Seeker

My thought ATM is to have folks run "dpkg-reconfigure" **after** the "grub-install", or after the first time things do something unexpected.

Although it's nearly impossible to test each and every scenario. To some degree we need to "wait and see" how this change effects people.

---

### Post by oldfred on 2010-06-26
I just installed Maverick to my USB key from a USB key. Since I have 3 drives. I installed from sdd to sde. But I removed sdd when I rebooted and of course it would not reboot as there was not sde and the kernel line had sde in it.

I manually edited to get it to boot, run update grub and it replaced the sde with UUIDs. I also ran sudo dpkg-reconfigure grub-pc. I vaguely remember some discussion before, that it save by drive not by UUID, so I looked at /var/cache/debconf/config.dat  and the reinstall directory is sdd. But if I happen to plug in both USB keys and make my install sde and it does an update to grub, I think it will update my sdd not the sde unless every time before an update I run the reconfigure before hand. 

So anytime drive order could change the default may not be correct.

---

### Post by VMC on 2010-06-26
> **oldfred said:**
> .../var/cache/debconf/config.dat  and the reinstall directory is sdd. ....

I must be missing something here, but I don't see any correlation between the file "/var/cache/debconf/config.dat" and the boot process. Just a bunch of file names and there templates.

---

### Post by psusi on 2010-06-26
> **philinux said:**
> I be interested to know why, in my case, maverick grub did not take over.

My custom lucid grub is still in charge.

What is it set to install to when you run dpkg-reconfigure?  If it isn't set to sda, that would be why.  Judging from the fact that you have grub installed to the mbr of sdb, I would guess your maverick install is configured to install grub there, but your bios is booting from sda, which is why lucid is still the loader you get.

Having the MBR installed to non boot drives doesn't hurt anything, so I wouldn't worry about removing it.  In fact, if sda ever fails on you, it could come in handy since your system will be able to boot from sdb.

---

### Post by aviramof on 2010-06-27
As far as i see it it's great that grub install itself on the mbr of all drives in lucid for instance after installing ubuntu and restarting nothing would have changed it was automaticly boot to windows 7 despite the fact that i had an ext4 partition on it and i was forced to enter 
live cd again and install it again.

How ever in maverick ubiquity installed it properly on he's own so that a lot better then 
installing it manually and i hope it would stay like this if i would ever be forced to format
ubuntu and completly clean grub and then reinstall ubuntu.:)

---

### Post by bcbc on 2010-06-29
I did a maverick wubi install with the daily image. Still had to download > 200MB of changes. I can confirm that it does not install grub2 to the MBR. (The only interaction I had was the window in the image).

---

### Post by aviramof on 2010-06-30
If you installed using wubi then of course it want install grub at all what you just said it's incredibly ridiculous if you want it to install grub you need an ext4 partition and to install 
it in the normal way then it would install grub wubi is using windows boot manager to add itself to the boot menu and you can remove Ubuntu easily using windows add and remove 
options.

---

### Post by bcbc on 2010-06-30
> **aviramof said:**
> If you installed using wubi then of course it want install grub at all what you just said it's incredibly ridiculous if you want it to install grub you need an ext4 partition and to install 
it in the normal way then it would install grub wubi is using windows boot manager to add itself to the boot menu and you can remove Ubuntu easily using windows add and remove 
options.

Jeez, take a breath and read the thread. 

Kansasnoob was concerned that grub2 automatically installed itself to the MBR and wondered about whether it would overwrite a windows bootloader e.g. using wubi. I confirmed that it recognises wubi correctly and doesn't.

---

### Post by wilee-nilee on 2010-06-30
> **bcbc said:**
> Jeez, take a breath and read the thread. 

Kansasnoob was concerned that grub2 automatically installed itself to the MBR and wondered about whether it would overwrite a windows bootloader e.g. using wubi. I confirmed that it recognizes wubi correctly and doesn't.

I have had that user blocked for awhile now it's not worth the hassle. That was good work getting past the default Lucid download. When I installed wubi a couple of days ago I chose the no option as well.

---

### Post by bcbc on 2010-06-30
> **wilee-nilee said:**
> I have had that user blocked for awhile now it's not worth the hassle. That was good work getting past the default Lucid download. When I installed wubi a couple of days ago I chose the no option as well.

I haven't had to block anyone... yet. ;)

---

### Post by seeker5528 on 2010-07-01
This is looking interesting....

```
grub2 (1.98+20100614-2ubuntu4) maverick; urgency=low

* Only offer partitions containing /, /boot, or /boot/grub for
    grub-install; installing to other partitions may have harmful effects
    such as making Windows unbootable, and installing GRUB to every single
    partition is likely to result in confusion anyway (LP: #576724).
```

Don't know if that should be read that it will only offer installation to it's own /, /boot, or /boot/grub.... Or if that is to any /, /boot/, or /boot/grub. 

I would guess only it's own, but either way, should be an improvement.

Later, Seeker

---

### Post by dino99 on 2010-07-02
the debconf dialog box is still very confusing with its:

"Continue without installing Grub ?"

as there is no choice (you need to check it anyway) and if checked, grub is installed secretly and blindly, even if this silly question talk about "without"

---

### Post by seeker5528 on 2010-07-02
> **dino99 said:**
> the debconf dialog box is still very confusing with its:

"Continue without installing Grub ?"

as there is no choice (you need to check it anyway) and if checked, grub is installed secretly and blindly, even if this silly question talk about "without"

Your post is confusing to me.

A: "Continue without installing Grub ?" is a yes or no question. Choose yes or choose no. What's confusing about that? or now that I think about it in the Graphical version of the dialong checked should be yes, unchecked should be no, which I could concede does leave some room for confusion.

B: What makes you think if you chose to continue without installing grub that grub was "installed secretly and blindly"?

The presentation of the messages you see during installation may vary depending on whether you are seeing graphical dialogs or curses dialogs, but the information you are asked for and that you provide are the same either way and the end result should be the same.

When I do it the 'dpkg-reconfigure grub-pc' way, when there is a location selected for grub to install, the first text after proceeding from the last question is....

> Installation finished. No error reported.

If I choose not to install it anywhere there is no message about installation. 

Choosing not to install does not get rid of anything that may have previously been installed in any of the boot records.

Whether grub gets installed in any of these locations or not, the menu stuff in /boot/grub is still generated which, when doing this the 'dpkg-reconfigure grub-pc' way, causes messages like this to show up....

```
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-6-generic
Found initrd image: /boot/initrd.img-2.6.35-6-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

Later, Seeker

---


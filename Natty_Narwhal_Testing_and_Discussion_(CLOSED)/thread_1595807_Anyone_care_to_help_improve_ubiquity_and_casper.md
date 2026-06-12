---
title: "Anyone care to help improve ubiquity and casper?"
date: 2010-10-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-10-13
*Sorry if this is a bit sloppy but I'll improve/edit this post as time goes along. I'm busy ATM but I decided to get an early start on this* :)

AFAIK there are two actual bugs in ubiquity and casper:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

There may be a third bug effecting the installer/live desktop regarding parted not recognizing partitions properly but I'm only basing that on posts I've read at the Installation and Upgrades sub-forum. I've not been able to reproduce it myself so I don't know :confused:

I do however have a "wishlist" for the new ubiquity and this would be a good starting point:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

That should be somewhat self explanatory.

I have two other "wishes":

#1: Add the option to maximize the installer windows again. Particularly if using the manual partitioning option it simply makes things simpler to read. Not sure why they included an option to minimize :confused:

#2: Add the option to NOT install grub again.

Another that I've read two complaints about is the lack of the option to "install to largest free space".

I'm thinking I should at least put something up at Ayatana before UDS on the 28th and I'd truly appreciate some feedback :)

Sorry again for the sloppy post but I'd truly appreciate any and all feedback, even if you totally disagree with me.

---

### Post by cariboo on 2010-10-13
I added myself to your first bug, as I noticed it the other day when preparing a partition for natty.

---

### Post by ranch hand on 2010-10-13
Without the resizable window it is real tough to use the installer partitioner if you have 11 partitions on one drive and 7 on the other.

I am lucky on my test drive as only one of the two drives is bootable.  I can install grub to /dev/sdb.  No problem.

There is no chance what so ever that Ubuntu will ever be installed, as the installer is now, on either of my internal drives.

If there is something I can do, besides beating my head on a wall, let me know.

---

### Post by 23meg on 2010-10-13
> **ranch hand said:**
> 
If there is something I can do, besides beating my head on a wall, let me know.

Alternate CD.

---

### Post by k3lt01 on 2010-10-15
> **mgunes said:**
> Alternate CD.It would be nice to be able to use the LiveCD even on low power machines. I haven't used a LiveCD on my laptop since Gutsy. For some of the machines I refurbish I like to show the recipients how easy it can be to install Ubuntu, unfortunately that is just not possible with an AlternateCD.

And yes I realise the bugs listed don't deal with this but it is a realistic request.

---

### Post by ronacc on 2010-10-15
all of the dialog boxes/windows need to be FULLY resize-able , on a net book you can't see the accept/cancel , etc buttons because theyu are off the bottom of the screen and the box can't be dragged up above the top of the window or resized small enough to fit on the window , you have to blindly use <tab> and <return> and hope you guessed correctly which selection is in what position.

edit : madded myself to all of your bugs , the general flakyness of Ubiquity is one of Ubuntu's greatest embarrassments .

---

### Post by kansasnoob on 2010-10-15
> **ronacc said:**
> all of the dialog boxes/windows need to be FULLY resize-able , **[COLOR="Red"]on a net book you can't see the accept/cancel , etc buttons because theyu are off the bottom of the screen and the box can't be dragged up above the top of the window or resized small enough to fit on the window , you have to blindly use <tab> and <return> and hope you guessed correctly which selection is in what position.[/COLOR]**

edit : madded myself to all of your bugs , the general flakyness of Ubiquity is one of Ubuntu's greatest embarrassments .

That's exactly the kind of info I need when I write this. I've found that whatever I throw out at Ayatana is quite dependent on the way I originally present it :)

I'm thinking I better take time this weekend to put something together. I fear I'm really going to mess up because I've been insanely busy.

---

### Post by kansasnoob on 2010-10-15
> **k3lt01 said:**
> It would be nice to be able to use the LiveCD even on low power machines. I haven't used a LiveCD on my laptop since Gutsy. For some of the machines I refurbish I like to show the recipients how easy it can be to install Ubuntu, unfortunately that is just not possible with an AlternateCD.

And yes I realise the bugs listed don't deal with this but it is a realistic request.

That's beyond what I'm trying to achieve here.

Oddly I have a very old PII w/256MB of RAM that will run Ubuntu. It's slow as molasses but it runs. And it runs a bit better if I create a SWAP using something like Puppy LuPu first.

Lucid Puppy made me smile more than anything in a very long time :)

---

### Post by kansasnoob on 2010-10-15
> **ranch hand said:**
> Without the resizable window it is real tough to use the installer partitioner if you have 11 partitions on one drive and 7 on the other.

I am lucky on my test drive as only one of the two drives is bootable.  I can install grub to /dev/sdb.  No problem.

There is no chance what so ever that Ubuntu will ever be installed, as the installer is now, on either of my internal drives.

If there is something I can do, besides beating my head on a wall, let me know.

I don't find it unusable, it's simply less friendly to the eyes. I also use two drives to test:

```
lance@lance-desktop:~$ sudo blkid
[sudo] password for lance: 
/dev/sda1: LABEL="Maverick" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="Karmic" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Lucid" UUID="d252929b-949d-432e-a18c-18f9ae770d28" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" TYPE="ext3" 
/dev/sda9: UUID="80627269-1ccd-4774-b4ea-a5ef8824ffaa" TYPE="swap" 
/dev/sda10: LABEL="Isadora" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Squeeze" UUID="0eec2831-7805-437e-a06e-e18ab3268e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="Pure Gnome" UUID="f6062e12-09f1-4f19-b6c2-ad58812d6794" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Peppermint" UUID="720d719e-e571-4bdd-aac9-718f0ffe2266" TYPE="ext4" 
/dev/sda14: LABEL="LL to MM final" UUID="8ecdcd5d-6fc8-4e81-aed9-fa20f3b7b079" TYPE="ext4" 
/dev/sda15: LABEL="LMDE" UUID="22eefad4-870e-4191-87c9-57f4e756411d" TYPE="ext4" 
/dev/sda16: LABEL="LL to MM RC" UUID="7a90aa0c-2377-48e4-97ad-20283c962abc" TYPE="ext4" 
/dev/sda17: LABEL="Maverick test" UUID="fad5d0d5-79d1-405c-9e9c-1dd714d39b8b" TYPE="ext4" 
/dev/sdb1: UUID="9222d787-5297-42a2-98fc-eb1b6f5813e9" TYPE="ext4" 
/dev/sdb2: UUID="0ef3f012-83c8-43d6-ab63-b7d700e2d900" TYPE="ext4" 
/dev/sdb3: UUID="ee3de357-beea-4bfb-a939-fb79632350b6" TYPE="ext4" 
/dev/sdb5: UUID="21cbb26a-53d1-4764-8e17-3d8f3132af82" TYPE="ext4" 
/dev/sdb6: UUID="3c2402bb-c36a-45d9-a548-6ec87cbf5441" TYPE="swap" 
/dev/sdb7: UUID="34ebe2de-758c-4e75-8c81-4bc47ac6b678" TYPE="ext4" 
/dev/sdb8: UUID="64c38ae5-706c-4e98-ba7d-13bd9203b34d" TYPE="swap" 

```

I last used sdb to test this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

So I don't find the new ubiquity unuasable, I'm actually quite impressed at how quickly the devs pulled it all together.

I just want to present some suggestions for improvements in a coherent manner. Ha-ha I need to be coherent :)

---

### Post by kansasnoob on 2010-10-15
Come to think of it I did address the window resizing problem at Launchpad long ago:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

No dev activity at all after I filed that :(

To my thinking I need to find a great way to repeat what Ivanka Majic said here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31)

> The Ubuntu Live CD is the first experience many new users will have of Ubuntu. The installation experience should be attractive and effortless to reassure new users that Ubuntu is the right choice. The process should feel safe and should only highlight risk when necessary (e.g. when data will be destroyed).

Well, did the new ubiquity achieve that goal?

I'd say, "no", but it's going to take more than my say-so to get any changes implimented.

I'll put something together ASAP and post it to Ayatana, then I'll post back here.

If no one supports any of my suggestions they'll likely not be implemented :(

---

### Post by psusi on 2010-10-15
The option to not install grub is there.  In fact, it's now on one of the first screens instead of at the end.

---

### Post by ranch hand on 2010-10-15
Hmm, I did not see it the last time I installed.  Would have been the release ISO RC.

I will look for it on the 11.04A1 ISO RC when that comes around.

---

### Post by kansasnoob on 2010-10-15
> **psusi said:**
> The option to not install grub is there.  In fact, it's now on one of the first screens instead of at the end.

I guess it's time for me to take another look, I sure haven't seen it.

---

### Post by psusi on 2010-10-15
I think it was on the first or second screen.  There's a drop down box at the bottom for where to install grub to, and iirc, NOWHERE was one of the choices.  It just isn't a check box to install or not like it used to be.

---

### Post by kansasnoob on 2010-10-16
I double, triple, quadruple checked and I see no option to NOT install grub:

[ATTACH]172506[/ATTACH]

If I'm wrong then show me.

This is very serious to me.

---

### Post by kansasnoob on 2010-10-16
My very, very early, unpolished (aka: sloppy) draft for Ayatana:

> While ubiquity is not a listed project with Ayatana I really wanted to get some suggestions into the works before UDS, apologies in advance if I did this totally wrong. We live and we learn.

I want to begin by saying that I’m quite impressed with how quickly the devs “pulled together” the new ubiquity during the Maverick dev cycle. I’m fully aware that nothing can just “stand still” so it was time for a change. Unfortunately change always includes challenges and I’d like to address a few of those.

I’d also like to say that I can’t possibly improve on Ivanka Majik’s words here:

 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31)

“&#65279;The Ubuntu Live CD is the first experience many new users will have of Ubuntu. The installation experience should be attractive and effortless to reassure new users that Ubuntu is the right choice. The process should feel safe and should only highlight risk when necessary (e.g. when data will be destroyed).”

AFAIK there are only two valid bugs in the new ubiquity/casper (both of which I filed):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/657086)

And I’m sure those can be dealt with throughout the Natty dev cycle, however there are other “design” issues.

Issue #1 I described here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Honestly think of yourself as a Windows user with no past Linux experience. You choose “side-by-side” and then see the options “Use entire disc” and “Use entire partition”. Huh? What disc? What partition?

Most Win users are used to Drive A, Drive C, etc. They don’t know the difference between “entire disc” and “entire partition”, and they already chose “alongside” so they are NOT going to think they could mess up and wipe Win and their data at that point.

How would you know that if you want to continue with “side-by-side” you’re supposed to ignore those and “drag” the “slider” to adjust partition size? Or even just continue with the pre-selected sizes?

Six options! Use entire disc, use entire partition, advanced tool, quit, back, or install now. Huh? I already chose “side-by-side" so I should be able to click anything, eh?

SIX OPTIONS! Huh? I think that’s confusing. We always need to wear our “noob shoes” when it comes to the installer. Ask yourself if your grandmother could understand it ;^)

Issue #2:

For some reason the installer windows can now be minimized but not maximized or “resized” by “dragging”. While I find that only annoying others find it nearly impossible to deal with:

[http://ubuntuforums.org/showpost.php?p=9976163&postcount=6](http://ubuntuforums.org/showpost.php?p=9976163&postcount=6)

[http://ubuntuforums.org/showpost.php?p=9968363&postcount=3](http://ubuntuforums.org/showpost.php?p=9968363&postcount=3)

I actually did file a bug report regarding that early after the new ubiquity was released:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

As described in the first of those links it can create real havoc for netbook users:

“&#65279;on a net book you can't see the accept/cancel , etc buttons because theyu are off the bottom of the screen and the box can't be dragged up above the top of the window or resized small enough to fit on the window , you have to blindly use <tab> and <return> and hope you guessed correctly which selection is in what position.”

Issue #3:

I’ve twice seen folks on the forums lament the absence of “Install to largest free space” as an option. I’ve seldom used that option but I felt it worth mentioning.

Issue #4:

There is no option to NOT install grub. I’m not concerned with that because it should be acceptable to just install grub to either the root partition or “/boot” if one exists, even if you don’t plan on chain-loading.

Ultimately I’d like to see this tossed around a bit. How well are we living up to what Ivanka stated as a goal?


---

### Post by cariboo on 2010-10-16
I'm still going to argue against your point #4

For a new user that has just installed a system, a choice to not install grub is a bad decision, there have been quite a few threads in the forums where new users chose not to install grub with the previous installer, and ended up with a system that would only boot to the operating system that was already installed before they installed Ubuntu.

The only people that really think they need an option not to install grub, are advanced users, and we know enough to work around the problem. Having multi-distributions on one computer is not a typical use case

---

### Post by ranch hand on 2010-10-16
Sounds pretty good to me.

Not longer than it needs to be either.  That is always a good thing.

---

### Post by kansasnoob on 2010-10-16
> **cariboo907 said:**
> I'm still going to argue against your point #4

For a new user that has just installed a system, a choice to not install grub is a bad decision, there have been quite a few threads in the forums where new users chose not to install grub with the previous installer, and ended up with a system that would only boot to the operating system that was already installed before they installed Ubuntu.

The only people that really think they need an option not to install grub, are advanced users, and we know enough to work around the problem. Having multi-distributions on one computer is not a typical use case

I'm actually cool with that. I know that if I don't want to install grub to the mbr I can safely install the new OS's grub to its root partition (or /boot if one was created).

This makes me wonder if I should drop that request altogether :confused:

I mean if anything I'm asking about detracts or distracts from the more serious stuff then we lose, eh?

Everyone's opinion matters to me :)

In fact I wish someone else would just take the lead on this. I'm tired, I'm legally blind, I have a bum leg, I broke the arm I should be holding my cane with, my goats are brats, and my dogs are even bigger brats.

And my kids are trying to stuff me in one of those "retirement housing" places. That'll be the day :)

I can still wield a 3# hammer pretty well with my left hand, and I'm right handed.

---

### Post by ranch hand on 2010-10-16
The hammer should come in handy with the kids.  Use it until they find an "elder prison" that takes goats and dogs.

---

### Post by ronacc on 2010-10-16
> **cariboo907 said:**
> I'm still going to argue against your point #4

For a new user that has just installed a system, a choice to not install grub is a bad decision, there have been quite a few threads in the forums where new users chose not to install grub with the previous installer, and ended up with a system that would only boot to the operating system that was already installed before they installed Ubuntu.

The only people that really think they need an option not to install grub, are advanced users, and we know enough to work around the problem. Having multi-distributions on one computer is not a typical use case

by default anyone installing Ubuntu ( or any other distro or OS ) "alongside" windows ( or OSX don't forget MAC users ) is going to have multi ( more than one ) OS's installed .

Perhaps with the new ubuquity it is time to have the process fork right at the beginning with an "express/advanced" option . IIRC ( and its been more than 10 years so I could be wrong ) windows does it this way . That way we can accommodate both newbes and  more experienced users with special wants/needs .

---

### Post by cariboo on 2010-10-16
What I meant meant when I said multi, was more then just Windows and Ubuntu. I'm sure if we ran a poll, we would find the average user has only the two.

---

### Post by ranch hand on 2010-10-16
People still use Windows?  Goodness me, thought they would have gotten over that by now.

---

### Post by seeker5528 on 2010-10-16
> **cariboo907 said:**
> The only people that really think they need an option not to install grub, are advanced users, and we know enough to work around the problem. Having multi-distributions on one computer is not a typical use case

Just because I *can* backup and restore my MBR every time I do a new install, doesn't mean I want to be *required* to back it up and restore it.

Instead of removing the option, it would be better to assume that people can read and include some text indicating that if you don't understand what the option is for you shouldn't check the box.

Later, Seeker

---

### Post by arpanaut on 2010-10-16
@ K_noob 
You seen this thread?

[http://ubuntuforums.org/showthread.php?t=1598243](http://ubuntuforums.org/showthread.php?t=1598243)

Looks like a serious problem with ubiquity,  re: your #1 issue in that beyond confusion, It doesn't work as advertised. 
Not that you need further aggravation but, food for thought.

---

### Post by psusi on 2010-10-16
> **arpanaut said:**
> @ K_noob 
You seen this thread?

[http://ubuntuforums.org/showthread.php?t=1598243](http://ubuntuforums.org/showthread.php?t=1598243)

Looks like a serious problem with ubiquity,  re: your #1 issue in that beyond confusion, It doesn't work as advertised. 
Not that you need further aggravation but, food for thought.

That thread seems to be about a confused user who told the installer to use the entire disk when he didn't mean to, which has nothing to do with #1.

---

### Post by plun on 2010-10-16
> **cariboo907 said:**
> What I meant meant when I said multi, was more then just Windows and Ubuntu. I'm sure if we ran a poll, we would find the average user has only the two.
  
I understand it....

The challenge seems to be that a normal Windows 7 install**(OEM pc)** takes 3 partitions...#-o , 2 partitions for restore and one normal.

If a user then install Ubuntu there is no room for a normal install and everything is a mess with extended partitions.

I don't know if **Mr Colin Watson** test this with a sharp Windows installed... but maybe its high time for him to test this !!!

Just a shame with all broken Dual-boots.... IMHO.

---

### Post by psusi on 2010-10-16
> **plun said:**
> I understand it....

The challenge seems to be that a normal Windows 7 install**(OEM pc)** takes 3 partitions...#-o , 2 partitions for restore and one normal.

If a user then install Ubuntu there is no room for a normal install and everything is a mess with extended partitions.

I don't know if **Mr Colin Watson** test this with a sharp Windows installed... but maybe its high time for him to test this !!!

Just a shame with all broken Dual-boots.... IMHO.

What?

---

### Post by arpanaut on 2010-10-16
> That thread seems to be about a confused user who told the installer to  use the entire disk when he didn't mean to, which has nothing to do with  #1.

I see what you are saying, but once the side by side is chosen and then entire partition is chosen then why did he end up with the entire disk partitioned for Ubuntu?

I do see some confusing aspects with the installer if this is happening.  I have used the Live_CD to install lately and some of the options confuse me and I have been installing Ubuntu for many years.  This is exactly why I prefer the "Advanced" option or use the Alt-CD most of the time.  What is obvious to ubiquity is not always so obvious to me.

disclaimer<I am getting older, so confusion is not an unusual stae of mind for ME!>:biggrin:

---

### Post by plun on 2010-10-16
> **psusi said:**
> What?

Grub mess !!.....  but maybe we shall totally ruin Ubuntus reputation...:tongue:

It brakes your computer....:---)

---

### Post by cariboo on 2010-10-16
> **plun said:**
> I understand it....

The challenge seems to be that a normal Windows 7 install**(OEM pc)** takes 3 partitions...#-o , 2 partitions for restore and one normal.

If a user then install Ubuntu there is no room for a normal install and everything is a mess with extended partitions.

I don't know if **Mr Colin Watson** test this with a sharp Windows installed... but maybe its high time for him to test this !!!

Just a shame with all broken Dual-boots.... IMHO.

I have a multi-boot system with white-box OEM win 7, Maverick and Natty, as far as I can tell grub2 ignores the the 100MB partition the Win 7 installer creates. Admittedly I manually partition the drives, but once the partitioning is done I don't even look at the grub install options, except out of curiosity, and just let the install continue, but that's just me.

The big problem/advantage is that no two installs are alike, I think that the aim of the installer is, to create an average that everyone can use. 

So far it looks more like the automatic partitioner is more of a problem than where grub gets installed.

---

### Post by psusi on 2010-10-16
> **arpanaut said:**
> I see what you are saying, but once the side by side is chosen and then entire partition is chosen then why did he end up with the entire disk partitioned for Ubuntu?


Because he chose the option to use the entire partition rather than split it in two.  Admittedly this option does not seem to make much sense once you have already chosen to do a side by side install, but it has nothing to do with issue #1 in this thread.

> **plun said:**
> Grub mess !!.....  but maybe we shall totally ruin Ubuntus reputation...:tongue:

It brakes your computer....:---)

I sense a language barrier.  Perhaps you can find some help conveying your thoughts in english?

---

### Post by ronacc on 2010-10-16
I don't have any difficulty understanding Plun , and his spelling is no worse than some native english speakers .

---

### Post by k3lt01 on 2010-10-16
> **ronacc said:**
> and his spelling is no worse than some native english speakers .My keyboard is broken :P

---

### Post by psusi on 2010-10-16
> **ronacc said:**
> I don't have any difficulty understanding Plun , and his spelling is no worse than some native english speakers .

Perhaps you can translate then?

---

### Post by arpanaut on 2010-10-16
> Because he chose the option to use the entire partition rather than  split it in two.  Admittedly this option does not seem to make much  sense once you have already chosen to do a side by side install, but it  has nothing to do with issue #1 in this thread.I see the errors he made, but look at Pic #1 of his original partitioning, he had other partitions on the drive that ubiquity should never have touched after choosing "entire Part." Somehow it reverted to" entire drive"  It should have reverted to installing to sda2 and nowhere else. Or revert to the original screen asking what the user really wants to do.

If this is not an example of the confusing nature of the operation of the installer I don't know what is?
Okay maybe not exactly what K-noob is addressing but very close relative to mistakes being made because of the way installation is presented.
[http://ubuntuforums.org/showpost.php?p=9980160&postcount=16](http://ubuntuforums.org/showpost.php?p=9980160&postcount=16)

I'm not trying to have an argument here, just trying to help the OP  get more ammo to bring change to the installer which does work very well but does have some issues that can be improved upon. Maybe I'm way off base?

Heck, maybe I have some problems with the English language too? :smile:

---

### Post by ronacc on 2010-10-16
> **psusi said:**
> Perhaps you can translate then?

in this instance I will do as you request .

what Plun said is that since an OEM install of Windows 7 uses up 3 of the 4 regular partitions that are recognised by the file system ,that a "normal" install of ubuntu ( / + /home + swap ) won't work and that the 4th partition needs to be an extended partition to allow the extra partitions to be created .


As to the translation , this is an international forum and MANY here are not native english speakers ( either American or British variety ), so you should really make an effort to be more understanding .

---

### Post by psusi on 2010-10-16
> **arpanaut said:**
> I see the errors he made, but look at Pic #1 of his original partitioning, he had other partitions on the drive that ubiquity should never have touched after choosing "entire Part." Somehow it reverted to" entire drive"  It should have reverted to installing to sda2 and nowhere else.

You say you see the errors he made, but then the rest of that statement indicates you do not.  The error was choosing to use the entire partition, which is what it did.  It used the entire partition ( that previously held windows ) to install ubuntu to.  It couldn't install to sda2 because there WAS no sda2.

> **arpanaut said:**
> If this is not an example of the confusing nature of the operation of the installer I don't know what is?

Yes, it's confusing and probably should be changed.

> **ronacc said:**
> in this instance I will do as you request .

what Plun said is that since an OEM install of Windows 7 uses up 3 of the 4 regular partitions that are recognised by the file system ,that a "normal" install of ubuntu ( / + /home + swap ) won't work and that the 4th partition needs to be an extended partition to allow the extra partitions to be created .

Yes, you can only have 4 primary partitions, but he seemed to be complaining about Ubuntu and specifically grub in some way I could not understand.

> **ronacc said:**
> As to the translation , this is an international forum and MANY here are not native english speakers ( either American or British variety ), so you should really make an effort to be more understanding .

I do try, but in this case I am still at a loss.

---

### Post by ronacc on 2010-10-16
> **psusi said:**
> 
Yes, you can only have 4 primary partitions, but he seemed to be complaining about Ubuntu and specifically grub in some way I could not understand.

I don't believe ubiquity will create extended partitions and even when they are created before hand with gparted , I have on occasion had a problem with grub finding them .

---

### Post by cariboo on 2010-10-16
Ubiquity will create extended partitions, even using manual partition, you specifiacally have to tell it to use a primary partition.

On that last natty install I did, I wanted to try btrfs, so I created a 10Gb /,   250Mb /boot, 2Gb swap , and the rest of the disk for /home. I wasn't paying attention and /boot ended up on an extended partition.

---

### Post by ronacc on 2010-10-16
I will give it a try when I do a fresh install at A1 . i'm going to wipe my test box and start from scratch so it can't hurt anything .

---

### Post by ubername on 2010-10-17
Kansasnoob's point:

> Issue #1 I described here:

[https://bugs.launchpad.net/ubuntu/+s...ty/+bug/655950](https://bugs.launchpad.net/ubuntu/+s...ty/+bug/655950)

Honestly think of yourself as a Windows user with no past Linux experience. You choose “side-by-side” and then see the options “Use entire disc” and “Use entire partition”. Huh? What disc? What partition?

Most Win users are used to Drive A, Drive C, etc. They don’t know the difference between “entire disc” and “entire partition”, and they already chose “alongside” so they are NOT going to think they could mess up and wipe Win and their data at that point.

How would you know that if you want to continue with “side-by-side” you’re supposed to ignore those and “drag” the “slider” to adjust partition size? Or even just continue with the pre-selected sizes?


I am disappointed that the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950) has been set to 'Won't fix' for the following reason: 

> Regarding your original concern of the presence of "use entire disk" and "use entire partition" buttons, I fail to see how they do any harm. Their presence is part convenience, and part desire to consolidate the automatic partitioning options to a single page. The fact that the first partitioning page offers you separate "use entire disk" and "resize partition" options is arguably a bug, but I am otherwise satisfied with the UI.

This does not seem to address the issues in the original bug report that 
a) user has already selected 'side-by-side' so might be justified in thinking they can 'skip this bit' by selecting anything (Oooh Noo! I hear you cry, but it happens)
b) Lots of Windows users  are unfamiliar with the Disk / Partition concepts and may think of partitions as disks, so could easily make the wrong selection ([SIZE="1"]*What, me, a couple of years ago? No never! <whistles unconvincingly>*[/SIZE]).

Does anyone know what the actual impact of selecting 'side-by-side' is? If the intention is to keep the partitioning options to a single page it might be better to not have this 'side-by-side option at all, to avoid confusion after having selected it (I think this is solving the problem the wrong way, but if it fits with the concept for the UI then maybe it's the lesser of two evils.)

---

### Post by kansasnoob on 2010-10-17
> **arpanaut said:**
> @ K_noob 
You seen this thread?

[http://ubuntuforums.org/showthread.php?t=1598243](http://ubuntuforums.org/showthread.php?t=1598243)

Looks like a serious problem with ubiquity,  re: your #1 issue in that beyond confusion, It doesn't work as advertised. 
Not that you need further aggravation but, food for thought.

Thanks for that. That's an excellent example of the "confusion" I'm trying to explain.

Personally however, if I'm planning to use pre-existing partitions, I'd use manual partitioning anyway.

Thanks again.

---

### Post by kansasnoob on 2010-10-17
> **plun said:**
> I understand it....

The challenge seems to be that a normal Windows 7 install**(OEM pc)** takes 3 partitions...#-o , 2 partitions for restore and one normal.

If a user then install Ubuntu there is no room for a normal install and everything is a mess with extended partitions.

I don't know if **Mr Colin Watson** test this with a sharp Windows installed... but maybe its high time for him to test this !!!

Just a shame with all broken Dual-boots.... IMHO.

It is quite common to see "branded" Win7 PC's with 3 primary partitions, one very small w/part of the boot files, a second large "main" primary, and yet a third small primary w/recovery and/or system utilities.

Quite honestly, if I had my druthers, I'd just as soon see the installer refuse to proceed if either Vista or Win7 are recognized with a recommendation to use Vista/Win7's own partitioning tools, then using the ***now non-existent*** "use largest free space" option.

I suppose a lot of this does get confusing no matter what, which really leads us to the greatest challenge: educating people a bit ahead of time about repartitioning, etc. Sadly it's been my experience that people just d/l a disc, toss it in, and let her rip :(

---

### Post by ronacc on 2010-10-17
not to mention that windows puts its swap file at the very end of the drive creating a bad situation since gparted doesn't like to create partitions inside of another partition (except for an extended partition ) , thereby requiring them to know to boot windows ,turn off their swap file and defrag before installing .

---

### Post by kansasnoob on 2010-10-17
> **arpanaut said:**
> I see what you are saying, but once the side by side is chosen and then entire partition is chosen then why did he end up with the entire disk partitioned for Ubuntu?

I do see some confusing aspects with the installer if this is happening.  I have used the Live_CD to install lately and some of the options confuse me and I have been installing Ubuntu for many years.  This is exactly why I prefer the "Advanced" option or use the Alt-CD most of the time.  What is obvious to ubiquity is not always so obvious to me.

disclaimer<I am getting older, so confusion is not an unusual stae of mind for ME!>:biggrin:

This is exactly what I'm trying to explain here:

> Honestly think of yourself as a Windows user with no past Linux experience. You choose “side-by-side” and then see the options “Use entire disc” and “Use entire partition”. Huh? What disc? What partition?

Most Win users are used to Drive A, Drive C, etc. They don’t know the difference between “entire disc” and “entire partition”, and they already chose “alongside” so they are NOT going to think they could mess up and wipe Win and their data at that point.

How would you know that if you want to continue with “side-by-side” you’re supposed to ignore those and “drag” the “slider” to adjust partition size? Or even just continue with the pre-selected sizes?

Six options! Use entire disc, use entire partition, advanced tool, quit, back, or install now. Huh? I already chose “side-by-side" so I should be able to click anything, eh?

SIX OPTIONS! Huh? I think that’s confusing. We always need to wear our “noob shoes” when it comes to the installer. Ask yourself if your grandmother could understand it ;^)

As I think about, after selecting "install alongside" how many options are displayed really? And how clear are those options to the average user?

[ATTACH]172639[/ATTACH]

Note: I realize the available options depend on hardware, existing partitions, etc.

#1: Select drive. IMO that's a must have and I think it should be self explanatory.

#2: Allocate by dragging. Again a must have and I think self explanatory.

#3: List of hidden partitions and offer to use advanced tool. Again I think this is a good thing.

#4 and #5: Use entire disc and/or partition. This is IMHO very confusing. I've already chosen to "install alongside" so what am I being asked? I think this needs the most attention :)

#6, #7, and #8: Quit, Back and Install Now. Again very much self explanatory.

It's #'s 4 and 5 that I think could really throw a person. I've chosen to "install alongside" now what should I click on next :confused:

---

### Post by kansasnoob on 2010-10-17
> **ronacc said:**
> not to mention that windows puts its swap file at the very end of the drive creating a bad situation since gparted doesn't like to create partitions inside of another partition (except for an extended partition ) , thereby requiring them to know to boot windows ,turn off their swap file and defrag before installing .

That, and the possibility (however slight) that parted might move the "beginning" of the Win OS partition mangling boot files, is why I personally always recommend resizing Vista and Win7 with their own tools.

If I resize using Wins own tools, then reboot to be sure Win still boots, and then install Ubuntu to the newly existing free space I should, theoretically, be safe, eh?

---

### Post by kansasnoob on 2010-10-17
> **cariboo907 said:**
> I have a multi-boot system with white-box OEM win 7, Maverick and Natty, as far as I can tell grub2 ignores the the 100MB partition the Win 7 installer creates. Admittedly I manually partition the drives, but once the partitioning is done I don't even look at the grub install options, except out of curiosity, and just let the install continue, but that's just me.

The big problem/advantage is that no two installs are alike, I think that the aim of the installer is, to create an average that everyone can use. 

**[COLOR="Red"]So far it looks more like the automatic partitioner is more of a problem than where grub gets installed.[/COLOR]**

I agree. If I try to address too many issues at once it could effect the overall focus and detract from the most serious issue(s).

That's exactly why I prefer discussing things here before jumping directly to Ayatana or Launchpad :)

And, as I said previously, it should always be safe to install grub2 to the newly created "/" (or "/boot" if one is being created) if someone wants to leave the mbr alone. This would also be the best way to ensure that Easy-BCD works with the new install if someone prefers using Easy-BCD.

I can't comment on Mac because I've never messed with it.

---

### Post by kansasnoob on 2010-10-17
> **arpanaut said:**
> I see the errors he made, but look at Pic #1 of his original partitioning, he had other partitions on the drive that ubiquity should never have touched after choosing "entire Part." Somehow it reverted to" entire drive"  It should have reverted to installing to sda2 and nowhere else. Or revert to the original screen asking what the user really wants to do.

If this is not an example of the confusing nature of the operation of the installer I don't know what is?
**[COLOR="Red"]Okay maybe not exactly what K-noob is addressing[/COLOR]** but very close relative to mistakes being made because of the way installation is presented.
[http://ubuntuforums.org/showpost.php?p=9980160&postcount=16](http://ubuntuforums.org/showpost.php?p=9980160&postcount=16)

I'm not trying to have an argument here, just trying to help the OP  get more ammo to bring change to the installer which does work very well but does have some issues that can be improved upon. Maybe I'm way off base?

Heck, maybe I have some problems with the English language too? :smile:

Actually very much my number one concern:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

You'll see that earned a "Won't fix" w/this explanation from Evan Dandrea:

> Regarding your original concern of the presence of "use entire disk" and "use entire partition" buttons, I fail to see how they do any harm. Their presence is part convenience, and part desire to consolidate the automatic partitioning options to a single page. The fact that the first partitioning page offers you separate "use entire disk" and "resize partition" options is arguably a bug, but I am otherwise satisfied with the UI.

IMHO it's a killer combined with this "actual" bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

I'd add that I have the utmost respect for Evan. I've seen him fix last minute bugs many times while I was iso-testing. We simply disagree on this issue :)

Therefore I, **or someone**, must address this in a way that's effective.

---

### Post by kansasnoob on 2010-10-17
ATM, looking back at this:

[http://ubuntuforums.org/showpost.php?p=9980160&postcount=16](http://ubuntuforums.org/showpost.php?p=9980160&postcount=16)

I think I'll drop issue #4 altogether for the moment.

I think issue #3 needs to be artfully combined with issue #1.

Issue #2 does need to be addressed but should it be included in this Ayatana request? I'm thinking NO :confused:

As I'd mentioned I had previously filed a bug report about that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

So maybe we could address that separately, maybe even at that bug report? If it's not improved by Natty Alpha1 iso-testing I can even report it then. Usually the "QA" tag results in some action, if that results in a "won't fix" or "invalid" or something indicating that it's a design change we can tackle it then, eh?

I need to get some sunshine, get my blood circulating, and try to let my brain digest this.

Many thanks to everyone for commenting :)

I do wish psusi would show me where he sees the option to "not install" grub though. I even posted a screenshot in post #15 and I may be overlooking something.

I'm not stone blind but I am legally blind and sometimes I overlook the obvious. Also sometimes my "personalized" use of fonts "pushes" things "off-screen" :)

---

### Post by kansasnoob on 2010-10-17
I see a bit more activity here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950?comments=all)

I'd be very, very happy if I didn't have to go to Ayatana with this :)

It's not on the Ayatana list and I always feel like the fracking hall monitor in high school when I have to take that route :(

Maybe QA could take the reigns and steer this sled. That would be awesome.

---

### Post by psusi on 2010-10-17
> **kansasnoob said:**
> 
I do wish psusi would show me where he sees the option to "not install" grub though. I even posted a screenshot in post #15 and I may be overlooking something.


I could have sworn that nowhere was one of the many options for the destination, but apparently I was wrong.

---

### Post by ronacc on 2010-10-17
the choice of where ( or not ) to install grub is on the summary screen under the "advanced" tab ( at least it used to be ) thats the next screen after your screenshot .

---

### Post by cariboo on 2010-10-18
You have to choose the manual partitioning option in order to have the choice of where to install grub with the new version of the installer.

---

### Post by ronacc on 2010-10-18
> **cariboo907 said:**
> You have to choose the manual partitioning option in order to have the choice of where to install grub with the new version of the installer.

Thanks for the clarification , due to the complex and admittedly convoluted setup on my test box I never tried anything other than manual partitioning .

---

### Post by kansasnoob on 2010-10-18
> **ronacc said:**
> the choice of where ( or not ) to install grub is on the summary screen under the "advanced" tab ( at least it used to be ) thats the next screen after your screenshot .

Yes, I posted a screenshot of that here:

[http://ubuntuforums.org/showpost.php?p=9980140&postcount=15](http://ubuntuforums.org/showpost.php?p=9980140&postcount=15)

I just don't see an option to NOT install grub, but I've decided not to worry about that right now.

I think I'll do basically what I said here for now:

[http://ubuntuforums.org/showpost.php?p=9987018&postcount=50](http://ubuntuforums.org/showpost.php?p=9987018&postcount=50)

I'll try and get it put together today.

I appreciate all of the feedback, it really helps me decide what's related, what's not related, and what I should focus on the most.

I hope to spur some thought prior to UDS.

---

### Post by kansasnoob on 2010-10-18
I'm getting a little bit cooked (it happens with age) but this is where I'm at right now:

> *Does the new ubiquity offer confusing options during “side-by-side” installs?*

While ubiquity is not a listed project with Ayatana I really hope to open up some meaningful discussion regarding what I see as a major shortfall in the new ubiquity prior to Natty UDS. However, I’d first like to say that I’m largely impressed with the overall appearance of the new ubiquity and just how quickly the devs pulled this all together during the Maverick dev cycle.

My goal is to offer constructive criticism from an end users perspective without ever being disagreeable. I’m very much reminded of what Ivanka Majik said during the dispute regarding the ability to change the computer name during installation:

“&#65279;The Ubuntu Live CD is the first experience many new users will have of Ubuntu. The installation experience should be attractive and effortless to reassure new users that Ubuntu is the right choice. The process should feel safe and should only highlight risk when necessary (e.g. when data will be destroyed).”

I simply question whether or not we’re living up to that goal if a new user selects “Install alongside other operating systems”. The screen following that choice displays a number of options including “Use entire partition” and “Use entire disc”. I believe the other options are quite clear, but at this point I want everyone to put their “noob shoes” on ;^)

What partition and/or disc is the installer referring to? Also consider that most Windows users are used to designations like Drive A, Drive C, etc. Who are we targeting with the “alongside” option?

The user has just chosen between three options:

1: Install alongside other operating systems
2: Erase and use entire disc
3: Specify partitions manually (advanced)

Having already chosen “Install alongside other operating systems” why are they now being asked if they want to “Use entire partition” or “Use entire disc”? Didn’t they already make that decision?

They already decided not to “Erase and use entire disc” but they’re being asked again. Is that confusing? I think it is.

If they choose “Use entire partition” what partition are they agreeing to use? Remember who we’re targeting with the “side-by-side” option :^) As previously mentioned many Windows users, and sadly some long time Ubuntu users, have no idea what device designations are.

Possibly exacerbating the problem, even for more experienced users, is this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

I simply identified that too late in the Maverick dev cycle to expect a fix and I’ll follow up on that during Natty iso-testing.

I had however filed a bug report regarding this “auto-resize confusion”:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

While I got seriously “off-track” there you’ll see that Evan Dandrea said:

“&#65279;Regarding your original concern of the presence of "use entire disk" and "use entire partition" buttons, I fail to see how they do any harm. Their presence is part convenience, and part desire to consolidate the automatic partitioning options to a single page. The fact that the first partitioning page offers you separate "use entire disk" and "resize partition" options is arguably a bug, but I am otherwise satisfied with the UI.”

I obviously disagree but I’d like to point out that I have great respect for Evan. During the time I’ve been iso-testing I’ve seen him fix a lot of last minute bugs. I know he poured a lot of effort into the new ubiquity and I’d hope that everyone agrees that we can disagree without being disagreeable :^)



Am I close?

---

### Post by arpanaut on 2010-10-18
> Am I close?

YES, Very Diplomatic!

One will catch more flies with honey than vinegar.

If Ayatana does not pick this up, maybe they will point you to the correct venue.

Good Work, and Thanks for the effort!

---

### Post by ubername on 2010-10-18
I think a useful step in developing the report is to find out exactly what is supposed to be the outcome of selecting 'Install alongside other operating systems' (as I mentioned in my previous post). I don't know where / if design doc's are kept or if they are accessible. At the moment I am not at all clear what value it has. 

I do think that once this option has been selected, there should be ***no way at all*** of over-writing any existing operating systems.

FWIW I would like to see something like the following happen once the user has selected to 'Install alongside'

1. Check to see if there is a sufficiently (how big?) large unallocated space on any available disk, if so use it, if not
2. Check to see which partition has the most free space. If it is large enough, use it. Otherwise - 'There is not enough space available to complete the installation safely'

3. In any event, Display to the user something like:

> 
'Windows was detected on the (Nth/only) partition of your (Nth/only) disk. This will (not be affected/ be resized) by this installation.
(Above repeated for each OS found)


NNGb of free space was found (unallocated on/ on the nth partition of) your Nth drive. NGb of this will be used for your new installation of Ubuntu' 

Obviously the above is very mickey mouse and loads more error conditions etc. need to be checked but the basic premise of:

Identify available disk space
Select, based on a set of priorities, some of this space as the target.
Tell the user what is about to happen, including what else has been found and that it will be OK!
Give the option, of course, to  back out / quit

seems a sensible course of action after 'install alongside' has been selected.

---

### Post by ronacc on 2010-10-18
perhaps the NAME of the choice should be changed to " only use free space do not overwrite existing installs" .  Kind of wordy , but no ambiguity .

---

### Post by kansasnoob on 2010-10-19
Well, I done did it:

[https://lists.launchpad.net/ayatana/msg03898.html](https://lists.launchpad.net/ayatana/msg03898.html)

I'm not too happy with the way it's formatted, but it shows up different in my mail.

If my visual acuity weren't so darn poor I'd try to learn some new (and better) tricks, but I do the best I can :)

---

### Post by Mark Phelps on 2010-10-20
Despite the fact that I have been multi-booting Linux distros with MS Windows OSs since Ubuntu 7.04, using this new installer is the first time I felt "nervous" about what it was going to do -- and I know what I'm doing!

What about the poor slob who only wants to try out Ubuntu on their brand spanking new Win7 PC, and 30 minutes later, returns to find out that their entire Win7 stuff got wiped out?

Whatever happened to the philosophy described as "When in doubt, at least, do no harm"?

If there is any risk at all of overwriting an existing partition, the installer MUST put up some kind of dialog box issuing something along the lines of: "WARNING: If you continue, you will  wipe out <partition name>, are you sure you want to do that? (No, Yes)" -- and default to No if nothing is entered.

---

### Post by ranch hand on 2010-10-20
> **Mark Phelps said:**
> Despite the fact that I have been multi-booting Linux distros with MS Windows OSs since Ubuntu 7.04, using this new installer is the first time I felt "nervous" about what it was going to do -- and I know what I'm doing!

What about the poor slob who only wants to try out Ubuntu on their brand spanking new Win7 PC, and 30 minutes later, returns to find out that their entire Win7 stuff got wiped out?

Whatever happened to the philosophy described as "When in doubt, at least, do no harm"?

If there is any risk at all of overwriting an existing partition, the installer MUST put up some kind of dialog box issuing something along the lines of: "WARNING: If you continue, you will  wipe out <partition name>, are you sure you want to do that? (No, Yes)" -- and default to No if nothing is entered.
I agree with you.  I do not use MS, won't have it in the house.  When I first saw the new installer I thought that some one with a similar hostility to MS had designed it.

It is one way to move toward a MS free world (or perhaps an Ubuntu free world if it makes enough folks mad).

---

### Post by k3lt01 on 2010-10-20
> **Mark Phelps said:**
> Whatever happened to the philosophy described as "When in doubt, at least, do no harm"?The Hypocratic Oath.

---

### Post by kansasnoob on 2010-11-11
Still jumping through hoops here :)

Matthew Paul Thomas tells me that I need to join a different team to address this:

[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-installer](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-installer)

So I'll do that ASAP, it may be a few days however.

I can't help but wonder though if things can't be simplified? Does it seem like we just keep adding layer upon layer of complication?

It sort of feels like it to me. Looking back here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

If one of us get's a "won't fix" and disagrees with that how many hoops should we have to jump through?

I know QA watches this sub-forum and I'd think they'd truly be concerned with "end-user experience". I am an end-user with quite a bit of installation experience (but no actual tech knowledge).

I'm thinking it would be great for Launchpad to include a "peer review" type of thing so a person could basically ask for a second opinion. What do you think?

---

### Post by ranch hand on 2010-11-11
I think you are banging your head on the wall.  The layers of complication are to insulate Ubuntu from the unwashed masses.  Works better all the time.

Glad I am writing this from Debian (kernel 2.6.36).  Nice and stable, and boots faster than any of my Ubuntu installs.

They are a lot of fun to play with though.

---

### Post by cariboo on 2010-11-11
Personally I think the installer mailing list may be a better place to get your problems resolved. There is so much noise on the Ayanta mailing list, that it is almost useless.

---

### Post by kansasnoob on 2010-11-14
> **ranch hand said:**
> I think you are banging your head on the wall.  The layers of complication are to insulate Ubuntu from the unwashed masses.  Works better all the time.

Glad I am writing this from Debian (kernel 2.6.36).  Nice and stable, and boots faster than any of my Ubuntu installs.

They are a lot of fun to play with though.

You're too negative.

Looking backwards I've won some battles and lost others. This battle is serious enough to me that I'm not not likely to just give up.

I've just had almost no time to deal with computer issues. Between health problems and weather related property damage I've had no time to play :(

---

### Post by ranch hand on 2010-11-14
Storm damages?  On your newly remodeled home?

You are having way too much FUN to be messing with your computer.

Hope that all gets straightened out and you can relax in boredom.  I have found that boredom, in moderation, is a very good thing.

---

### Post by Quackers on 2010-11-15
I've made my views known in my own subtle way.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

### Post by ronacc on 2010-11-15
I have about given up on raising any questions about design decissions , by the time we find out about them , the deed is done and the chance that they will listen to reason is 0 to any neagative # .

---

### Post by Quackers on 2010-11-15
IIRC Ranch Hand was talking about this issue some time ago.
It just seems silly to me that newcomers to Ubuntu will believe that they are selecting the "safe" option to install alongside, when actually they are choosing how much of their existing installation they want to lose! It's not the welcome I would expect!
It seems to be the way of big business nowadays to insulate the decision makers from the masses by introducing layer after layer of intermediate bod to fend us off. But, as big business is finding out slowly, it is not the way to go.

---

### Post by ronacc on 2010-11-15
its called bureaucracy .

---

### Post by kansasnoob on 2010-11-15
> boredom, in moderation, is a very good thing.

I may use that as a sig :)

Edit: BTW I never got the remodel done. Had to focus on damaged out buildings. I've used so much strongbarn tin this summer I see the crap when I close my eyes to sleep at night.

---

### Post by kansasnoob on 2010-11-15
> **Quackers said:**
> IIRC Ranch Hand was talking about this issue some time ago.
It just seems silly to me that newcomers to Ubuntu will believe that they are selecting the "safe" option to install alongside, when actually they are choosing how much of their existing installation they want to lose! It's not the welcome I would expect!
It seems to be the way of big business nowadays to insulate the decision makers from the masses by introducing layer after layer of intermediate bod to fend us off. But, as big business is finding out slowly, it is not the way to go.

I think the "use entire disc/partition" options just don't belong there! I've installed a lot and that was the most confusing thing I've ever seen :(

---

### Post by kansasnoob on 2010-11-15
> **ronacc said:**
> I have about given up on raising any questions about design decissions , by the time we find out about them , the deed is done and the chance that they will listen to reason is 0 to any neagative # .

But I hammered home on eliminating the option to change computer name during installation :)

OTOH I lost the battle regarding the "non-interactive boot".

Today I did something I'd been intending to do for a while:

[http://ubuntuforums.org/showthread.php?p=10119622#post10119622](http://ubuntuforums.org/showthread.php?p=10119622#post10119622)

Time to go wallow in the mud now but tonight or tomorrow I'll sign up at ubuntu-installer and keep trying.

If I believe in something I'm not one to just give up.

---

### Post by kansasnoob on 2010-11-15
Just subscribed to ubuntu-installer and saw that the maintainer is cjwatson (aka: Colin Watson) so I'm stoked!

Having worked with Colin before I think there's a very good possibility of really fixing this :)

I must go wallow in the mud but I'll continue this tomorrow.

Or anyone can get involved.

Since I know Colin is involved I'm going to hit him with the whole "wish list".

To those that may not know, Colin Watson is the guy that managed to pull together grub2!

No small feat!

And the best dev I've ever worked with on a problem. He's tireless!

---

### Post by Quackers on 2010-11-15
There is hope then :-)

---

### Post by Speed_arg on 2010-11-16
> **kansasnoob said:**
> I double, triple, quadruple checked and I see no option to NOT install grub:

[ATTACH]172506[/ATTACH]

If I'm wrong then show me.

This is very serious to me.

Wow thats a crazy amount of distros. How do you override the partitions number limit?

---

### Post by kansasnoob on 2010-11-16
> **Speed_arg said:**
> Wow thats a crazy amount of distros. How do you override the partitions number limit?

I've only run into problems if I pass 18 or 19, that's why I no longer use separate /home partitions. Of course I have only 3 primaries and one extended. With IDE drives I'd easily gone into the 30's.

Sometimes the newer versions of Gparted balk but 0.4.6-1.iso never gives me any trouble. A long time ago I saw a guide where someone managed to boot 150 OS's with legacy grub.

I do as much testing as possible with VBox but at some point I must get both feet wet to see how an OS works with actual hardware.

Next time I start over from scratch I'll probably go to only one data partition instead of symlinking 4 for Documents, Pictures, Downloads, and Backups.

I never do the same thing twice when I'm rebuilding my own machine :)

---

### Post by ranch hand on 2010-11-16
> **kansasnoob said:**
> I've only run into problems if I pass 18 or 19, that's why I no longer use separate /home partitions. Of course I have only 3 primaries and one extended. With IDE drives I'd easily gone into the 30's.

Sometimes the newer versions of Gparted balk but 0.4.6-1.iso never gives me any trouble. A long time ago I saw a guide where someone managed to boot 150 OS's with legacy grub.

I do as much testing as possible with VBox but at some point I must get both feet wet to see how an OS works with actual hardware.

Next time I start over from scratch I'll probably go to only one data partition instead of symlinking 4 for Documents, Pictures, Downloads, and Backups.

I never do the same thing twice when I'm rebuilding my own machine :)
I haven't counted my partitions of late but in 9.10 testing I was running 21 OS' on 41 partitions on 2 hdds.

I am on a sata box.

The partitioning I do is not recommended and I do not encourage anyone to do it.  That said, all my drives are now set up the same way.  That is one extended partition.  I think it gives maximum flexibility.

It is also easy to brick a drive doing that.  If anyone is silly enough to try it make sure you put something on the drive before leaving the partitioning tool of your choice.  I put a small swap partition at the end of the extended.  With out some thing on there my box will not see the drive.  Yes I learned that the hard way.

The guy with 100+ OS' wrote it all up and I did read it.  I think it was on these forums but it may have been over at Linuxquestions.  Very interesting.  It was when I first did a dual boot of Hardy/Hardy to protect one OS from my "improvements.  Got real interesting in multi boot and read everything I could find.

Real multi booting is an awful lot of FUN.  It also insures that you have something that will boot in spite of your attempts at improving the OS'.

---

### Post by cariboo on 2010-11-16
Personally I prefer using different computers, instead of setting multiple distros on a single system. I've got enough spare computers that were given to me that I can do this. 

That being said I do have one system that  has XP, Natty, PCLOS, OpenSUSE and Fedora 13 installed. My office system also has Win 7, Maverick and Natty installed. While my main system at home only has Maverick and Natty installed.

---

### Post by psusi on 2010-11-16
> **ranch hand said:**
> I haven't counted my partitions of late but in 9.10 testing I was running 21 OS' on 41 partitions on 2 hdds.

Wow... you really should think about using LVM.  I wrote up an article on the wiki the other day: [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm).

---

### Post by kansasnoob on 2010-11-16
> **cariboo907 said:**
> Personally I prefer using different computers, instead of setting multiple distros on a single system. I've got enough spare computers that were given to me that I can do this. 

That being said I do have one system that  has XP, Natty, PCLOS, OpenSUSE and Fedora 13 installed. My office system also has Win 7, Maverick and Natty installed. While my main system at home only has Maverick and Natty installed.

I never manage to hang onto a spare computer for very long. I'm the guy that would give someone the shirt off his back, only in my case it's always that spare computer :)

---

### Post by kansasnoob on 2010-11-16
Well, I fired one off to ubuntu-installer:

> First of all I'd like to introduce myself. You may know me as Erick Brunzell at Launchpad or Lance at iso-testing, and it may help to know that I'm kansasnoob at Ubuntu Forums.

When signing up for "ubuntu-installer" I noticed that Colin Watson is the maintainer and I've worked with both Colin and Evan Dandrea in the past so I hope you take this seriously.

While I'm largely impressed with the overall appearance of the new ubiquity and just how quickly you devs pulled this all together during the Maverick dev cycle, I hope to offer some constructive criticism from an end users perspective without ever being disagreeable.

I'm going to give you the whole laundry list of complaints beginning with what I see as the most serious, the first I actually filed a bug report on too late to make any changes:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Now, just put your noob-shoes on and imagine selecting the option to install alongside an existing OS. Then you see a screen with up to 8 options:

Select drive
Allocate drive space by dragging divider
Offer to use advanced partitioning tool
Use entire partition
Use entire disc
Quit
Back
Install now

You've already chosen to install alongside rather than using the entire disc so why offer the option to use the entire disc again?

And what partition are you being asked to entirely use? That may be exacerbated by this actual bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

I'll follow up on that during Natty iso-testing but most importantly we need to think what level of user is going to use the install alongside option!

It's largely going to be Windows users that have no idea what partition and disc designations mean. They're used to Drive C, etc. So offering confusing options only increases the risk of wiping out their existing OS and/or data.

The second issue is the elimination of the Install to largest continuous space option.  It appears that was a popular option from following the forums. And it was very simple.

The third issue is not being able to maximize or resize the installer windows. Only minimize and close are available. Being able to maximize windows made things much easier, particularly when using the manual partitioning option.

The fourth, last, and most minor thing has to do with grub and it's two pronged:

Since the grub install options are now only available if using manual partitioning you can't really just choose the entire disc option for an auto-install to a new internal drive and then choose to install grub to only that drive.

And there is no longer an option to NOT install grub. I happen to think it's fine to just install grub to either the root partition or /boot if one's being created, but what do you think?

I hope this all makes sense, and I am only trying to provide helpful criticism. I really hope for at least a bit of feedback.

Thanks in advance.

I hope I did good, at least I'm trying :)

---

### Post by ranch hand on 2010-11-16
Sounds good to me.  Good luck.

---

### Post by kansasnoob on 2010-11-21
Well, I'm not giving up. I updated some info here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

specifically:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

Then I fired off a new one to ubuntu-installer, it's not showing up yet in archives but her it is:

> Sorry my previous messages at Ayatana and "ubuntu-installer" have formatted so poorly. I'm legally blind so I do the best I can.

I think you might find my recent post at the forums very useful:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

Or the full thread:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Once again I want to be clear that I'm only trying to improve Ubuntu.

Colin may remember this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

I'm not just a casual complainer.

I try very hard to be precise and I always try to follow up on my own bugs if I find they're not actual bugs.

In this case we have a true bug - actually two bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

I'll certainly be following up on both, particularly the latter.

But it would mean the world to me at this point just to know I'm being heard.

I really hope to have a serious debate regarding needed changes to ubiquity.

I don't give up easy ;)

---

### Post by kansasnoob on 2010-12-02
Added one to the line-up:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

So far I know it can be reproduced by either creating 3 empty NTFS primary partitions or using the manual install method and creating an Ubuntu install existing of 3 primary partitions: </> </home> <SWAP>.

Now I'm going to see what happens with two primary partitions.

Oddly, if extended and logical partitions are used it seems to do what you'd expect, so it requires the use of all primaries.

I still don't see what possible functionality the "Use entire partition" and "Use entire disc" options provide. If you've chosen to install alongside they just seem to add confusion, and in at least the 3 primary scenario there's actual breakage.

---

### Post by dino99 on 2010-12-02
> **kansasnoob said:**
> 

I still don't see what possible functionality the "Use entire partition" and "Use entire disc" options provide. If you've chosen to install alongside they just seem to add confusion.

Agree too, for a newcomer 'free space" is less confusing than "partition"

---

### Post by kansasnoob on 2010-12-02
I did a couple more tests to be certain I knew how to reproduce this bug, here's my most recent comment at that bug report:

> I did a bit more testing this AM since I'd finally gotten my mind around this a bit. I know some of my previous comments got a bit rambling so here's a recap:

This bug can be reproduced by creating either 2 or 3 primary partitions on a testing drive. No extended or logical partitions may be present on the drive.

I've tried this with empty NTFS partitions and a "manually installed" Ubuntu that uses only primary partitions.

Having chosen "Install alongside .........." the installer selects the largest partition as it should, but if you then select "Use entire partition" it actually uses the entire drive.

I must say though, I can't imagine any circumstance under which a person would want to select "Use entire partition" after selecting "Install alongside ..........". I suspect this is responsible for an uptick in reports of OS/data loss at the forums.

IMO the "Use entire partition" and "Use entire disc" options just don't belong there. In fact I believe they only present an opportunity for an inexperienced user to wipe out an existing OS and/or data.

The "Erase and use entire disc" option on the previous screen is more appropriately descriptive.

If I had my druthers I'd like to just see those options removed and have the "Use largest continuous free space" option restored to the prior screen.


I'd appreciate some backup on that if anyone cares to get involved :)

---

### Post by seeker5528 on 2010-12-02
> **kansasnoob said:**
> If you've chosen to install alongside they just seem to add confusion, and in at least the 3 primary scenario there's actual breakage.

If it only does this when you have 3 primary partitions, maybe the bug isn't that it asks if you want to use the entire disk or an entire partition, maybe instead the bug is that the installer doesn't tell you the existing partitioning scheme doesn't allow the installer to create what it wants for a side by side installation. 

If the installer can't use the partitioning scheme it wants (OS on a primary partition/swap on a logical partition), then asking what to do makes perfect sense.

It might be nice if it could look to see if it could put both on logical partitions before resorting to other measures.

Later, Seeker

---

### Post by cariboo on 2010-12-02
The last time I did a side by side install, the two new partitions were create as extended partitions. I had three partitions setup for the first install.

---

### Post by kansasnoob on 2010-12-03
I want to clarify: "alongside" works fine IF you ignore the "Use entire partition" and "Use entire disc" options.

Should you choose "Use entire partition" and you have only primary partitions it will erase the whole disc. This of course would be true even with only one primary partition. If you have any pre-existing extended/logical partitions (even just a SWAP) bug #682429 doesn't appear to happen.

I'd still like someone to explain what possible functionality is added by the presence of "Use entire partition/disc" :confused:

Consider that you're a noob and know nothing about partitioning and you've just chosen from three options:

Install alongside other operating systems
Erase and use the entire disc
Specify partitions manually (advanced)

You don't want to "Erase and use the entire disc" because you want to keep your Windows in tact, and "Specify partitions manually (advanced)" sounds downright scary so you click on "Install alongside other operating systems".

*I should note that the installer will only offer that option if parted recognizes an acceptable arrangement.*

Anyway you next see eight possible options:

Select drive
Allocate drive space by dragging divider
Offer to use advanced partitioning tool
Use entire partition
Use entire disc
Quit
Back
Install now

What possible functionality or "value" do the "Use entire" options add? You've already rejected "Erase and use the entire disc" from the previous screen, why offer it again, and this time w/o the **Erase and**?

And why offer to "Use entire partition"? Throughout my testing it appears that the installer always chooses the largest partition to resize, as it should, so why offer a potentially destructive option at all?

And besides these two bugs negate any possible value added (I contend there is no value is added):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

And if you click on "Use entire partition" you then see this:

[ATTACH]177273[/ATTACH]

And then if you click on "Split largest partition" you come back to this:

[ATTACH]177274[/ATTACH]

Does it not appear that the installer is dead set on forcing you to choose one of the "Use entire" options?

***If you choose to ignore those two buttons you should be OK, however.***

Regardless, imagine you have a typical unbranded OEM install of Win XP. Vista, or 7, which will typically leave you with either one or two primary partitions. It could even be a variety of branded PC's as long as no more than three primary partitions exist.

Knowing that "Install alongside" defaults to using the largest available partition, you resize your main Windows partition and create a new partition for Ubuntu, eg(160GB drive):

-5GB Win Utility----55GB Win XP----100GB set aside for Ubuntu

With bug #682429 if you choose "Use entire partition" expecting that only the 100GB partition will be used you're in for a surprise, and not a good one.

Another scenario that makes bug #682429 particularly bad is if someone has Vista or Win7 with a recovery partition. If they were foolish enough to click on "Use entire partition" and found that Windows is now gone, if the installer had in fact only used the main partition they'd still at least have the recovery partition in tact so they could use PhotoRec to recover data to an external source, then use the recovery partition to restore the PC to it's original state, etc.

I still agree with this earlier statement:

> If I had my druthers I'd like to just see those options removed and have the "Use largest continuous free space" option restored to the prior screen. 

---

### Post by seeker5528 on 2010-12-03
> **kansasnoob said:**
> Does it not appear that the installer is dead set on forcing you to choose one of the "Use entire" options?

Yes, it does not? ;)

How idiot proof do you want to make it? I could see some people being confused, but generally I would hope that if people have already chosen what to do for the installation they would not think they had to choose again. Or at the very least that they would use the slider to determine how much will be dedicated to each instead of choosing a button to switch away from the side by side install.

> Knowing that "Install alongside" defaults to using the largest available partition, you resize your main Windows partition and create a new partition for Ubuntu, eg(160GB drive):

-5GB Win Utility----55GB Win XP----100GB set aside for Ubuntu

With bug #682429 if you choose "Use entire partition" expecting that only the 100GB partition will be used you're in for a surprise, and not a good one.

Since no partitioning/formatting has been done at that point, it wouldn't come as a surprise to me that the entire 155 GB of the 155 GB partition would be used when choosing 'entire partition'.

Maybe I changed my mind since clicking side by side and now *want* the installation to use the entire partition or to use the entire disk.

As far as expectations go, I would be expect when choosing 'entire partition' to be shown some information about what will be done if I continue and a chance to bug out if I don't like it. The same as it was showing that X GB would be used by Windows and X GB by Ubuntu on the 'side by side' screen. Preferably I would also be given a choice of which entire partition to use as opposed to assuming I want to install to the same partition that would have been used for the side by side install.

Later, Seeker

---

### Post by Quackers on 2010-12-04
@seeker
Maybe I changed my mind since clicking side by side and now *want* the installation to use the entire partition or to use the entire disk.

Isn't that what the "back" box is for?

Just out of interest, seeker, have you used the new installer?

---

### Post by kansasnoob on 2010-12-04
> Yes, it does not?

I simply disagree. The options to "use entire" present nothing of value and add only an option to destroy an existing OS or data. Remember you were already offered that choice and you rejected it ;)

> I could see some people being confused

No doubt, I've been iso-testing since Intrepid and it confused me at first.

> I would hope that if people have already chosen what to do for the installation they would not think they had to choose again

There you're forgetting what audience "Install alongside" is generally focused on. I'd argue it's mostly focused on first time dual-booters/Windows users, and most Windows users have no idea what the difference between a partition and a disc is.

They might think, "I guess I want to create a new partition", or "I guess it's asking me if I want to use everything on the installation disc" :(

Remember to put your noob shoes on.

Regardless, if you click on either one and then see the option to "split largest", I guess one could argue that they should be smart enough to think, "yeah, I thought that's what I told it to do"?

But compare that to the old behavior!

> Since no partitioning/formatting has been done at that point, it wouldn't come as a surprise to me that the entire 155 GB of the 155 GB partition would be used when choosing 'entire partition'.

That alone would be bad but, if all the partitions are primary partitions, that's not even what it does! It uses the whole disc! 

> Maybe I changed my mind since clicking side by side and now *want* the installation to use the entire partition or to use the entire disk.

Then click on back or guit :)

> As far as expectations go, I would be expect when choosing 'entire partition' to be shown some information about what will be done if I continue and a chance to bug out if I don't like it. The same as it was showing that X GB would be used by Windows and X GB by Ubuntu on the 'side by side' screen. Preferably I would also be given a choice of which entire partition to use as opposed to assuming I want to install to the same partition that would have been used for the side by side install.

Here again you've chosen NOT to use manual/advanced because you have no idea what you're doing.

With the old installer noobs had the option to "Use largest continuous free space" or if they hadn't already freed up any space they were not presented with these confusing options.

And these two bugs are actual bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

If the devs decide to ignore them or work around them I have no control over that, just like I have no control over grub-pc in Wubi using dpkg (or whatever) to hose their mbr.

Like it or not, we're becoming very unfriendly to new Windows users. We have been for some time.

I discovered Ubuntu when Gutsy was about 2 months old and the installation was simple as heck! Much simpler than anything else I'd tried.

Now it's difficult!

---

### Post by kansasnoob on 2010-12-04
> **Quackers said:**
> @seeker
Maybe I changed my mind since clicking side by side and now *want* the installation to use the entire partition or to use the entire disk.

Isn't that what the "back" box is for?

Just out of interest, seeker, have you used the new installer?

I'd ask if someone has tried it on actual hardware rather than in a VM :)

I'm tired.

---

### Post by Quackers on 2010-12-04
> **kansasnoob said:**
> I'd ask if someone has tried it on actual hardware rather than in a VM :)

I'm tired.

Definitely! It might be a shock for them.

---

### Post by cariboo on 2010-12-04
Clicking the back button the the last couple of installs I've done take you right back to the start of the installation process.

---

### Post by Quackers on 2010-12-04
> **cariboo907 said:**
> Clicking the back button the the last couple of installs I've done take you right back to the start of the installation process.

Yes, the chance to start again after having changed your mind.

---

### Post by kansasnoob on 2010-12-06
Help out here:

[http://ubuntuforums.org/showthread.php?t=1639436](http://ubuntuforums.org/showthread.php?t=1639436)

Typically those posts go unanswered by the OP. They only want their data/OS back so you never hear from them again.

We've hosed ubiquity!

---

### Post by seeker5528 on 2010-12-06
> **Quackers said:**
> @seeker
Maybe I changed my mind since clicking side by side and now *want* the installation to use the entire partition or to use the entire disk.

Isn't that what the "back" box is for?

But I'm lazy, I don't want to have to go back to change the road I'm on, I just want to jump on the other road. ;)

> Just out of interest, seeker, have you used the new installer?

Typically I use the alternate installer and choose the advanced partitioning.

But after seeing the screenshots, it gives a pretty good view of the progression and it seems pretty natural to me.

If you don't really understand partitioning and see that equal parts are going to be used for Windows and Ubuntu, I don't understand why you would click something other than 'Install Now'.

If you want to change the amounts dedicated the each OS, I don't understand why you would do something other than what the instructions say "Allocate drive space by dragging the divider below", then when happy with the amounts click on 'Install Now'. 

> **kansasnoob said:**
> I simply disagree. The options to "use entire" present nothing of value and add only an option to destroy an existing OS or data.

> They might think, "I guess I want to create a new partition", or "I guess it's asking me if I want to use everything on the installation disc" :(

If it always showed what will be done before doing it and always showed the option to change to one of the other paritioning targets, then it should be a non-issue. Then even a noob that clicks on the button to change the type of installation a couple of times should be able to figure out that after you have chosen what to do, 'Install Now' is always selected by default as the next step.

> That alone would be bad but, if all the partitions are primary partitions, that's not even what it does! It uses the whole disc!

If you tell it to use the entire partition and it uses the entire disk, that's definitely a bug and pretty significant.

> And these two bugs are actual bugs:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

But people who don't know partitioning will never know the difference between what it says will happen and what actually happens as long as what actually happens is the correct thing. Not saying it shouldn't be fixed, but it doesn't seem like that high of a priority either, relatively speaking, or maybe better to say it is important, but not a show stopper.

> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

This was already touched on earlier.

> Like it or not, we're becoming very unfriendly to new Windows users. We have been for some time.

There has to be some balance between making it friendly for new users and making it friendly for the people the new users call for help.

I don't know what the thought process of the developers is. If current stuff is a stepping stone to get some additional simplified partitioning options in there, then adding the 'entire disk' and 'entire partition' buttons in there might make sense. If they were just extra buttons added in with no real plans for additional options, then removing them would make sense.

My test system at work has a 40GB drive and dual boots Windows and Lubuntu which I keep a released version on and  I just got a couple of 40GB drives to wipe and test, so maybe I can use one of those as a scratch disk to clone my test set up and do installation/upgrade testing. 

My other systems I have Ubuntu on I actually use and run the in development version on, but I only re-install as a last resort (not very often).
 
Later, Seeker

---

### Post by kansasnoob on 2010-12-07
> My test system at work has a 40GB drive and dual boots Windows and Lubuntu which I keep a released version on and I just got a couple of 40GB drives to wipe and test, so maybe I can use one of those as a scratch disk to clone my test set up and do installation/upgrade testing. 

Remember to reproduce bug #682429 you must create all primary partitions :)

If an extended partition exists things seem to work fine other than the cosmetic thing in bug #657397.

I know it's uncommon to install Ubuntu to all primary partitions but Windows will almost always be installed on all primary partitions. Since the only installable Windows I have is XP I had to come up with an alternative method to test this.

---

### Post by cariboo on 2010-12-07
The full Windows Vista/7 installation doesn't have to be on a primary partition anymore, as long as the hidden 100Mb partition it create's is on the first partition of the first hard-drive.

---

### Post by kansasnoob on 2010-12-07
> **cariboo907 said:**
> The full Windows Vista/7 installation doesn't have to be on a primary partition anymore, as long as the hidden 100Mb partition it create's is on the first partition of the first hard-drive.

But most OEM installs will consist of all primary partitions :D

The point is that if two or three primary partitions exist selecting "use entire partition" should not use the entire disc, but rather use the partition displayed on the left hand side of the "slider" gui, don't you think?

Under what circumstance should "use entire partition" use the whole disc unless one has only one partition to begin with?

I still think simply displaying the "use entire" options after selecting "alongside" only increases the risk of a noob destroying their existing data/OS without providing any viable "value-added".

Yes, that's partly opinion, but these bugs are valid and reproducible:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

---

### Post by seeker5528 on 2010-12-08
> **kansasnoob said:**
> The point is that if two or three primary partitions exist selecting "use entire partition" should not use the entire disc, but rather use the partition displayed on the left hand side of the "slider" gui, don't you think?

The "partitions" displayed on the left and right of the slider don't exist, they are representations of what you will end up with if you click on 'Install Now'.

If you instead click 'user entire partition', what I would view as the desired behavior would be to show you a new screen that shows a graphical representation of the partitions as they actually exist, indicates which one the OS will be installed to, and gives the option to select a different partition to use by clicking a different partition in the graphical representation.

If 'use entire disk' is selected, then I would consider it desired behavior to show a new window indicating the entire disk will be used and for those who have more than one HDD an option to choose which disk will be used.

*If* all of these things are done, then I would consider it desirable that whichever simplified installation scheme you choose, in addition to being able to change the options that are relevant for that scheme, you have the buttons to jump directly to one of the other schemes.

It doesn't make sense to provide the buttons to change to a different scheme if clicking them will result in action without telling the user what is different about what will be done and asking for confirmation.

Later, Seeker

---

### Post by kansasnoob on 2010-12-11
Sorry to take so long to respond, I've just been very busy. regardless you said:

> The "partitions" displayed on the left and right of the slider don't exist

In my experience that's just wrong! The device designation on the left should correctly represent the partition that's going to be "shrunk". With both the old and new ubiquity I've not seen that fail.

Think about it. What does "Install alongside" mean?

If there is sufficient free-space it should offer to use it, eh? It used to but it doesn't anymore :(

Or if all partitions are being used then it should offer to shrink the largest, eh? It does that properly, but what follows seems confusing to me.

Once an end user chooses "alongside other OS" NO potentially destructive option should be offered thereafter IMO.

---

### Post by seeker5528 on 2010-12-13
> **kansasnoob said:**
> In my experience that's just wrong! The device designation on the left should correctly represent the partition that's going to be "shrunk". With both the old and new ubiquity I've not seen that fail.

The entire partition (the one that actually exists) is the combined total of what is represented by the left and right slider.

The partitions on the left and right are what *will* exist *after* shrinking the original and creating the new.

> Think about it. What does "Install alongside" mean?

I could just as easily say 'Think about it. What does 'Entire Partition' or 'Entire Disk' mean?'.

> If there is sufficient free-space it should offer to use it, eh? It used to but it doesn't anymore :(

*If* there is free space, that would imply that either the user knows what they are doing and use the advanced option or they don't know what they are doing so how is it any less confusing to offer to use the free space. 

If they don't know about partitioning, would they know what is meant by 'free space'? 

Offering a choice between 'Along Side' or 'Use Free Space' would be good.

If the existing OS partition and the free space form a contiguous block, then it might be good to show that as the total size instead of the total size of the existing OS partition and have the option to change the total size as well, but then you are getting more complicated again.

> Or if all partitions are being used then it should offer to shrink the largest, eh? It does that properly, but what follows seems confusing to me.

Once an end user chooses "alongside other OS" NO potentially destructive option should be offered thereafter IMO.

'Alongside other OS' is a potentially destructive option, there is always a risk in resizing. The risk may be relatively small, but still a risk.

If you choose one of the other partitioning schemes, there is no potentially about it, choosing to use an existing partition will always result in the existing partition being formatted, choosing to use the entire disk will always cause the entire disk to be formatted. Correct?

If you were *always* shown a visual representation of what will be done, as you are on the 'Alongside' scheme, with some text to indicate something *will* be destroyed to make room for the new if that is the case, and given a button to switch back the the 'Along Side' install, confusion wouldn't be such a big deal because you would see what the result of the action would be before actually doing it and have the option to switch directly to another partitioning scheme if the one you are on doesn't look like it will do what you want.

It's just a question of whether the developers are going to take it there or not and if they are, how long it will take.

If they don't have plans to take it there, I don't know why they would have included the buttons to change to the other simplified partitioning schemes.

Later, Seeker

---

### Post by kansasnoob on 2010-12-18
I finally got a critical ranking on this one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

Turns out that was actually a duplicate of this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

And I may have convinced them to amend the Maverick release notes to reflect that here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

I don't give up easy ;)

---


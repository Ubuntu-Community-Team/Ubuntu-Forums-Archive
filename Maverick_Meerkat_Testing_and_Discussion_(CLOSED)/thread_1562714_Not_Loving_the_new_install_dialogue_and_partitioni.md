---
title: "Not Loving the new install dialogue and partitioning wizard!"
date: 2010-08-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-08-28
I usually use gParted to blow away my old install and leave the space unallocated. Then upon installing a new version, I would simply tell the wizard to use all unallocated space.

There doesn't seem to be such an option anymore and I MUST create the partitions for Swap and ext4 manually.  I'm not lovin' it at all...

Also I think the Lucid slide show looked better than the current screen presented by Maverick.  I sure hope a couple of tweaks are made to this before the release.

Just my $0.02 worth...

---

### Post by ranch hand on 2010-08-28
There will be changes.  The installer at least seems to work now.

The partitioner is pretty bad but it does work.  You could use the "manual" option.  It seems to work, at least for selecting premade partitions.

The auto install of  grub is a very bad idea.

The slide show could be easily improved by removing it.

---

### Post by kahping on 2010-08-28
It's a work in progress after all. Yesterday's ISO seems to work when I tested in a VM.

I do agree on the slide show bit. I guess they haven't gotten around to fixing it for the new installer yet? The text on the slides get cut off

---

### Post by Starks on 2010-08-28
Installing GRUB behind the scenes and without user intervention is extremely dangerous.

I don't want a bootloader written to a partition or my MBR without my partition.

It's bad enough when Windows does it, but at least that's easy to fix.

---

### Post by alexfish on 2010-08-28
> **ranch hand said:**
> There will be changes.  The installer at least seems to work now.

The partitioner is pretty bad but it does work.  You could use the "manual" option.  It seems to work, at least for selecting premade partitions.

The auto install of  grub is a very bad idea.

The slide show could be easily improved by removing it.

will the auto install grub  have any affect on early versions 
of Ubuntu

---

### Post by ronacc on 2010-08-28
> **alexfish said:**
> will the auto install grub  have any affect on early versions 
of Ubuntu

I'm not sure what you mean by that but I can say that for me atleast it found  my earlier installs and added them to the boot menu and boots them ok .

---

### Post by KdotJ on 2010-08-28
I installed last night with yesterdays daily build. I'm sure that the final installer will be better than his, it does also explain that at the beginning. I didn't like the partitioner though either, the options on the previous installers were much better in my opinion. 
I like the backgrounding though, I.e. The way it sorts out user details while it is partitioning the disk in the background

---

### Post by kansasnoob on 2010-08-28
There is an ongoing discussion here:

[http://ubuntuforums.org/showthread.php?t=1548416](http://ubuntuforums.org/showthread.php?t=1548416)

---

### Post by KdotJ on 2010-08-28
> **kansasnoob said:**
> There is an ongoing discussion here:

[http://ubuntuforums.org/showthread.php?t=1548416](http://ubuntuforums.org/showthread.php?t=1548416)

Thanks, I'll head over there

---

### Post by alexfish on 2010-08-28
> **ronacc said:**
> I'm not sure what you mean by that but I can say that for me atleast it found  my earlier installs and added them to the boot menu and boots them ok .

Had a system with 8.04 , 8.18. 9.04 

put 9.10 on using ext4  , and lost track of 8.04 , 8.10 :confused:

---

### Post by Mr. Picklesworth on 2010-08-28
> **crjackson said:**
> 
Also I think the Lucid slide show looked better than the current screen presented by Maverick.  I sure hope a couple of tweaks are made to this before the release.

Just my $0.02 worth...

The current one should be the same as the Lucid one so far, albeit with the first slide replaced by placeholder text. New one is coming in this branch:

[https://code.edge.launchpad.net/~dylanmccall/ubiquity-slideshow-ubuntu/maverick-ubuntu-design](https://code.edge.launchpad.net/~dylanmccall/ubiquity-slideshow-ubuntu/maverick-ubuntu-design)

It's based on the design team's (as usual excellent looking) new mockup:
[ATTACH]167744[/ATTACH]

We're borrowing the copy from the web site's tour thingy, which should make things simpler for everyone. (And if you're particularly observant, you may note that is *also* using writing done for Lucid. Maverick copy is coming, apparently, hopefully with more calls to action and fewer attempts to sell Ubuntu to the converted).

---

### Post by ronacc on 2010-08-28
why bother ? does anyone actually sit there slack jawed and drooling watching the install slide show ? the are a lot better ways to waste a few minutes , run down to the store for a six pack , make out wither your girlfriend , chase the neighbors kids off your lawn .

---

### Post by zekopeko on 2010-08-28
> **ronacc said:**
> why bother ? does anyone actually sit there slack jawed and drooling watching the install slide show ? the are a lot better ways to waste a few minutes , run down to the store for a six pack , make out wither your girlfriend , chase the neighbors kids off your lawn .

It's called polish.

---

### Post by Mr. Picklesworth on 2010-08-28
> **ronacc said:**
> why bother ? does anyone actually sit there slack jawed and drooling watching the install slide show ? the are a lot better ways to waste a few minutes , run down to the store for a six pack , make out wither your girlfriend , chase the neighbors kids off your lawn .

> **zekopeko said:**
> It's called polish.

Because people (me especially) like shiny stuff.

We're hoping this can give some new users a bit more confidence and knowledge. One big problem we have is people who install Ubuntu but don't know about Software Centre, for example. Often leads to breakage and / or unhappy users. So, this points that feature out quite prominently. I think the new writing carries a better spirit of adventure than my own did for Lucid, which fills that &#8220;confidence&#8221; part. Hopefully we'll have more casual users excited to try new things such as GIMP and Stellarium, and then even more excited when they find *even more* new things.

---

### Post by crjackson on 2010-08-28
> **Mr. Picklesworth said:**
> The current one should be the same as the Lucid one so far, albeit with the first slide replaced by placeholder text. New one is coming in this branch:

[https://code.edge.launchpad.net/~dylanmccall/ubiquity-slideshow-ubuntu/maverick-ubuntu-design](https://code.edge.launchpad.net/~dylanmccall/ubiquity-slideshow-ubuntu/maverick-ubuntu-design)

It's based on the design team's (as usual excellent looking) new mockup:
[ATTACH]167744[/ATTACH]

We're borrowing the copy from the web site's tour thingy, which should make things simpler for everyone. (And if you're particularly observant, you may note that is *also* using writing done for Lucid. Maverick copy is coming, apparently, hopefully with more calls to action and fewer attempts to sell Ubuntu to the converted).

That's good news.  I install on nearly 40 machines every release.  People have there first exposure while watching me install often make comments as to the installers looks and performance.  I always love it when new users are impressed with the ease and looks of the installer.

---

### Post by crjackson on 2010-08-28
> **ronacc said:**
> why bother ? does anyone actually sit there slack jawed and drooling watching the install slide show ?

Yeah sure.  That's all I do in life.

---

### Post by crjackson on 2010-08-28
> **zekopeko said:**
> It's called polish.

And it counts a lot with new users especially. I too like to see a slick looking install. It looks less hackish and more professional. It presents the feeling of a quality product.

---

### Post by crjackson on 2010-08-28
> **ranch hand said:**
> There will be changes.  The installer at least seems to work now.

The partitioner is pretty bad but it does work.  You could use the "manual" option.  It seems to work, at least for selecting premade partitions.

The auto install of  grub is a very bad idea.

The slide show could be easily improved by removing it.

yea, I did manual install option without major issues, and the grub thing is a real mistake IMO. It's just an observation on my part.  As I bring new Ubuntu users into the mix, I like to have bragging rights for Ubuntu. You can't imagine how many computer users struggle no matter what the OS is, unless it's pre-installed.  I like to show them that "You too, can Ubuntu!".

A slick install is really impressive. When a new user gets confronted with issues before it's even on the HD, it tends to sour the milk. It's the same regardless of OS, but the vast majority of users never have to worry with the initial install when using an MS OS, so an easy install Ubuntu install that shows them how easy it truly is makes for a nice experience.

---

### Post by ktp on 2010-08-28
> **crjackson said:**
> And it counts a lot with new users especially. I too like to see a slick looking install. It looks less hackish and more professional. It presents the feeling of a quality product.

first impression is everything.

---

### Post by KdotJ on 2010-08-28
> **crjackson said:**
> And it counts a lot with new users especially. I too like to see a slick looking install. It looks less hackish and more professional. It presents the feeling of a quality product.

+1
It also makes people feel a bit more relaxed and think that maybe, perhaps you don't need to be a command line wizard to use linux

---

### Post by kansasnoob on 2010-08-28
> **ronacc said:**
> why bother ? does anyone actually sit there slack jawed and drooling watching the install slide show ? the are a lot better ways to waste a few minutes , run down to the store for a six pack , make out wither your girlfriend , chase the neighbors kids off your lawn .

+++ One Million!!!!!!!!!!!!!!!!!!

Who cares about that?

I want an installation process that just works and allows advanced options without confusing those who don't need advanced options.

So far this new ubiquity is just confusing!

---

### Post by cariboo on 2010-08-28
Of the few times I've shown someone the install process, they are more impressed by the fact that you can do something else while the install proceeds. Normally I boot to the desktop and run the installer from there, once all the details have been entered I usually open up firefox and check the forums, or play a rousing game of solitaire. :) To bad [pysolfc]("http://pysolfc.sourceforge.net/") isn't installed by default.

---

### Post by VMC on 2010-08-28
> **kansasnoob said:**
> +++ One Million!!!!!!!!!!!!!!!!!!

Who cares about that?

I want an installation process that just works and allows advanced options without confusing those who don't need advanced options.

So far this new ubiquity is just confusing!

This has to be for new users, aka Windows users. They love watching things.  I preferred the progress bar myself. Bygone days for sure.

And that small 2-3 line mini terminal is meaningless. At least right now. In the future it might play a better role.

Ubiquity is a work in progress. At least it now works. Before I had to jump through hoops to get Ubuntu installed.

---

### Post by kansasnoob on 2010-08-28
From a few things said here and in other threads I wonder if things aren't different with various front-ends?

I guess I'll have to explore some more.

---

### Post by Glenn nl on 2010-08-29
> **crjackson said:**
> I usually use gParted to blow away my old install and leave the space unallocated. Then upon installing a new version, I would simply tell the wizard to use all unallocated space.

There doesn't seem to be such an option anymore and I MUST create the partitions for Swap and ext4 manually.  I'm not lovin' it at all...


Really?
That sucks, I have been doing it like that for a year.
Is that option coming back?

---

### Post by 23meg on 2010-08-29
> **Glenn nl said:**
> Really?
That sucks, I have been doing it like that for a year.
Is that option coming back?

According to [this part]("https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_Allocate_drive_space_autom") of the spec, it *may not* be.

---

### Post by ronacc on 2010-08-29
> **Glenn nl said:**
> Really?
That sucks, I have been doing it like that for a year.
Is that option coming back?

just use the advanced option ( specify partitions manually ) , you can either prepare the partitions with gparted when you wipe the old install or roll the dice and hope that ubiquity actually does what you tell it and not wipe the whole box .

---

### Post by crjackson on 2010-08-29
> **23meg said:**
> According to [this part]("https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_Allocate_drive_space_autom") of the spec, it *may not* be.

Well... we'll just have to wait and see how it all turns out.  I wouldn't mind seeing a graphic representation of each available partition on the drive and the ability to select it for the install location.

---

### Post by ranch hand on 2010-08-29
I do not see anywhere in that document a mention of grub installation.  This is troubling.

---

### Post by 23meg on 2010-08-29
> **ranch hand said:**
> I do not see anywhere in that document a mention of grub installation.  This is troubling.

Here:

> 
Stuff that is in the advanceed thing:

[] install boot loader
    Device for boot loader installation

---

### Post by ronacc on 2010-08-29
unfortunately the choice of boot loader location has not yet been implemented , for many of us that is a show stopper .

---

### Post by ranch hand on 2010-08-29
Ah there you go again.  Proving once again that I can't see.

Had to run through it 2 more time to find it.

This is a big relief even if it appears to be a much lower priority than "improving" the slide show.

---

### Post by Starks on 2010-08-29
> **ronacc said:**
> unfortunately the choice of boot loader location has not yet been implemented , for many of us that is a show stopper .
Yup. It's bad design decisions like this that make Ubuntu look like a noob distro that's unfriendly to power users.

---

### Post by 23meg on 2010-08-29
> **Starks said:**
> Yup. It's bad design decisions like this that make Ubuntu look like a noob distro that's unfriendly to power users.

What exactly is the "bad design decision" here?

---

### Post by ronacc on 2010-08-29
> **23meg said:**
> What exactly is the "bad design decision" here?

since the development daily's are aimed at testers who are exactly those most likely to have multi disk/partition/installs  , pushing the new installer in without the ability to control where grub is to be installed ( or even if it is to be installed ) , is certainly a questionable " design decision" if not an outright stupid one .

---

### Post by ranch hand on 2010-08-29
> **ronacc said:**
> since the development daily's are aimed at testers who are exactly those most likely to have multi disk/partition/installs  , pushing the new installer in without the ability to control where grub is to be installed ( or even if it is to be installed ) , is certainly a questionable " design decision" if not an outright stupid one .
And we have a bunch of us grumpy geezers testing.  If they don't treat us nice we won't let them in our yards.

---

### Post by MacUntu on 2010-08-29
I just hope they will re-add the "hostname" field. I don't want my machine named <user>-laptop or - I guess - <user>-pc (yeah, I know how to change it later).

---

### Post by ranch hand on 2010-08-29
Not a real good security arrangement for sure.

---

### Post by KdotJ on 2010-08-29
> **MacUntu said:**
> I just hope they will re-add the "hostname" field. I don't want my machine named <user>-laptop or - I guess - <user>-pc (yeah, I know how to change it later).

I second that.. hope it comes back for final

---

### Post by ktp on 2010-08-29
> **MacUntu said:**
> I just hope they will re-add the "hostname" field. I don't want my machine named <user>-laptop or - I guess - <user>-pc (yeah, I know how to change it later).

doesn't windows even let you name your computer...I sure hope to see some way to name it while I install...even if that mean I have to click few more buttons.

---

### Post by cariboo on 2010-08-29
> doesn't windows even let you name your computer...I sure hope to see some way to name it while I install...even if that mean I have to click few more buttons.

When your are at the networking setup section in Windows XP you can set the computer name and workgroup, I'm not as familiar with Win 7 setup, but I know you can set the computer name during installation, or you can change it by going to Start->Control Panel->System.

---

### Post by kansasnoob on 2010-08-29
I'm hoping there will be one more round of updates before the Beta, but regardless this is going to be one heck of an iso-testing cycle :D

And I suspect the period between Beta and RC will also be challenging. I normally enjoy a challenge but right now I'm into the 4th month of a two month remodel, things continue to go wrong, and that all seriously hampers my ability to test :(

I'm guessing this will all work out in the long run. IMHO this is the real purpose of testing, find bugs, file a decent bug report, etc.

And iso-testing is an excellent way to do that! Once a bug gets a "qa" tag you will get some response! The response may not always be what you'd like but so goes life (and remodeling).

---

### Post by kansasnoob on 2010-09-01
It appears to me that the "manual partitioning" option works flawlessly.

Can't really say the same of either the "side by side" or "entire disc" options :(

Quite confusing :confused:

I'll try and get some screenshots posted when I'm done iso-testing.

---

### Post by kansasnoob on 2010-09-01
Oh, also I filed a bug report about the hostname issue:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

---

### Post by ranch hand on 2010-09-01
> **kansasnoob said:**
> Oh, also I filed a bug report about the hostname issue:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)
Added to it and marked it serious on the report.  Just crazy.

---

### Post by kansasnoob on 2010-09-01
Hmmm, I already mentioned the issue of being able to name your puter something other than username-desktop so lets see what else I complained about:

************************************************

Maverick ubiquity windows can not be resized/maximized

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

************************************************

Not possible to create an extended partition w/ubiquity 2.3.12  

[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/627805](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/627805)

That one's resolved!

************************************************

Then the biggy:

During install reports size of new partition as 0.0 B  

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

And, no, I didn't name it! Regardless it goes beyond that. This what I wrote last there:

> I just tried two more installs , using ubiquity version 2.3.13, details below:

I began with another entire disc install, beginning with only one drive installed:

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
 1 1049kB 25.4GB 25.4GB primary ext4 boot
 2 25.4GB 80.0GB 54.7GB extended
 6 25.4GB 50.1GB 24.7GB logical ext4
 8 50.1GB 73.5GB 23.4GB logical ext4
 9 73.5GB 74.6GB 1061MB logical linux-swap(v1)
 7 74.6GB 76.7GB 2142MB logical linux-swap(v1)
 5 76.7GB 80.0GB 3305MB logical linux-swap(v1)

**[COLOR="Red"]After choosing the "Erase and use entire disc" option I'm taken to a screen that shows "Allocate drive space" and I see the graphic "Ubuntu /dev/sda (ext4) 0.0B" with the two options "Use entire partition" or "Split largest partition". Since I'd already selected the "entire disc" option why is it even asking me those two questions? Which partition? I've already chosen to "Erase and use entire disc" so why ask if I want to split a partition?[/COLOR]**

Also the "use the advanced partitioning tool" option was NOT available!

I clicked on neither one of those options. I just clicked on "Install now".

It did install properly (I rebooted to be sure):

lance@lance-desktop:~$ sudo parted /dev/sda print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
 1 1049kB 76.7GB 76.7GB primary ext4 boot
 2 76.7GB 80.0GB 3305MB extended
 5 76.7GB 80.0GB 3305MB logical linux-swap(v1)

But I can easily see how this would be very confusing,

Next I went for a "side by side" install on that same drive. I made no changes to the partitions before beginning. After clicking on "Install side by side choosing between...." I go to a screen that this time shows the partitions properly. It showed 37.8GB and 38GB, and it showed one smaller partition hidden (obviously SWAP) along with the option to use the advanced partitioning tool. And the "slider" works to change partition size.

**[COLOR="Red"]But it also shows the options to "Use entire partition" or "Use entire disc". Need I explain the potential confusion surrounding that? Which partition are they referring to? Which disc? Remember that Windows users are used to thinking "A", "C", "D", etc. Many don't know the difference between a disc and a partition because Windows keeps us "dumbed down" :^)[/COLOR]**

However I simply bypassed those options again, clicked on "Install now", and the install was successful:

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
 1 1049kB 38.7GB 38.7GB primary ext4 boot
 2 38.7GB 80.0GB 41.3GB extended
 6 38.7GB 75.1GB 36.4GB logical ext4
 7 75.1GB 76.7GB 1605MB logical linux-swap(v1)
 5 76.7GB 80.0GB 3305MB logical linux-swap(v1)

I wish I could come up with some consistent pattern here but I've been testing with both 2.3.12 and 2.3.13 the past two days and I can not find a consistent behavior :^(

I'd first thought it had to do with the number of partitions but I've now tried it enough to know that's not the case.

The problem is also not just limited to this "misreading" of drive/partition size. Improper (or poorly described) options are offered after making an initial selection.

So, I'm thinking this at least needs a mention in the release notes but the behavior is so inconsistent I have no idea what a person could say. I very much fear what will happen with Win 7 users because many OEM installs have 3 existing partitions (one tiny one with part of the boot files, another with sys utility, and the big one with the actual OS).

This scares me big time. Even for a Beta!

I'm quite tired so if this makes very little sense please accept my apologies in advance, and hang in there ;^)

So I gave both the "entire disc" and "auto resize" iso tests a fail! I hope we can get more feedback on that.

Right now I'm tired, I'll bet I've done at least 20 installs in the last 24 hours trying to find a common trigger or some consistent behavior with this new ubiquity and I just can't.

Time for a break :D

---

### Post by kansasnoob on 2010-09-01
> **ranch hand said:**
> Added to it and marked it serious on the report.  Just crazy.

These "design choice" issues can be tricky. I still very much dislike the new live-boot. Even if you do know that you need to edit boot parameters at boot a silly 3 second window in which to hit "any key" when those two stupid looking emblems show up is ridiculous.

If you're booting and the phone rings, or if you pass gas, belch, or if one of the grandkids screams you've missed the option to edit so you have to reboot again.

That's a battle I lost and it still sticks in my craw, although SABDFL sent me several emails so at least I can say I corresponded with a really, really rich guy at least once :)

Honestly, in our discussions he was always very nice. But he's the boss and that's the way he wants it!

Let's hope we can handle this one more effectively. At least Colin Watson left it open so we still stand a chance :)

---

### Post by buzzmandt on 2010-09-01
> **kansasnoob said:**
> Oh, also I filed a bug report about the hostname issue:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

checked the affects me too.

---

### Post by seeker5528 on 2010-09-01
The 'not being able to change the hostname' thing seems a bit whacked to me, so I added my input to the comments of [Bug #628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087).

Later, Seeker

---

### Post by ktp on 2010-09-01
> **seeker5528 said:**
> The 'not being able to change the hostname' thing seems a bit whacked to me, so I added my input to the comments of [Bug #628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087).

Later, Seeker

I liked your idea...I hope there is some way before release...even if it is hidden under "advance config" or something and I have to click 2 or more clicks.

---

### Post by ronacc on 2010-09-01
added my me too's to all of the above bugs .

---

### Post by kansasnoob on 2010-09-02
I see ubiquity is up to version 2.3.15 now so I know they're still working on it.

I wonder if we won't have one more round of iso-testing?

Or if the Beta will be delayed?

---

### Post by kansasnoob on 2010-09-02
Well they kicked it loose :D

I'm more than a bit worried since Beta usually brings many more testers into the fold, some quite new to boot. Nothing wrong with that but I have some concerns. Especially regarding both the "side by side" and "entire disc" installs.

Choosing "side by side" typically gets me this:

[ATTACH]168342[/ATTACH]

I think that's a tiny bit confusing. Why ask me if I want to "split" the largest partition after I've already selected "side by side", but that may not be terribly bad. The "slider" seems to work right so if you just adjust the partitions to the proper size, and then click on "Install now", it seems to work OK.

OTOH it's not always that smooth, sometimes I get this:

[ATTACH]168343[/ATTACH]

Why offer "entire disc" and/or "entire partition", for that matter which partition are they referring to?

Think about Windows users. With Win 7 OEM installs it's very common to have 3 existing partitions. Would that confuse you?

I tried this quite a bit, over 20 trial installs I'm sure, and I find this horribly confusing! Then toss in the fact that many Windows users don't understand the difference between a disc and a partition :eek:

I expect this to be a nightmare. In my next post I'll show some examples of "entire disc" install confusion.

---

### Post by ranch hand on 2010-09-02
I do not have the disk space to do that testing on and seeing your pics makes me very happy I don't.  That is one of the stupidest things I have ever seen.

It almost looks like they sat around and said "is there some way that we can make this twice as hard as it needs to be".

I just use the manual option.

From the looks of it the wise thing to do is to recommend the Alt install to noobs as it is easier to understand.

I am getting to feel that way for me anyway.  The installer was fine until they decided to improve it.  I was a total Linux noob when I installed Hardy, it was no trouble at all.  Now you have this kind of stuff.  Nuts.  Oh well they can watch the video while Ubuntu eats their drives.  How nice.

The only thing that keeps me on the Live CD is the ability to copy some music to the Live Session to listen to while installing.  Just not having to see this kind of thing and then the damn video is getting real close to tipping the scales to the Alt or just Debian full time.

---

### Post by kansasnoob on 2010-09-03
The following is fairly common with "entire disc" but I've also seen it with "side by side" (although not as often):

[ATTACH]168345[/ATTACH]

Since is shows a drive designation why is it showing 0.0? Just ignoring and installing seems OK but sometimes I'd even get this:

[ATTACH]168346[/ATTACH]

Why would it offer to split a partition when I've selected to use a whole drive?

This is why I spent a lot of time, literally testing this no less than 20 times, just to see how things worked.

I realize it's a WIP and this is only BETA but I fear the worst. My best suggestion ATM is use nothing but the manual partitioning option.

Other than lacking the option to not install grub at all the manual partitioning option seems great.

I did mention all of this at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

And this one seems important too:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

In fact the latter is not even assigned which really bothers me but I'm trying. It's going to take a lot of diligence on our part to see the devs get this all fixed by the RC :D

---

### Post by kansasnoob on 2010-09-03
> **ranch hand said:**
> I do not have the disk space to do that testing on and seeing your pics makes me very happy I don't.  That is one of the stupidest things I have ever seen.

It almost looks like they sat around and said "is there some way that we can make this twice as hard as it needs to be".

I just use the manual option.

From the looks of it the wise thing to do is to recommend the Alt install to noobs as it is easier to understand.

I am getting to feel that way for me anyway.  The installer was fine until they decided to improve it.  I was a total Linux noob when I installed Hardy, it was no trouble at all.  Now you have this kind of stuff.  Nuts.  Oh well they can watch the video while Ubuntu eats their drives.  How nice.

The only thing that keeps me on the Live CD is the ability to copy some music to the Live Session to listen to while installing.  Just not having to see this kind of thing and then the damn video is getting real close to tipping the scales to the Alt or just Debian full time.

I'm not exaggerating when I say, "this is the worst I've seen regarding the Ubuntu live installer"!

I try almost every distro out there from time to time and I'd always thought Ubuntu had the best "live installer" there was. Not now!

ATM this really feels like "change only for the sake of change". I'm only aware of one annoying little bug with the old ubiquity:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/571802](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/571802)

And the original:

[https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/19732](https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/19732)

I'd suggested:

> I'd really like you to consider the following:

1) When the graphic appears to be frozen at 50% for a long time noobs will consider that "it's stuck"!

2) The amount of time it takes to complete the operation depends greatly on the amount of data to be moved, etc.

3) Aborting can cause data loss!

I really think we should drop the progress bar and percentage altogether until we perfect it. Just stick with, "WAIT". And possibly a stronger warning.

Also consider who uses "auto-resize". Noobs of course :^)

So they sit and watch, and after an hour or so they think IT'S STUCK!

We're not putting our noob shoes on here ;^/

I've been installing Ubuntu and many other Linux distros since early 2008 and this scares me worse than any change Ubuntu has made.

---

### Post by ranch hand on 2010-09-03
Yup not good at all.

Up to now the only problem I have really had with the Ubuntu installer is dialup configuration.  Most other distros can do this with 3 questions during the install.

It appears that they are addressing this problem in he most direct way possible.  Make every thing just as bad.

It is scary.

---

### Post by ktp on 2010-09-03
Don't give up on this...this is just the first round...it will be better by next LT =)

---

### Post by VMC on 2010-09-03
I noticed resizing using gparted also takes a great deal of time. I lost some data recently because of the excessive amount of time and I gave up.

I always use manual partitioning when using ubiquity. It would be nice to show some numbers showing through for the users than those "idiot gauges" like the progress bar. then at least the user could tell if anything is happening. Colin in post#7 mentioned about using resize2fs. If they could implement that , it would be great.

In Windows, that was a great benefit of using a program such as ImgBurn vs Nero , when ImgBurn would show sectors it was either writing or verifying, Nero was using % / progress

edit: this was in reply to post#56 above.

---

### Post by kansasnoob on 2010-09-03
> **VMC said:**
> I noticed resizing using gparted also takes a great deal of time. I lost some data recently because of the excessive amount of time and I gave up.

I always use manual partitioning when using ubiquity. It would be nice to show some numbers showing through for the users than those "idiot gauges" like the progress bar. then at least the user could tell if anything is happening. **[COLOR="Red"]Colin in post#7[/COLOR]** mentioned about using resize2fs. If they could implement that , it would be great.

In Windows, that was a great benefit of using a program such as ImgBurn vs Nero , when ImgBurn would show sectors it was either writing or verifying, Nero was using % / progress

edit: this was in reply to post#56 above.

Is that Colin Watson or another Colin?

I've had no huge problems using gparted from the live CD but if I have a lot of "parted" work to do I still use version "gparted-live-0.4.6-1.iso" just because it works.

What I'm thinking is this is such a huge change we'd all benefit from something like what **keybuk** did regarding ureadahead, remember:

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

In this case the informational thread could even be "closed" and "stickied". No need for a dev to tie up a lot of time responding or anything like that.

---

### Post by arpanaut on 2010-09-03
> **ktp said:**
> Don't give up on this...this is just the first round...it will be better by next LT =)

Sorry but I think you misunderstand where these gentlemen are coming from.
They have legitimate complaint!

I think in an effort to simplify, fine grained customization is lost.  I've been installing Ubuntu for almost six years now and am seeing thing get more complicated with every release.  For years I ignored the 'Live_CD" for the  alt.install because it confused me, The alt. install is more difficult but it does what you expect.

Lately, I've seen UI choices that presumed "prior knowledge" of the installation process.  Windows Users are not going to be able to make the "correct" choices because of their "prior knowledge",  How do I say this discretely...  If very experienced Ubuntu users are confused and "making mistakes" WTF are these user interface developers thinking.  

Personally. I'm moving back to the alt. installer, I don't know where the disconnect between the Ubuntu developers and the real users is, but it scares the hell out of me!

Kudos to kansasbob and ranch_hand for their efforts to bring a different perspective to these issues.

P.S. Late Lucid, early Maverick, the live CD install  was logical to me (except for the grub install issues) but lately I cannot "see" where this is headed.  People are not stupid, don't dumb things down so much that you insult them!

---

### Post by ronacc on 2010-09-03
now that they have chosen to go with a dvd for the actual releases I think its time that they rethink the whole way they handle the install process . I know there is the alt install but would a newbe ? right after the timezone and keyboard screens they need to split the process , one branch for fewest choices ( and for God's sake explain what the choices mean ) and one branch allowing much more control over the installation . They can call them what they like , express/custom , simple/advanced ,dumb/smart , I really dont care about the names , just that we get a little sanity in the process .

---

### Post by Starks on 2010-09-03
Wait, what?

Ubuntu is transitioning to DVD ISOs for default?

Where is this coming from?

---

### Post by ronacc on 2010-09-03
the last couple of actual releases have been on dvd .
[http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/)

---

### Post by 23meg on 2010-09-03
> **ronacc said:**
> the last couple of actual releases have been on dvd .

That's [not true]("http://releases.ubuntu.com/"), and no, there's no intention to switch to DVDs as the main distribution medium right now.

---

### Post by ronacc on 2010-09-03
sorry , my bad , I don't go in through the front page , I just go straight to the url I posted .

---

### Post by crjackson on 2010-09-03
A DVD install wouldn't be a particular issue for on my systems, however I install Ubuntu on MANY systems that don't have a DVD drive. I'm glad that was in incorrect statement.

---

### Post by jerrylamos on 2010-09-03
I've got a 1024x768 screen on this test machine.  Not many are smaller; I think even the netbooks have 1024x600 or 1024x576?

Install partitioner by default uses very small windows.  Hello?  Even though this is an older pc, it's got 16 partitions on it with various Ubuntu and non-ubuntu.  I need more than a few lines!

Several windows on the installer are pretty small.  Let's use the space so we can see.

Yes I always do manual partition, there's a swap already so I don't specify that.  If the installer's formatting works (sometimes it's busted) I use that on my chosen partition, otherwise use gparted to prepare the partition.

Then after installing I boot a different ubuntu so I can label the just installed partition.  Why no choice to do that with the installer??

Well anyway, install worked.  I think I got one ubiquity crash on one of the installs (reported it) but it ran anyway.

Jerry

---

### Post by cariboo on 2010-09-03
I'm just in the process of installing the netbook edition, on the manual partitioning screen there is a now a drop down, for where you want to install grub, I left the default, as this system only has one hard drive.

@jerrylamos, I've got a 1024X600 screen, everything just barely fits so far.

---

### Post by kansasnoob on 2010-09-03
> **jerrylamos said:**
> I've got a 1024x768 screen on this test machine.  Not many are smaller; I think even the netbooks have 1024x600 or 1024x576?

**Install partitioner by default uses very small windows.**  Hello?  Even though this is an older pc, it's got 16 partitions on it with various Ubuntu and non-ubuntu.  I need more than a few lines!

Several windows on the installer are pretty small.  Let's use the space so we can see.

Yes I always do manual partition, there's a swap already so I don't specify that.  If the installer's formatting works (sometimes it's busted) I use that on my chosen partition, otherwise use gparted to prepare the partition.

Then after installing I boot a different ubuntu so I can label the just installed partition.  Why no choice to do that with the installer??

Well anyway, install worked.  I think I got one ubiquity crash on one of the installs (reported it) but it ran anyway.

Jerry

I filed a bug report regarding that during iso-testing:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

No action there yet in spite of it getting the qa tag.

I know with the old ubiquity you could maximize the windows which made it much easier :)

Maybe some more subscribers and "effects me to's" will help.

---

### Post by seeker5528 on 2010-09-03
> **ronacc said:**
> the last couple of actual releases have been on dvd .
[http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/)

The live image on the DVD is the same as the one on the CD and if you use Ubiquity to install, the installed system will be the same as well.

The main benefit of the DVD is that it includes packages for everything in main. So whether you are running the live session or from an installation, you have a significant amount of additional software available for installation even if you don't have an internet connection available.

Later, Seeker

---

### Post by ronacc on 2010-09-03
I understand that the live image is the same but the extra software available on the dvd makes it even more desirable to enhance the installer per my original comment .

---

### Post by 23meg on 2010-09-03
> **seeker5528 said:**
> 
The main benefit of the DVD is that it includes packages for everything in main. So whether you are running the live session or from an installation, you have a significant amount of additional software available for installation even if you don't have an internet connection available

The DVD doesn't contain everything in main; that's a common myth. It just contains all language packs, plus a few additional applications. Its main benefit is the language packs.

[http://people.canonical.com/~ubuntu-archive/germinate-output/ubuntu.maverick/dvd](http://people.canonical.com/~ubuntu-archive/germinate-output/ubuntu.maverick/dvd)
[http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd)

---

### Post by seeker5528 on 2010-09-03
> **ronacc said:**
> I understand that the live image is the same but the extra software available on the dvd makes it even more desirable to enhance the installer per my original comment .

I would like to see the live image include some additional software, but I doubt the installer will ever be different than with the CD version. 

If you choose to boot the alternate install, then you are running the Debian installer, so your experience there depends on how far the Debian devs have come with it, I keep seeing stuff about it being GUIfied, but haven't seen that yet. 

Usually when I use the Debian installer I end up either choosing the standard desktop install or do a minimal install otherwise if I try to use the curses interface of aptitude to browse and select stuff I want to install, aptitude always seems find a way to **** me, easier than dselect my ***. But that's a whole different conversation. :p

Later, Seeker

---

### Post by cariboo on 2010-09-03
I did a debian lenny net install a couple of months back on an Apple G3, I was offered the choice of a graphical install, although it didn't work properly. I put that down to having an ATI card in the thing. I only did a command line install, so I didin't need a gui to install it.

---

### Post by ktp on 2010-09-03
> **arpanaut said:**
> Sorry but I think you misunderstand where these gentlemen are coming from.
They have legitimate complaint!

I think in an effort to simplify, fine grained customization is lost.  I've been installing Ubuntu for almost six years now and am seeing thing get more complicated with every release.  For years I ignored the 'Live_CD" for the  alt.install because it confused me, The alt. install is more difficult but it does what you expect.


Don't get me wrong...I agree with them.  I think the new installer is missing some key things also, which I have commented on bugs that they have opened.  I also think making it simpler is good idea, but not a good one at the cost of losing some others ones and having to to directly to alt.install, which seem to much for me too.

I guess I am hoping the bugs will be looked and something reasonable comes out of it...if not now, then by next LTS.

> **arpanaut said:**
> 
Kudos to kansasbob and ranch_hand for their efforts to bring a different perspective to these issues.

kudos to both and keep up to good work and helping other people out.

---

### Post by kansasnoob on 2010-09-06
Looking at still existing bugs in Ubiquity today I'm thinking we're down to four things:

1) Not possible to NOT install grub (unassigned and confirmed).

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033)

2) They've fixed the thing about being able to minimize windows during install, and possibly even fixed the window size during "slide-show" but it's still not possible to maximize or "resize" any of the installation screens - particularly when you go to manual partitioning. But IMHO all "install windows" should be capable of "maximizing". (Some of us blind old farts like to be able to see what we're doing)-(new and still unassigned):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

3) Not possible to change computer name during installation. (confirmed - low priority - unassigned):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

4) General confusion with partition/drive size, device installation description, installation options in general (this one is hard to explain unless you've seen it) -(:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

At least the latter one is High priority and assigned. And I have a lot of faith in Evan Dandrea. I've dealt with Evan before doing iso-testing and I always get some solution.

I am concerned though. Are my comments at that last bug complete enough?

Should I file a new bug report about confusing options being offered?

With the other bugs should I take some other action?

If so what action?

I need all the help I can get everyone!

We all know that maverick final gets released one time! It's very doubtful they'd have a redo of the final iso!

Lets get busy!

---

### Post by kansasnoob on 2010-09-06
BTW I hope I did that right ;)

I'm old, legally blind, and tired :D

---

### Post by ranch hand on 2010-09-06
> **kansasnoob said:**
> BTW I hope I did that right ;)

I'm old, legally blind, and tired :D
I sure am glad to hear that you a legally blind.  I would hate to think you were criminally blind.

---

### Post by kansasnoob on 2010-09-06
> **ranch hand said:**
> I sure am glad to hear that you a legally blind.  I would hate to think you were criminally blind.

That's the funniest thing I've read in days :lolflag:

But, my point was that I can overlook things and I see all of these issues as quite serious.

It's one of those situations where we can either be part of the solution or part of the problem :)

But my limited vision is one of the reasons I can't do things like use IRC, etc.

I do, always. appreciate your humor.

---

### Post by kansasnoob on 2010-09-06
I'm really wondering if these bugs shouldn't be broken down into different threads?

Have you read them?

---

### Post by kansasnoob on 2010-09-06
I kicked this one onto Ayatana:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

with SABDFL cc'ed :D

> noticed early on with the new ubiquity that there was no option to rename the computer during installation. While I don't personally do that I saw that was a problem for some at the forums so I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

Given Colin Watson's comment,

"I believe this was intentionally removed as part of the installer redesign, but design work may be open to re-evaluation in light of user feedback, so this bug might as well remain open ..."

And based on responses both at Launchpad and at the forums I believe it would be in our best interest to either restore that option or provide a definitive method to do so post-installation in the release notes.

I very much want Maverick to be as bug-free as possible :^)

I'm sure I'll live through it.

---

### Post by ranch hand on 2010-09-06
> **kansasnoob said:**
> That's the funniest thing I've read in days :lolflag:

But, my point was that I can overlook things and I see all of these issues as quite serious.

It's one of those situations where we can either be part of the solution or part of the problem :)

But my limited vision is one of the reasons I can't do things like use IRC, etc.

I do, always. appreciate your humor.
I saw that I was not on the grub non-install option bug.  Have no idea how that happened.  I did fix it.

The last bug I can't "me to" because I have never seen that part of the installer.  I only use the manual partitioning.  I need another drive as my 5th died last round and it was the only one that I could do things like "whole disk" and "side by side" installs on.

---

### Post by ranch hand on 2010-09-06
The box name bug is kind of interesting.  Does seem to be getting some attention.  Have to see how that turns out.

---

### Post by kansasnoob on 2010-09-06
> **ranch hand said:**
> I saw that I was not on the grub non-install option bug.  Have no idea how that happened.  I did fix it.

The last bug I can't "me to" because I have never seen that part of the installer.  I only use the manual partitioning.  I need another drive as my 5th died last round and it was the only one that I could do things like "whole disk" and "side by side" installs on.

You can now choose where to install grub, you just can't choose to NOT install grub. And we still don't know what those designations with a "-" mean.

If I had to make a choice now I'd just inmstall grub to "/" unless I had a "/boot" in which case I'd install to "/boot".

But I'd want to see that in official documentation :)

What "I'd do" and "what should be done" could be many degrees apart.

---

### Post by kansasnoob on 2010-09-06
This is exactly why you never give up! I received this response from SABDFL:

> I think there are two separate issues:

1. we need an effective way to rename a machine post-install.
2. we need to take a view on how important it is to expose the name during install, and how visible to make the option to change it.

If name conflicts are a problem, then [1] is just as important as [2],
since we can't put all our eggs in the basket of "getting it right at
install time".

I'm subscribing Michael Forrest, who's the designer responsible, for
comment on the rationale for having dropped it.

Mark

This is where others need to get involved.

I went down this road with the "non-interactive boot" and got nowhere because no one else followed through!

---

### Post by ranch hand on 2010-09-06
Those "-" entries are interesting to say the least.

I really wonder where they are coming from.   I am not real willing to try them to find out either.

On my test drive I can live with the option to install grub.  I can install to the second drive in the enclosure.  I can't boot from it anyway.  All my /home partitions are on that one.

On my other drives I really need to be able to not install grub.  Os-prober gets weird with custom  menus.  I get a real long generated menu because every OS is listed on every partition.  This gives over a hundred menu entries.  Eleven of the buggers work.  Just not real good at all.

I can boot to the new install with the existing menu entry for that partition from what ever OS is supposed to be on the MBR.  Now I have chroot in before leaving the Live Session and run install grub on any of my other OS' (they all have the same menu with a different background so I can tell them apart).

---

### Post by PGHammer on 2010-09-06
> **ronacc said:**
> I'm not sure what you mean by that but I can say that for me atleast it found  my earlier installs and added them to the boot menu and boots them ok .

What he means is that the auto-install of GRUB tends to install GRUB to the *opposing* hard drive (if the OS is using all the second hard drive, for example, GRUB winds up on the first).

This is extremely problematical if you have multiple drives (as opposed to multiple partitions).  I loathe that openSuSE pulls such stuff by default (I have to use a custom install to prevent it); but to have 'buntu pull that really stings.

The very reason I use multiple *drives* so I can choose to boot one operating system (instead of the other) and have minimal cross-pollination of one by the other, especially when testing.  A test OS shouldn't do stuff like that (yes; that includes Windows).

---

### Post by ranch hand on 2010-09-06
You do have the option of where to install grub in the latest versions of the new installer.  The only option missing is the option of not installing it.

You can even get, if you are lucky the option to install it on sdx-y.  What that "-" means is a mystery.  Maybe the same partition as y but in a parallel universe.   I am not trying it.

---

### Post by cariboo on 2010-09-06
I ran into that problem with openSUSE the other day, it would only let me install grub to the mbr of /dev/sdb. It was fine for me as I use Maverick's grub to control boot, but it was annoying. 

The other thing I found annoying was that PCLinuxOS, Fedora and openSUSE all still use grub-legacy by default.

---

### Post by ranch hand on 2010-09-06
And PCLOS and Mandriva.

---

### Post by ktp on 2010-09-06
> **ranch hand said:**
> The box name bug is kind of interesting.  Does seem to be getting some attention.  Have to see how that turns out.

me too..hopefully I can name by box at install time. =)

---

### Post by cariboo on 2010-09-06
I see [SADFL]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/14") has responded positively in the bug, so there should be some action on the problem.

---

### Post by ktp on 2010-09-06
yep saw that so waiting to see what the design team thinks and comes up with.  I am sure there was some thoughts behind it...so hoping to see the whole picture. =)

---

### Post by kansasnoob on 2010-09-07
Reviewing this list of bugs again:

[http://ubuntuforums.org/showpost.php?p=9813612&postcount=77](http://ubuntuforums.org/showpost.php?p=9813612&postcount=77)

I'm trying to decide what's truly serious, etc. and #3 is getting some love now since I brought it up at Ayatana. 

I think #1 can be worked around by installing grub to "/" or "/boot" if one exists, but that's purely my opinion.

And I guess #2 is mostly cosmetic, although not being able to resize/maximize the windows (particularly the advanced partitioning window) could, I think, cause some confusion.

So I think #4:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

is probably the most significant, and wondered what others thought about what I asked yesterday:

> Are my comments at that last bug complete enough?

Should I file a new bug report about confusing options being offered?

I'm curious what others think about that. I'd posted some screenshots:

[http://ubuntuforums.org/showpost.php?p=9799583&postcount=53](http://ubuntuforums.org/showpost.php?p=9799583&postcount=53)

[http://ubuntuforums.org/showpost.php?p=9799662&postcount=55](http://ubuntuforums.org/showpost.php?p=9799662&postcount=55)

Any help would be much appreciated :)

---

### Post by cariboo on 2010-09-07
Reading some of the comments on the mailing list and the bug report on the hostname bug, has me wondering if some of the devs actually live in the same world as we do, there was one work around suggest where the host name change be done at the start of the install.

> Advanced users can still set their own hostname by putting netcfg/get_hostname=ubuntupad on the live CD's kernel command line. To do this, press a key when you see the "keyboard = accessibility options" image, then select a language, press F6, followed by escape.

---

### Post by sgosnell on 2010-09-07
I wonder what percentage of the target audience is that advanced.  As a WAG, I'd say it approaches zero.

---

### Post by ranch hand on 2010-09-07
Wow.  Simplicity itself.  Why didn't we think of that?

---

### Post by ktp on 2010-09-07
> **cariboo907 said:**
> Reading some of the comments on the mailing list and the bug report on the hostname bug, has me wondering if some of the devs actually live in the same world as we do, there was one work around suggest where the host name change be done at the start of the install.

> **ranch hand said:**
> Wow.  Simplicity itself.  Why didn't we think of that?

I am lost for words...I guess I am not surprise since dev would try to find the easiest way out...at least that's my experience.

---

### Post by kansasnoob on 2010-09-08
I sort of had to laugh when I read this from Ivanka Majic:

> Looking at the design of the installer, it is very much geared around
this new user of Ubuntu. "Welcome", "Where are you?" , "About you"; the
slideshow elements are all things that You can do.

If we add another field (and I do like Randall's wording) we would have
to add another step on the 'About you' page? In fact, it could be argued
that the name of my computer doesn't belong on a page About Me in which
case we would be adding complete extra page.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31)

The new way:

[ATTACH]168865[/ATTACH]

The old way:

[http://members.iinet.net/%7Eherman546/p28/031_who-am-i.png](http://members.iinet.net/%7Eherman546/p28/031_who-am-i.png)

Why would we need an advanced tab or another page?

I further had to laugh at this:

> The process should feel safe and should only highlight risk when necessary (e.g. when data will be destroyed).

Obviously Ivanka hasn't seen this:

[http://ubuntuforums.org/showpost.php?p=9799583&postcount=53](http://ubuntuforums.org/showpost.php?p=9799583&postcount=53)

Or this:

[http://ubuntuforums.org/showpost.php?p=9799662&postcount=55](http://ubuntuforums.org/showpost.php?p=9799662&postcount=55)

I realize we're still in Beta but I anticipate a lot of confusion with the new ubiquity. And I can't help but wonder how many of the devs actually test this stuff in anything other than a VM?

We'll see what happens, I'm certainly trying my best at filing, and following up on, bugs.

---

### Post by MacUntu on 2010-09-08
Hilarious. If I would ask my mother (70) to fill out the old dialog she would pass with flying colors - and the only computers she knows are in her kitchen devices. IMO this is a big step backwards.

---

### Post by ranch hand on 2010-09-08
Yup, if you dumb it down enough only a genius can figure it out.

---

### Post by arpanaut on 2010-09-08
> **ranch hand said:**
> Yup, if you dumb it down enough only a genius can figure it out.

Exactly!
The conversation on this bug shows the difference between designer-think and engineer-think:

designer-> simple, pretty
engineer-> Yeah, but... what if?

A balance between the two needs to be found. for the sake of ALL users.

---

### Post by fedexnman on 2010-09-08
yup hate the new installer , i partitioned my 10.04 drive with gparted, clicked on install 10.10 side by side with other os , and it installed 10.10 over it and erased my 10.04, did microsoft make this new installer ? :-({|=

---

### Post by ktp on 2010-09-08
> **ranch hand said:**
> Yup, if you dumb it down enough only a genius can figure it out.

does that mean if I remember to put "netcfg/get_hostname=ubuntupad" to name my computer...it makes me a genius.  To bad I wouldn't remember that.

---

### Post by ranch hand on 2010-09-09
You just need to add that to the list of things you need to change to get the Disk to boot anyway.  If I were to do that it would be quite a long print out.

Great installer.  Great boot manager.  Great Wallpaper.  Everything is just great.

---

### Post by kansasnoob on 2010-09-09
> **fedexnman said:**
> yup hate the new installer , i partitioned my 10.04 drive with gparted, clicked on install 10.10 side by side with other os , and it installed 10.10 over it and erased my 10.04, did microsoft make this new installer ? :-({|=

You really need to report that!

I'd suggest here for now:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

You'll see in post #4 how I try to describe all of the other stuff going wrong. But it's worse than that I fear :(

You might need to file a new bug report explaining exactly what happened, but I can assure you that only complaining here will get nothing accomplished!

---

### Post by kansasnoob on 2010-09-09
> **ktp said:**
> does that mean if I remember to put "netcfg/get_hostname=ubuntupad" to name my computer...it makes me a genius.  To bad I wouldn't remember that.

Well I tried that today and it didn't work, or I did something wrong, I'm not sure.

I'm really trying to narrow this stuff down to what's important and what can wait for Natty, it's not easy!

I updated this one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

> 

First of all I apologize in advance for rudely subscribing Evan but I hope this ultimately saves him time.

I was doing some unrelated testing today and I notice the window sizes look much better, especially regarding the slideshow.

I'd say all of the window sizes are at least acceptable so I'm tempted to say we could close this bug report.

Perhaps though we should wait until at least the RC?


Was I right?

Next I reported this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/633768](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/633768)

> Doing some unrelated testing today I noticed that "ubiquity-slideshow-ubuntu 23" still shows f-spot whereas Maverick has transitioned shotwell.

While it's only cosmetic it might be something we should fix by Maverick final.

But from what Ivanka Majic says we should just live with it until the next UDS:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/31)

> 

The specification for the installer that was used at UDS can be found here: [http://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v](http://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v)

The spec describes the first Objective of the installer as: Make installation process quick with an engaging hand-off to the desktop.

It goes on to describe the Problem Definition as: The Ubuntu Live CD is the first experience many new users will have of Ubuntu. **[COLOR="Red"]The installation experience should be attractive and effortless to reassure new users that Ubuntu is the right choice.[/COLOR]** The process should feel safe and should only highlight risk when necessary (e.g. when data will be destroyed).

The document goes on to list 3 types of user to consider:
1. Users with no prior knowledge of Ubuntu or understanding of the nature of an operating system
2. Users who already know they want to install Ubuntu
3. Expert Ubuntu users who have very specific configuration requirements

In this context we can discuss this bug in 2 ways:

a) Is the design intent the right choice for us?

b) Given that the design intent has been agreed through an accepted process what do we do about the use-case presented?

I propose that a discussion around a) should be left for UDS (or similar decision making forum) as design intent is often a complex decision inviting technical, user and strategic goals to be represented and cannot be adequately explored in this forum. **[COLOR="Red"]Design intent is not a bug.[/COLOR]**

Which brings us to the use-case represented.

Looking at the design of the installer, it is very much geared around this new user of Ubuntu. "Welcome", "Where are you?" , "About you"; the slideshow elements are all things that You can do.

If we add another field (and I do like Randall's wording) we would have to add another step on the 'About you' page? In fact, it could be argued that the name of my computer doesn't belong on a page About Me in which case we would be adding complete extra page. This might not be a big deal but our intent has been described as creating an "Quick, Attractive and Effortless" install and I believe that we owe it to ourselves to fight the urge to add steps. Do we want to do that?

Providing an auto-generated bit of the name (as per Mark's suggestion) would just add an element of uniqueness that might be helpful if, let's say, someone installed an Ubuntu box somewhere where there were lots of Ubuntu machines and then they could share music and see how lovely it is to be part of ubuntu-land, it would also mean that if you were installing Ubuntu on a lot of machines you wouldn't end up with any repeated names on your network.

Now to the fact that there is no way to change the name of the machine. If that is a use-case we need to support, let's design and make the best way to do that.


**What happens when design intent reduces usability?**

I dunno :confused:

Yet, we catch hell here at the forums if we get too emotional discussing this stuff in order to figure out what to do next.

My list of "what to do next" includes finding someone that can represent actual "end-users" at UDS!

---

### Post by VMC on 2010-09-09
> **kansasnoob said:**
> ...

My list of "what to do next" includes finding someone that can represent actual "end-users" at UDS!
The best quote of the testing cycle!

Oddly enough Kubuntu's installer, using the same ubiquity as Ubuntu, has the ability to allow users to change computer name. The "not install" boot loader is also not available though.

---

### Post by kansasnoob on 2010-09-09
> **ranch hand said:**
> You just need to add that to the list of things you need to change to get the Disk to boot anyway.  If I were to do that it would be quite a long print out.

Great installer.  Great boot manager.  Great Wallpaper.  Everything is just great.

Well, I'm spending a lot of time on trying to get **installer** bugs fixed.

What's wrong with the **boot manager**? I think it's getting pretty darn great.

And, **Wallpaper**? Really? I could care less about wallpaper. I thought the big "poo-poo" over wallpaper was the biggest waste of energy I've ever seen!

How hard is it to change wallpaper? How often do you keep a default theme?

The installer is a different thing, just as grub2 was with Karmic! If actual usability suffers so does Ubuntu!

---

### Post by kansasnoob on 2010-09-09
@ VMC, I guess I'm going to have to subscribe Colin Watson to that thread to try and deal with **The "not install" boot loader is also not available though.**.

I've really been pushing things and I'm just an end user. I don't want to push too hard and end up being disregarded altogether in the future ;)

I've been trying very hard to prioritize these ubiquity bugs so we can minimize the ill results and I think this is the most serious:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

And I won't know until it's fixed if some of those confusing options change.

I do think that it should always be safe to install grub to "/" (or "/boot" if one exists) if NOT installing grub is still not an option by final.

---

### Post by sgosnell on 2010-09-09
I admit that text is a difficult medium for showing emotion, but I'm pretty sure I detected a little sarcasm in Ranch Hand's post.  Maybe more than a little.

---

### Post by ktp on 2010-09-09
> **kansasnoob said:**
> My list of "what to do next" includes finding someone that can represent actual "end-users" at UDS!

I love this one...lets hope you find someone. :D

---

### Post by kansasnoob on 2010-09-09
> **ktp said:**
> I love this one...lets hope you find someone. :D

I do think we need more "end-user" input in development. I'm not quite sure how to accomplish that. I'm the wrong guy for the job :D

Clearly there is somewhat of a communication problem when you look at Mark Shuttleworth's comment here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/14](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/14)

> 

I think there are two separate issues:

 1. we need an effective way to rename a machine post-install.
 2. we need to take a view on how important it is to expose the name during install, and how visible to make the option to change it.

If name conflicts are a problem, then [1] is just as important as [2], since we can't put all our eggs in the basket of "getting it right at install time".

I'm subscribing Michael Forrest, who's the designer responsible, for comment on the rationale for having dropped it.

Mark


IMHO why did we decide that it was OK to drop that option "post-install" quite a long time ago?

And why did we decide it was now OK to drop it from the installation menu?

Could it be because most devs work purely through VM's?

Should "in-house" testing involve more actual "hard installs"?

I'm just not sure. I do however find Ivanka Majic's comments troubling, particularly:

> **Design intent is not a bug.**

I tend to think if "design intent" reduces usability that is a bug!

That is however just my opinion :D

---

### Post by bennachie on 2010-09-09
@kansasnoob

You are not alone in your opinion. At least, for the moment, the Kubuntu installer still does the right thing. Name conflicts are a real possibility for those of us routinely accessing fairly large networks (I suppose that "john-laptop" is a marginally better option than "localhost.localdomain", but not by much).

---

### Post by ktp on 2010-09-09
> **kansasnoob said:**
> I tend to think if "design intent" reduces usability that is a bug!

That is however just my opinion :D

I think lots of people feel the same way.  "Design intent" is most likely, can be wrong, done to improve something.  If user, which the change was for, finds it not useful, then it's a "bug" in their mind.  

If you think about it, "bug" to end user is something that doesn't work as they would expect it...it doesn't matter if was design intent or not.  But that doesn't mean designer has to change it, but since someone "important" has said it needs change, let hope it happen...sooner (the better) or later. =)

---

### Post by kansasnoob on 2010-09-09
Lot's of changes poured through today:

> ubiquity (2.3.17) maverick; urgency=low

  [ Evan Dandrea ]
  * Fetch the translations for the release_notes_only and
    update_installer_only strings (LP: #629627).
  * Don't use the same name for the error method and GTK label
    (LP: #631046).
  * Re-use the valid username check from user-setup in the GTK UI
    (LP: #631046).
  * Do not cut off the text of the Try and Install buttons by setting
    their width to just the largest initial width of the two
    (LP: #629437).
  * Update the panel to use the new location for the panel background,
    and force a redraw when setting it.
  * If the username only contains non-alphanumeric characters, set the
    hostname to ubuntu-{laptop,desktop}.
  * Replace RELEASE with the release name in the KDE UI finished dialog
    (LP: #628964).
  * Do not look for a full path on non-paths when getting the default
    grub target.
  * Fix a crash when there are no disks present on the system
    (LP: #631766).
  * Don't let the user continue if there are no disks present, or if
    there isn't enough free space on any of them to install.
  * Fix UI bugs in the automatic partitioner page.  Better handle
    determining what the desired partitioning recipe is (LP: #630450).
  * Update the KDE partitioning UI to reflect changes to ubi-partman and
    partman-auto.
    - Use the already existent ubiquity variants of the d-i "Guided -" strings
      (LP: #628864).
    - Fix the automatic resize option failing to appear
      (LP: #628897, LP: #628815).
    - Use a combobox to select which disk to use on all options that support
      multiple disks, not just the "use entire disk" option.
  * Add notification area support in the panel.
  * Drop ia64 and sparc.
  * Run nm-applet in the ubiquity GTK session.

  [ Colin Watson ]
  * Factor out common /proc/mounts handling into a new
    ubiquity.misc.mount_info function.
  * Remove lpia architecture support.
  * Handle grub-efi when installing on amd64/efi or i386/efi
    subarchitectures (LP: #632642).

  [ Mario Limonciello ]
  * Adjust the fudge factor for showing languages on oem-config page
    due to the changes to the default window size being much bigger.
  * During oem-config's removal of ubiquity, remove other ubiquity
    related items that might have potentially still been on the system
    from a live-helper generated image.
  * Refactor mount_info to also report ro/rw, and let plugininstall
    key off that instead.
  * Set the panel indicators to show up on the right to match the rest
    of the desktop (LP: #632592)
  * Automatic update of included source packages: grub-installer
    1.55ubuntu3.

 -- Mario Limonciello <Mario_Limonciello@Dell.com>  Wed, 08 Sep 2010 14:43:59 -0500


Trying things in a VM it certainly looks better than the Beta, and given Mark Shuttleworth's opinion on the "host-name" issue I think this could work out OK :D

Given the fact that it's a complete "rework" of ubiquity there will be issues but from what I've seen the devs are really busting butt to get it right.

I think I'll back off for a bit. I remember working as a mechanic for decades and people would interrupt me while I was working. Every time that happened it delayed my progress.

We have until the 30th for the RC so I think we should chill out for a week or so.

---

### Post by kansasnoob on 2010-09-09
> **ktp said:**
> I think lots of people feel the same way.  "Design intent" is most likely, can be wrong, done to improve something.  If user, which the change was for, finds it not useful, then it's a "bug" in their mind.  

If you think about it, "bug" to end user is **[COLOR="Red"]something that doesn't work as they would expect it[/COLOR]**...it doesn't matter if was design intent or not.  But that doesn't mean designer has to change it, but since someone "important" has said it needs change, let hope it happen...sooner (the better) or later. =)

I'd say many times we make things "not work at all"! We dropped the option to rename our computers using a GUI around Intrepid or Jaunty, now we're trying to break it further by not allowing that option at installation.

At the same time we're professing to make things "simpler" for the noob and that's just often not true! Intent and result can be 180 degrees apart.

---

### Post by Reiger on 2010-09-09
> **kansasnoob said:**
> I do however find Ivanka Majic's comments troubling, particularly:

Frankly, I think her comments amount to a load of insubstantial waffle. Design intent not a bug? Perhaps, but it can certainly be misguided and wrong which this change clearly is an example of.

Elegant or not, advanced or not, naming things is the first thing any computer user learns how to do. And it is probably the only thing a noob computer user feels confident doing on the PC. Why on earth Ubuntu has to take that single piece of self-reinforcement away from them I don't know. Entire flipping file systems have been obsoleted by a demand for having &#8220;long&#8221; file names (as in: having control over what they're actually called rather than some truncated monstrosity).

EDIT: Also, things like this make me really happy to not use the Gnome flavour of Ubuntu. The KDE version may have its warts but at least its developers have so far had the sense to leave this in the installer...

---

### Post by cariboo on 2010-09-10
There is still at least on dev sticking up for use more *experienced* users. Scott Kitterman, keeps reminding some the others that not all of us use a gui all of the time.

---

### Post by BwackNinja on 2010-09-10
> **kansasnoob said:**
> I do think we need more "end-user" input in development. I'm not quite sure how to accomplish that. I'm the wrong guy for the job :D
...

The problem with adding a lot of end user input during the development cycle is that we would need to swap them out once in a while because they'd learn too much :P

---

### Post by cariboo on 2010-09-10
I think the design team is looking for end user input, look at this post by [SADFL]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/41")

---

### Post by kansasnoob on 2010-09-10
I'm sure glad I pushed that to Ayatana. Doing so got this a "Fix Committed" today!

I'm gonna' celebrate with a pizza :D

---

### Post by cariboo on 2010-09-10
I did an install of the daily build today, and was quite happy with the process, the slide show windows are all the correct size finally, the big thing that didn't work was wireless, The icon was in the top panel, and I could see my access points, but it didn't make an attempt to connect. There is also a page, where you are supposed to be able to connect to an access point, but that didn't show any, and because there was no network connection there was a message about trying to connect to a time server through the whole installation process. The skip button didn't work for this action either.

Another surprising thing was during the install of the nvidia restricted drivers, there was no need to run nvidia-xconfig. my monitor, an LG crt, was detected properly and an /etc/X11/xorg.conf file was created automagically

---

### Post by ronacc on 2010-09-10
It looks like from Marks the they are getting the message that maybe they got just a wee bit heavy handed with the dumbing down at least for this iteration , I wonder what they have in store to torture us with in Neutered Newt .

---

### Post by ktp on 2010-09-10
yep they did seem to dumb it down little to much...but the "iteration" is working fix it so that's good.  

I am sure there will be more fun in NN.

---

### Post by ktp on 2010-09-10
> **kansasnoob said:**
> I'm sure glad I pushed that to Ayatana. Doing so got this a "Fix Committed" today!

I'm gonna' celebrate with a pizza :D

nicely done...enjoy the pizza!!

---

### Post by crjackson on 2010-09-11
I guess it's time I get the daily download and install again to have a look see.

---

### Post by kansasnoob on 2010-09-11
The following two bugs are "fix committed" but the fixes have not yet been released:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

I'm dieing to see if the fix for the latter also helps the "confusing" options offered. I'd bet it'll make a difference.

---

### Post by cariboo on 2010-09-11
The final freeze is this coming Thursday, there's still time to get the fixes in.

---

### Post by kansasnoob on 2010-09-12
> **cariboo907 said:**
> The final freeze is this coming Thursday, there's still time to get the fixes in.

I should have made clear that I was addressing crjackson since he said:

> I guess it's time I get the daily download and install again to have a look see. 

Just so (s)he'd know that those two issues are only "fix committed", not yet "fix released" :)

Based on past experience I think the devs are very close to having this working pretty darn well :D

Of course that's largely based on my personal opinion so it should be taken with a grain of salt. I'm just amazed that they managed to pull this new ubiquity together so quickly, it was just released August 6th:

>   * Merge maverick-redesign branch.  Fingers crossed.
  * Automatic update of included source packages: clock-setup
    0.103ubuntu1.

 -- Evan Dandrea <evand@ubuntu.com>  Fri, 06 Aug 2010 14:15:17 -0400

I was very worried for a while ;)

I've always bragged about the simplicity of Ubuntu's live installer in comparison to others and I want to see it remain something I can still recommend as great.

---

### Post by cariboo on 2010-09-12
There has been a vast improvement in the installer since the beta release, and I have full confidence that most of the issues we've run into will be resolved by the RC release.

---

### Post by crjackson on 2010-09-12
> **kansasnoob said:**
> i should have made clear that i was addressing crjackson since he said:



Just so (s)he'd know that those two issues are only "fix committed", not yet "fix released" :)

  **_he_**  Thanks for the info.

> based on past experience i think the devs are very close to having this working pretty darn well :d 

---

### Post by kansasnoob on 2010-09-12
> **crjackson said:**
> **_he_**  Thanks for the info.

Hey, I caught heck once for assuming **he** so I now cover my bases :)

I really hate "to whom it may concern", but I'm human.

I've also caught heck if I use "OP" which only means "original poster", sometimes I just can't win for losing ;)

---

### Post by crjackson on 2010-09-12
> **kansasnoob said:**
> Hey, I caught heck once for assuming **he** so I now cover my bases :)

I really hate "to whom it may concern", but I'm human.

I've also caught heck if I use "OP" which only means "original poster", sometimes I just can't win for losing ;)

ha ha ha...  I'm not offended by any of them...  I was just passing info back to you.

How could anyone possibly be offended by OP?

---

### Post by ranch hand on 2010-09-12
Obvious Poop?

---

### Post by ktp on 2010-09-12
I knew that was coming...nicely done =)

---

### Post by Starks on 2010-09-12
Hostname configuration should be landing within the next daily or so.

---

### Post by crjackson on 2010-09-12
> **Starks said:**
> Hostname configuration should be landing within the next daily or so.

As the "Obvious Pooper" that's great news...  :)

---

### Post by crjackson on 2010-09-13
A fresh install of the daily build today reveals the fix isn't included just yet.  The installer still sucks swamp water.

---

### Post by ranch hand on 2010-09-14
> **crjackson said:**
> A fresh install of the daily build today reveals the fix isn't included just yet.  The installer still sucks swamp water.
Swamp water?  Sounds like an improvement to me.

---

### Post by crjackson on 2010-09-14
> **ranch hand said:**
> Swamp water?  Sounds like an improvement to me.

I was just keeping it digestible for the forum moderator.  It is what it is...

---

### Post by VMC on 2010-09-14
Careful guys. Your treading on thin ice, or is that shallow water.

---

### Post by sgosnell on 2010-09-14
Thin ice over very shallow water isn't so dangerous...

---

### Post by ktp on 2010-09-14
> **ranch hand said:**
> Swamp water?  Sounds like an improvement to me.

funny i was thinking the same thing...sorry just can't wait for the fix.

---

### Post by kansasnoob on 2010-09-15
> **crjackson said:**
> A fresh install of the daily build today reveals the fix isn't included just yet.  The installer still sucks swamp water.

Arrgh!

This is why I tried to explain that "Fix Committed" was not the same as "Fix Released"!

Things are moving in the right direction!

I can't guarantee that the new ubiquity will be perfect when 10.10 is released but I can assure you that everyone who's bothered to get involved have done everything possible to make it great!

Would you care to share your involvement at Launchpad? Maybe we could provide some helpful feedback :)

---

### Post by dannyboy79 on 2010-09-15
I personally don't see what the problem is. I just installed 10.10 beta on a Gateway T-1625 laptop and I always do manual partitioning anyways so I can control how big my home partition is and that swap is the second partition after root. So, apparently this installer that sucks swamp water doesn't affect me.
Everything booted up fine, recognized all hardware (wireless, sound, touchpad, etc etc) but i do need to research the webcam. Anyway, I love it and not sure what the fuss is as I will not be going back to read 11 pages of posts.

---

### Post by kansasnoob on 2010-09-15
> **dannyboy79 said:**
> I personally don't see what the problem is. I just installed 10.10 beta on a Gateway T-1625 laptop and I always do manual partitioning anyways so I can control how big my home partition is and that swap is the second partition after root. So, apparently this installer that sucks swamp water doesn't affect me.
Everything booted up fine, recognized all hardware (wireless, sound, touchpad, etc etc) but i do need to research the webcam. Anyway, I love it and not sure what the fuss is as I will not be going back to read 11 pages of posts.

Indeed, the manual (aka: advanced) part seems almost flawless. I think there should be some instruction about NOT installing grub if desired but I also think that's a minimal problem.

I'm discussing it:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033/comments/11](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/615033/comments/11)

There are at least 3 other ubiquity bugs that are "fix committed". I've followed dev for nearly 3 years and I can assure you that 99% of the time that status results in a "fix released"!

I can assure you that the devs are working very hard on this. That's why I waited to subscribe someone until I felt it was necessary.

If the devs had to answer every question presented to them they'd get nothing done ;)

---

### Post by crjackson on 2010-09-15
> **kansasnoob said:**
> Arrgh!

This is why I tried to explain that "Fix Committed" was not the same as "Fix Released"!

Arrgh!

And everyone understood your explanation as far as I know.  I was reinstalling for other reasons and noticed it still sucks so far as the daily build is concerned.  I'm not following it on launchpad because I know it's being worked on. It could have been fix released by now as far as I knew, but I didn't check the status before installing. The install itself told me the status. I was just noting that it still sucks high viscosity, contaminated H2O.

> **kansasnoob said:**
> Would you care to share your involvement at Launchpad? Maybe we could provide some helpful feedback :)

If I find something new to report I surly will.  Right now my complaints are the same as everyone else's.

---

### Post by crjackson on 2010-09-15
> **dannyboy79 said:**
> I personally don't see what the problem is. I just installed 10.10 beta on a Gateway T-1625 laptop and I always do manual partitioning.

Since you set your's up manually through the advanced install option you wouldn't see it.  I used that option too because I had no choice.

> **dannyboy79 said:**
> I love it and not sure what the fuss is as I will not be going back to read 11 pages of posts.

If you're not willing to read, then it's not surprising that you don't know what the fuss is.

---

### Post by DevHead on 2010-09-16
In the daily build (09/16/2010), I now see the option to enter in the computer/host name during the installation process. ):P

---

### Post by crjackson on 2010-09-16
> **DevHead said:**
> In the daily build (09/16/2010), I now see the option to enter in the computer/host name during the installation process. ):P

Sweet...  I'll have a look at it tonight.

---

### Post by cariboo on 2010-09-16
I just did an install with today's daily image, it looks like most of the problems have been fixed. One other thing I noticed, is that it doesn't default to auto login any more.

---

### Post by ranch hand on 2010-09-16
> **cariboo907 said:**
> I just did an install with today's daily image, it looks like most of the problems have been fixed. One other thing I noticed, is that it doesn't default to auto login any more.
That would be a big improvement.  That is a silly default.  You want that you can set it up easy enough.

---

### Post by ktp on 2010-09-16
> **cariboo907 said:**
> I just did an install with today's daily image, it looks like most of the problems have been fixed. One other thing I noticed, is that it doesn't default to auto login any more.

thanks for screenshots...things are looking better and better.  Going to test driver later.

I also think not defaulting to auto login is good thing...never understood that before.

---

### Post by crjackson on 2010-09-17
I'd like to check it out but this build won't even load on my testing laptop.

---

### Post by DevHead on 2010-09-17
> **crjackson said:**
> I'd like to check it out but this build won't even load on my testing laptop.

This is the version that I'm running.
[http://cdimage.ubuntu.com/daily-live/20100916.1/](http://cdimage.ubuntu.com/daily-live/20100916.1/)


I think this version is the "broken" one.  Installs fine but won't boot.
[http://cdimage.ubuntu.com/daily-live/20100916/](http://cdimage.ubuntu.com/daily-live/20100916/)

---

### Post by kansasnoob on 2010-09-17
I didn't have a chance to check out the ubiquity updates yesterday but the 10-17 daily seems not to like my Intel graphics. My Hanns-G LCD just belches with a "Input Signal Out of Range", and using "nomodeset" still will not let me "startx".

I may fiddle a bit in a VM later :)

---

### Post by cariboo on 2010-09-17
There were quite a few ubiquity bug fixes released today. Have a look [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/46")

---

### Post by arpanaut on 2010-09-17
That is impressive! =D>
Now to see if it all works. :biggrin:

---

### Post by Arrowstar on 2010-09-17
I just installed today's Daily Build on a VMWare Player VM and I was pleasantly surprised how easy it was.  All the major bugs I've noticed before are gone, and the installer even recognized that I was installing on a virtual machine.  Much improved! :)

---

### Post by crjackson on 2010-09-17
> **Arrowstar said:**
> I just installed today's Daily Build on a VMWare Player VM and I was pleasantly surprised how easy it was.  All the major bugs I've noticed before are gone, and the installer even recognized that I was installing on a virtual machine.  Much improved! :)

Sadly, testing has come to a screeching halt for me.  Todays and the last few days builds won't run on my lappy due to graphical issues (ATI). The beta works until I get updates then it's dead.

---

### Post by kansasnoob on 2010-09-17
> **crjackson said:**
> Sadly, testing has come to a screeching halt for me.  Todays and the last few days builds won't run on my lappy due to graphical issues (ATI). The beta works until I get updates then it's dead.

I'm stuck too :(

I tried my old VIA P4M800 box and today's daily won't run on it either.

I even tried an old Diamond Stealth card in this Intel machine and it was a no-go!

In a VM on this Intel machine I just get a totally garbled screen. If it's not better by Monday or Tuesday I'll examine closer.

---

### Post by kansasnoob on 2010-09-17
Oh, just FYI, I can still run a fully updated Maverick on my Intel machine so it's not going to be a huge problem. I'm thinking some updates just need to get caught up with others.

---

### Post by VMC on 2010-09-17
Oddly,  using todays daily-live, Ubuntu worked perfectly, but Kubuntu daily-live doesn't. All about the video. In my case its nvidia. 

It "bounces" from the kde startup picture back again to startup..endlessly. I'm sure a of the current nvidia.run would make it work, but unlike Ubuntu, there's a ton of tools that need to be installed.

I'll wait a couple of days and see the situation improves.

Also todays daily-live for Kubuntu was the largest of any. It has been Ubuntu with huge increases. Zsync'ing Kubuntu, I needed to get 30% more new data.

---

### Post by kansasnoob on 2010-09-18
Well, today it'll run in a VM but still not on my actual hardware, so I can't really get a good idea about this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/626299)

Specifically the options offered after selecting to use the entire disc or auto-resize, but the rest of it's looking pretty darn great IMHO :)

Today I notice the non-interactive boot emblems don't even show up, but if you press enter as soon the system/BIOS screen passes it does display the boot options. However pressing an arrow key just causes it to boot as though you'd pressed Enter.

No biggy, I'd bet something needs to get caught up in xorg. I'm always amazed at how the devs pull this all together. 

OTOH my installed Maverick seems quite stable other than a few minor quirks.

---

### Post by ranch hand on 2010-09-18
> **kansasnoob said:**
>  Today I notice the non-interactive boot emblems don't even show up, but if you press enter as soon the system/BIOS screen passes it does display the boot options. However pressing an arrow key just causes it to boot as though you'd pressed Enter.
 OMG NO, Keyboardman is gone!?  Please say it ain't so.

---

### Post by VMC on 2010-09-18
> **ranch hand said:**
> OMG NO, Keyboardman is gone!?  Please say it ain't so.

Ok. It ain't so.

At least for me it isn't. Using todays ISO, I get my two friends.

---

### Post by crjackson on 2010-09-18
As usual the ISO won't work on my machine so I can't test it.

---

### Post by kansasnoob on 2010-09-19
> **VMC said:**
> Ok. It ain't so.

At least for me it isn't. Using todays ISO, I get my two friends.

Glad you said something. I paid closer attention using VirtualBox and they were there, tried booting the Live CD and they were not.

Decided to try a new burn and there they are :P

CD passed the integrity test but still doesn't like my Intel graphics :(

After another cup of coffee or two I think I'll try it in verbose mode and see if I can tell what's up.

But I should know better than to assume each and every CD gets burned correctly. That's probably my first bad burn out of about 140 discs, but anything can happen :)

---

### Post by kansasnoob on 2010-09-19
> **crjackson said:**
> As usual the ISO won't work on my machine so I can't test it.

I'm thinking you have Intel graphics too, eh?

Mine is 82945G/GZ which works great on my installed Maverick but it's a no-go on the Live CD right now.

---

### Post by crjackson on 2010-09-19
> **kansasnoob said:**
> I'm thinking you have Intel graphics too, eh?

Mine is 82945G/GZ which works great on my installed Maverick but it's a no-go on the Live CD right now.

eMachines M6809
ATI Mobility RADEON 9600 with 64MB Video RAM
AMD Athlon 64 Mobile (2 GHz)
1.25 GB Memory

I'm trying to remember which version of Ubuntu was the last to support the proprietary catalyst driver.  I think it was 8.10.  I'm thinking of going back to that version so I can get some performance out of this machine again.

I had high hopes of putting Maverick on all of my systems but that hope is dwindling.

Two of my other laptops have intel video.  Last I checked they worked fine.  I'll check at least one of them out later tonight and let you know.

---

### Post by kansasnoob on 2010-09-22
> **crjackson said:**
> eMachines M6809
ATI Mobility RADEON 9600 with 64MB Video RAM
AMD Athlon 64 Mobile (2 GHz)
1.25 GB Memory

I'm trying to remember which version of Ubuntu was the last to support the proprietary catalyst driver.  I think it was 8.10.  I'm thinking of going back to that version so I can get some performance out of this machine again.

I had high hopes of putting Maverick on all of my systems but that hope is dwindling.

Two of my other laptops have intel video.  Last I checked they worked fine.  I'll check at least one of them out later tonight and let you know.

Sadly 8.10 is no longer supported. Hardy is good for several months yet though.

Sorry to take so long responding, life has just been a nightmare here :)

I want to get a real look at the new ubiquity but I've only been able to do so in a VM which doesn't tell me much about partitioning, etc.

Have you ever looked into xorg-edgers?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

It saved my bacon on my old VIA hardware once.

---

### Post by crjackson on 2010-09-22
> **kansasnoob said:**
> Sadly 8.10 is no longer supported. Hardy is good for several months yet though.

Sorry to take so long responding, life has just been a nightmare here :)

I want to get a real look at the new ubiquity but I've only been able to do so in a VM which doesn't tell me much about partitioning, etc.

Have you ever looked into xorg-edgers?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

It saved my bacon on my old VIA hardware once.
I've tried that repo and it doesn't help with this system.  It seems that nothing after the official BETA download without updates with work on this machine.  It works fine but once updates are applied it's broke.  Daily build won't work at all.  It's just like the BETA+Updates.

---

### Post by kansasnoob on 2010-09-22
My Intel graphics seem to have gone the same way with the Live CD but I do have a perfectly running Maverick that started with the toolchain upload on May 22nd.

I'm looking into sorting it out:

[http://ubuntuforums.org/showthread.php?t=1579475](http://ubuntuforums.org/showthread.php?t=1579475)

I'd bet that sorting out my Intel graphics problem will be easier than what you have to deal with. I've never had ATI graphics so I'm useless to you in that regard :(

---

### Post by kansasnoob on 2010-10-06
@ crjackson,

Who'd have thought that we were experiencing the same bug given the vast difference in hardware :confused:

Anyway that one's out of the way now, but I ran through some installation scenarios this AM and I think the new ubiquity is down to three .......... errm .......... **design changes** that I'm not so sure about. I'll begin with what I consider the least important:

#1: There is no option to NOT install grub, or I'm not seeing it, but I think it should always be safe to install grub to the new OS's "/" (or "/boot" if one exists) even if not chain-loading.

#2: The installer windows still can not be maximized or otherwise resized, only closed or minimized. I suffer from very limited vision and I can get by with it, but it was nicer to be able to maximize the windows :)

#3: I wonder how confusing the "Entire Disc" and Entire Partition" options being offered after selecting the initial "side by side" or "entire disc" options will be to new Windows dual-booters? While it's not a big deal for me, I always try to wear my "noob-shoes" when I'm testing.

I'd honestly be reluctant to recommend anything but "manual partitioning" to anyone with more than one existing partition. That may not be a bad idea actually because I tend to believe that Vista and Win7 should be resized using only Win's own tools.

Regardless I don't think any of these are "bugs" but rather design changes and I'm not sure how best to address these issues, or if it's even worth my time. It sort of depends how other end users feel about it :)

---

### Post by dannyboy79 on 2010-10-06
> **crjackson said:**
> eMachines M6809
ATI Mobility RADEON 9600 with 64MB Video RAM
AMD Athlon 64 Mobile (2 GHz)
1.25 GB Memory

I'm trying to remember which version of Ubuntu was the last to support the proprietary catalyst driver.  I think it was 8.10.  I'm thinking of going back to that version so I can get some performance out of this machine again.

I had high hopes of putting Maverick on all of my systems but that hope is dwindling.

Two of my other laptops have intel video.  Last I checked they worked fine.  I'll check at least one of them out later tonight and let you know.the release canidate maverick meerkat works fine on a live usb install with my ATI AIW 9800 Pro. I didn't check compiz or to see if 3d direct rendering was enabled but whatever the default graphics module that was loaded works just fine meaning i get to the desktop and everything looks sharp.

Just an FYI.

---

### Post by cariboo on 2010-10-06
> #1: There is no option to NOT install grub, or I'm not seeing it, but I think it should always be safe to install grub to the new OS's "/" (or "/boot" if one exists) even if not chain-loading.

This is only an issue for experienced users, as most new users will only have at the most Windows and Ubuntu installed. I don't see a lot of them using chain-loading. This really only comes up when manually partitioning, as there isn't a choice when using the automagic partitioner.

I feel it is much safer to not give the new user a choice on where to install grub when using automatic partitioning, as we saw in the last release, there were many new users installing grub on their windows partition and borking their windows install.

To me this seems to be a very sane choice. Us more experienced users know enough, that we can decide ourselves where to install grub. If we don't want that particular installs grub to take over the system, we know not to install it to the mbr of the first hard drive.

As for your other concerns, I do agree the automatic partitioner does seem a bit confusing to use, but I wonder how it looks to a truly new user that has never partitioned a hard drive before.

> #2: The installer windows still can not be maximized or otherwise resized, only closed or minimized. I suffer from very limited vision and I can get by with it, but it was nicer to be able to maximize the windows

I'll have to look, but I don't think the previous installer window was re-sizable either, I do remember that when starting the install in safe-graphics mode, the window was always to big for the screen, and some guessing with the tab key was needed.

I would imagine that now that the Live CD is doing a better job of detecting graphics, that this should be a concern, as all of us are not getting any younger.

---

### Post by kansasnoob on 2010-10-06
Sorry but I'm borrowing some bandwidth to post a screenshot that I don't seem to be able to save to my USB drive:

[ATTACH]171464[/ATTACH]

As I've said before, I'm visually impaired so I do what I must :)

---

### Post by kansasnoob on 2010-10-06
Wow! Shootin' in the dark and no spelling errors :)

I'm sorry to be a pain :)

---

### Post by kansasnoob on 2010-10-06
Borrowing more bandwidth :)

[ATTACH]171476[/ATTACH]

Trust me, it's important :)

---

### Post by kansasnoob on 2010-10-06
Another because I must:

[ATTACH]171480[/ATTACH]

I can usually save these to USB but not with this Live CD.

---

### Post by Uncle Spellbinder on 2010-10-06
Wow. Just got the RC and was going to install. With 10.4, I  would click "use unallocated space" > "Install" > Done. Or "Install alongside Windows" > Use slider to determine space for Ubuntu > "Install" > Done. None of that seems available anymore. FAR more complicated than it should be. This is a major step backwards, in my opinion.

---

### Post by kansasnoob on 2010-10-06
> **Uncle Spellbinder said:**
> Wow. Just got the RC and was going to install. With 10.4, I  would click "use unallocated space" > "Install" > Done. Or "Install alongside Windows" > Use slider to determine space for Ubuntu > "Install" > Done. None of that seems available anymore. FAR more complicated than it should be. This is a major step backwards, in my opinion.

Actually I don't think so .......... in the long run.

I hated it at first but I do see some advantages, be that as it may I need to try and file one more bug report before I drop :)

---

### Post by kansasnoob on 2010-10-07
I actually repeated some testing this AM, since it's always good to try and reproduce *bugs*, and I decided this was invalid:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/656023](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/656023)

The behavior is different but just being different doesn't make it a bug. There probably is a valid reason for the installer automatically unmounting a flash drive. I don't currently have a regular USB hard drive that I can test with, must buy another case for an old IDE :(

Of course it's never possible for one person to test every possible scenario, but I'm really left with only one serious concern:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Otherwise my other complaints are really a matter of nit-picking :)

Like I'd prefer being able to maximize the installer windows, there is no option to NOT install grub, and there is no option to change where grub will be installed if using the "entire disc" or "auto-resize" options.

One thing I was very impressed with was being able to easily select which drive to install to if using the "entire disc" option. Although IMHO it would also be nice to be able to also select which drives mbr to install grub on at the same time.

I suspect someone will have to get involved at the design team level to effect any big changes in ubiquity for Natty, but not me. Regardless I think the devs did a great job pulling the new ubiquity together so quickly :)

---

### Post by kansasnoob on 2010-10-07
Update here:

[http://ubuntuforums.org/showpost.php?p=9937384&postcount=10](http://ubuntuforums.org/showpost.php?p=9937384&postcount=10)

Not so good :(

I hope to see crjackson again soon.

---

### Post by crjackson on 2010-10-07
> **kansasnoob said:**
> Update here:

[http://ubuntuforums.org/showpost.php?p=9937384&postcount=10](http://ubuntuforums.org/showpost.php?p=9937384&postcount=10)

Not so good :(

I hope to see crjackson again soon.

I check every couple of days. I can't test, I'm in the hospital on my back.

---

### Post by ktp on 2010-10-07
> **crjackson said:**
> I check every couple of days. I can't test, I'm in the hospital on my back.

health first then...best wishes.

---

### Post by kansasnoob on 2010-10-07
> **crjackson said:**
> I check every couple of days. I can't test, I'm in the hospital on my back.

I'd seen over at your Launchpad bug you had to have surgery. Just get well, we'll be here when you get back.

---


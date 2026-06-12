---
title: "Mythbuntu 8.04"
date: 2008-01-28
forum: Mythbuntu
---

### Post by twkisner on 2008-01-28
So, I noticed the other day there is a Mythbuntu 8.04 Alpha 1 floating around.

Has anyone tried it?

Also, I noticed one of the Mythtv devs "unofficially" stuck his neck out and said .21 will be released before March -- and I saw SuperM mention that he would switch the Hardy release over the the trunk version in preparation for .21 to be included in Hardy (and thus Mythbutu 8.04).

So, is anyone running this?  I know it's alpha and we are months away from release, but I was wondering how stable it is?  I know I could goto the trunk builds on Gutsy, but I was thinking I could skip that and go straight to Hardy...

.21 is supposed to have DVB multirec in it, which would enable me to do + a couple of minutes before/after even on back to back recordings. (I seemed to be plauged lately with my clock running slow despite using NTP).

---

### Post by ubnewbie2 on 2008-01-28
> **twkisner said:**
> 

.21 is supposed to have DVB multirec in it, which would enable me to do + a couple of minutes before/after even on back to back recordings. (I seemed to be plauged lately with my clock running slow despite using NTP).

Even having the clock accurate wouldn't help here as show's invariable go over time  :(

Things I'd like to see in the next release are

1. storage groups, so LVM's aren't required
2. transcode that preserves 5.1 channels
3. Multirecording from DVB cards
4. nVidia drivers that aren't buggy
5. eliminate mythweb's ability to crash the backend
6. multiple delete on recordings that don't lock up the UI

Just a personal wishlist :)

---

### Post by Weidbrewer on 2008-01-29
> **ubnewbie2 said:**
> 
Just a personal wishlist :)

Mine:  

[1] Short-cut keys that work.
[2] Sound/video quality on par with TVTime.

[2] is the only one I'm really concerned with.

---

### Post by tgm4883 on 2008-01-29
> **ubnewbie2 said:**
> Even having the clock accurate wouldn't help here as show's invariable go over time  :(

Things I'd like to see in the next release are

1. storage groups, so LVM's aren't required
2. transcode that preserves 5.1 channels
3. Multirecording from DVB cards
4. nVidia drivers that aren't buggy
5. eliminate mythweb's ability to crash the backend
6. multiple delete on recordings that don't lock up the UI

Just a personal wishlist :)

> **Weidbrewer said:**
> Mine:  

[1] Short-cut keys that work.
[2] Sound/video quality on par with TVTime.

[2] is the only one I'm really concerned with.

You know, a really good place for these would be on launchpad under either blueprints or bugs

---

### Post by twkisner on 2008-01-29
> **ubnewbie2 said:**
> Even having the clock accurate wouldn't help here as show's invariable go over time  :(



Sure, I can make it record +5 minutes before and after every show (even back to back recordings) without using another tuner (I already have 3).  That way, I can live if the clock (or the TV station/Network) drifts a little.  But your right a sports event that delays everything 10 minutes will still mess stuff up.

> **ubnewbie2 said:**
> 

Things I'd like to see in the next release are

1. storage groups, so LVM's aren't required
2. transcode that preserves 5.1 channels
3. Multirecording from DVB cards
4. nVidia drivers that aren't buggy
5. eliminate mythweb's ability to crash the backend
6. multiple delete on recordings that don't lock up the UI

Just a personal wishlist :)


I know that storage groups (item number 1) is in there.  Also, as I already mentioned multirec on DVB cards (item number 3) is in there.  As far as number 4, the mythtv team doesn't have any control over that.

I don't know about the rest, but you can look at:

[http://mythtv.org/wiki/index.php/Release_Notes_-_0.21](http://mythtv.org/wiki/index.php/Release_Notes_-_0.21)

Mabe you will be pleasantly surprised.

---

### Post by stdPikachu on 2008-01-29
> **ubnewbie2 said:**
> 6. multiple delete on recordings that don't lock up the UI

I even get lockups when deleting a single recording; for me this is Myth's biggest UI problem is that it locks all over the place - but deleting files via the TV is my most irritating one, even on a JFS filesystem (by far the fastest for large files IME).

---

### Post by ubnewbie2 on 2008-01-29
> **stdPikachu said:**
> I even get lockups when deleting a single recording; for me this is Myth's biggest UI problem is that it locks all over the place - but deleting files via the TV is my most irritating one, even on a JFS filesystem (by far the fastest for large files IME).


From my reading, it's as much to do with the fact that it needs to run a complete reschedule after every delete, and not the file system.  The slow delete feature doesn't help either.

---

### Post by stdPikachu on 2008-01-29
I did wonder what was chomping the CPU on each delete. Not sure why it can't just add them to a "to be deleted..." queue and reschedule in the background, but then I'm not a mythtv coder...

---

### Post by ubnewbie2 on 2008-01-29
> **stdPikachu said:**
> I did wonder what was chomping the CPU on each delete. Not sure why it can't just add them to a "to be deleted..." queue and reschedule in the background, but then I'm not a mythtv coder...

It's probably to do with the "delete and allow rerecord".  If it is deleted, but not rescheduled until some time later, it's possible a rerecord will be missed.

---

### Post by stdPikachu on 2008-01-29
This is just for plain deletes, I rarely do re-records. In any case, I don't think the UI should lock waiting for the DB or the filesystem. But that's just me being picky :)

---

### Post by newlinux on 2008-01-29
> **stdPikachu said:**
> I even get lockups when deleting a single recording; for me this is Myth's biggest UI problem is that it locks all over the place - but deleting files via the TV is my most irritating one, even on a JFS filesystem (by far the fastest for large files IME).

Hmmm, something else might be going on with your system. For me (using XFS) deletions are pretty much instantaneous (The space is completely available right after I delete it) with no lockup of the UI.

---

### Post by twkisner on 2008-01-29
> **newlinux said:**
> Hmmm, something else might be going on with your system. For me (using XFS) deletions are pretty much instantaneous (The space is completely available right after I delete it) with no lockup of the UI.

To contribute to my own thread being hijacked:)

Ditto, I don't have that problem, even when I delete huge muti hour (12 gig plus) HD recordings it is instantanious in the UI.  I use XFS as well (and recordings are on a seperate drive than the OS and Sql, if that matters...).

I guess no one is brave enough here to have given Mythbuntu 8.04 Alpha a spin?

---

### Post by stdPikachu on 2008-01-29
Might just be a hangover of br0ked gentoo then, which my master backend still runs (going to take a while to get to the stage where I can replicate the same functionality in ubuntu). But even so, the speed of the filesystem shouldn't have any effect on the UI.

Thought it might have something to do with the number of recordings I have (1200-odd, about a terabytes worth) but will have to wait until I can get a handle on the code.

---

### Post by newlinux on 2008-01-29
> **twkisner said:**
> To contribute to my own thread being hijacked:)

Ditto, I don't have that problem, even when I delete huge muti hour (12 gig plus) HD recordings it is instantanious in the UI.  I use XFS as well (and recordings are on a seperate drive than the OS and Sql, if that matters...).

I guess no one is brave enough here to have given Mythbuntu 8.04 Alpha a spin?

Sorry about the hijack! :) I am completely chicken. I'm not even using mythbuntu (my systems are edgy and feisty - if it ain't broke or there isn't a must have feature...). I've done a good amount of customizing myth, and with 3 backends and 5 frontends that have been working great for over a year... I ain't messing with it.

> **stdPikachu said:**
> Might just be a hangover of br0ked gentoo then, which my master backend still runs (going to take a while to get to the stage where I can replicate the same functionality in ubuntu). But even so, the speed of the filesystem shouldn't have any effect on the UI.

Thought it might have something to do with the number of recordings I have (1200-odd, about a terabytes worth) but will have to wait until I can get a handle on the code.

I've got over a Terabyte as well (although spread across 3 different machines). So many variables. Good luck. JFS should be quick. Wonder if there is something in the logs that might explain --- OKAY, I'm not hijacking anymore :).

---

### Post by superm1 on 2008-01-29
I probably don't count, but I am running a frontend with it.  My old gutsy based netboot mythbuntu frontend got messed up when my router died, so I set up mythbuntu 8.04 alpha 1 on that machine instead.  Additionally, I run hardy on my development laptop (and consequently all the mythbuntu stuff is on there).

0.21 builds aren't included yet, but will be within the next two weeks.

The most significant things you will see different are stability related, and lirc related.  See a few snapshots of the new mcc pages here: [http://mythbuntu.org/image/tid/8](http://mythbuntu.org/image/tid/8)

The installer and mcc should both be more robust, so if you filed any bugs against either for gutsy, you shouldn't run into them on this.

---

### Post by stdPikachu on 2008-01-29
Heh, there's never the info I want in the logs :D We'll see once I get my setup ported over to mythbuntu (although probably going to go kubuntu on my master backend and then just install the mythbuntu bits over the top).

Is Myth 0.21 planned for inclusion in Hardy? I'm working on the assumption that it'd be using a different protocol than 0.20 which was why I was reluctant to commit to giving the beta a spin (although it's currently using 0.20 too). Might set it up in a VM if I have the time as I'm reluctant to add any further breakage to my creaking master system as I'm keen to see what changes have been made to the running config utils (difficult to experiment with those on a current system) since, as some of you may have read, I'm interested in getting involved in the coding if I turn out to be good enough at it :) Is it too late to nominate my OSD-of-choice, [MythTVMediaCentre](http://www.radixpub.com/vir/portfolio/mtvmc/), for inclusion? Since mythtv-themes doesn't seem to be a mythbuntu package, do I need to bug this further up?

So many questions, so little etiquette...!

---

### Post by superm1 on 2008-01-29
> **stdPikachu said:**
> Heh, there's never the info I want in the logs :D We'll see once I get my setup ported over to mythbuntu (although probably going to go kubuntu on my master backend and then just install the mythbuntu bits over the top).

Is Myth 0.21 planned for inclusion in Hardy? I'm working on the assumption that it'd be using a different protocol than 0.20 which was why I was reluctant to commit to giving the beta a spin (although it's currently using 0.20 too). 

Yeah your safe doing this right now.  We are planning 0.21 for hardy, so hopefully everything gets sorted out in time.

> 
Might set it up in a VM if I have the time as I'm reluctant to add any further breakage to my creaking master system as I'm keen to see what changes have been made to the running config utils (difficult to experiment with those on a current system) since, as some of you may have read, I'm interested in getting involved in the coding if I turn out to be good enough at it :) Is it too late to nominate my OSD-of-choice, [MythTVMediaCentre]("http://www.radixpub.com/vir/portfolio/mtvmc/"), for inclusion? Since mythtv-themes doesn't seem to be a mythbuntu package, do I need to bug this further up?

Its a wii bit late for this now.  File a bug against mythbuntu to include it and it can show up in the future.

Here's the themes coming along:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mythtv-theme&searchon=names&subword=1&version=hardy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mythtv-theme&searchon=names&subword=1&version=hardy&release=all)

---

### Post by twkisner on 2008-01-30
> **superm1 said:**
> I probably don't count, but I am running a frontend with it.  My old gutsy based netboot mythbuntu frontend got messed up when my router died, so I set up mythbuntu 8.04 alpha 1 on that machine instead.  Additionally, I run hardy on my development laptop (and consequently all the mythbuntu stuff is on there).

0.21 builds aren't included yet, but will be within the next two weeks.

The most significant things you will see different are stability related, and lirc related.  See a few snapshots of the new mcc pages here: [http://mythbuntu.org/image/tid/8](http://mythbuntu.org/image/tid/8)

The installer and mcc should both be more robust, so if you filed any bugs against either for gutsy, you shouldn't run into them on this.

You *do* definately count.  Will you announce when you include .21 in 8.04 ?  I think I can overcome any Alpha bugginess to get it installed, as long as most important stuff is resonably functional I'm willing to give it a go.  I'd rather start with a clean install with .21 than upgrade .20->.21, although that's probably not that big of a deal.

I have to say the Mythtv devs have really streamlined .20+fixes.  My box runs far better than it did just 6 months ago (CPU utilization is *way* down for HD content, and the frontend loads in a fraction of the time that it used to).  I think those were all backport fixes from the .21 branch, so with Multirec and storage groups .21 looks like it's going to be a really nice release....

---

### Post by superm1 on 2008-01-30
As much as I'm sure a lot of people will prefer to do a backup of 0.20 stuff and then a clean 0.21 install, it will really be a lot better if the upgrade can be at least tested. 

This is always something very undertested by folks, so catching any upgrade bugs early off the bat is very important.

For this exact reason, I've got an old dapper backend sitting around that I'm going to upgrade to Hardy once this is ready.

---

### Post by twkisner on 2008-01-30
> **superm1 said:**
> As much as I'm sure a lot of people will prefer to do a backup of 0.20 stuff and then a clean 0.21 install, it will really be a lot better if the upgrade can be at least tested. 

This is always something very undertested by folks, so catching any upgrade bugs early off the bat is very important.

For this exact reason, I've got an old dapper backend sitting around that I'm going to upgrade to Hardy once this is ready.

Personally I have no problem tring an upgrade, if you need testers.  Just let me know when .21 gets rolled into the Mythbuntu 8.04 Alpha and I will give upgrading a shot on my system.  If it blows up I can always re-install.  My box is running top notch right now, and I don't think there is any garbage in sql database so I don't *need* to go with a clean install.

---

### Post by superm1 on 2008-02-09
Okay, Hardy now has all the myth apps (and related apps) set for 0.21/trunk.  If you upgrade now, you can take a roll with trunk and see how things are working for you.

A new alpha disk (including these builds) will shortly follow.

---

### Post by kansei on 2008-02-10
very tempting. I may install hardy on my primary frontend and then the mythbuntu packages :)

all my other frontends are debian so it's no help :P

time will tell if this passes the roommate factor.. at least they're geeks as well, not hard to please like a wife haha.

---

### Post by Gourgi on 2008-02-11
i just upgraded my regular hardy installation to mythbuntu through synaptic :) 
let's see now ...

---

### Post by Ubeast on 2008-02-13
> **superm1 said:**
> Okay, Hardy now has all the myth apps (and related apps) set for 0.21/trunk.  If you upgrade now, you can take a roll with trunk and see how things are working for you.

A new alpha disk (including these builds) will shortly follow.

Nice :) 

Where can we find download links to the alpha disks? The only place I've found is this one:

[Linuxtracker.org]("http://linuxtracker.org/index.php?page=torrent-details&id=98afa9060d428f55e34e2e5e767d7aea8fb51a43")

---

### Post by superm1 on 2008-02-15
Please see the sticky in the forums.  They are available via it.

---

### Post by Nikas on 2008-02-16
I'm using 7.10 with weekly trunk builds. Can i upgrade and keep my weekly trunks? :)

---

### Post by superm1 on 2008-02-16
All builds are happening in the archive for 8.04, there is no point to keeping the weekly trunk builds at this point when you upgrade (actually atm the builds in the archive are newer than the weekly trunks too)

---

### Post by Nikas on 2008-02-16
Ok.

I'm upgrading now.
Got "Warning: could not initiate dbus" in the terminal when i started the upgrade but it seems to be fine.

Edit:
VNC no longer work. I can get the screen to show but when i click on something or if i press any button the session ends. This happens on my two upgraded computers...

---

### Post by superm1 on 2008-02-16
> **Nikas said:**
> Ok.

I'm upgrading now.
Got "Warning: could not initiate dbus" in the terminal when i started the upgrade but it seems to be fine.

Edit:
VNC no longer work. I can get the screen to show but when i click on something or if i press any button the session ends. This happens on my two upgraded computers...
Yeah the VNC is a big problem.  I'm not sure yet how we're going to approach it - RealVNC is broke across the board for all the new distros.

Also, you are going to run into needing this:
[https://edge.launchpad.net/~mythbuntu/+archive?field.name_filter=upnp&field.status_filter=published](https://edge.launchpad.net/~mythbuntu/+archive?field.name_filter=upnp&field.status_filter=published)

It's in NEW, but hasn't cleared into the archive yet.

---

### Post by Nikas on 2008-02-16
Ok. Thanks!

Is the apt-key the same for the hardy weekly repositry as for the weekly gutsy repositry?

I'm trying to install the themes from Mythbuntucc but it keeps crashing. Should i send this report that is coming up?

---

### Post by superm1 on 2008-02-16
Go ahead and file anything you run into.  At very worst, it's solved and the notes will be added to the bug report.  Anything that is caught is important to get fixed :)

---

### Post by Nikas on 2008-02-16
Ok. I have had several crash-reports on both my machines. ;)

I am using mytharchive much but in this build, mytharchive are compiled against the wrong version of libmyth.
Edit: Ok, this goes for all the plugins.

How about mediabuntu? I need ffmpeg from that package to make sound work for the flash videos in mythweb.

Great work with MythBuntu btw!

---

### Post by superm1 on 2008-02-16
> **Nikas said:**
> Ok. I have had several crash-reports on both my machines. ;)

I am using mytharchive much but in this build, mytharchive are compiled against the wrong version of libmyth.
Edit: Ok, this goes for all the plugins.

Yeah the archive's publisher didn't publish the new builds.  They are coming as soon as the archive publishes them.

> 
How about mediabuntu? I need ffmpeg from that package to make sound work for the flash videos in mythweb.

Yeah medibuntu works fine.  Also you can activate it from mcc still.
> 
Great work with MythBuntu btw!
Thanks :)

---

### Post by Nikas on 2008-02-16
> **superm1 said:**
> Yeah the archive's publisher didn't publish the new builds.  They are coming as soon as the archive publishes them.


Yeah medibuntu works fine.  Also you can activate it from mcc still.

Thanks :)

How soon can this be? ;)

I have tried to remove and reactivate mediabuntu from mcc but that made the mcc crash.
I have no sound from the flash player in mythweb. I had the same problem in 7.10 but activating mediabuntu made the sound work and conversion to xvid with nuvexport started to work too.

I have to sit in the closet to manage my server now .. i like vnc when it works! ;)

---

### Post by superm1 on 2008-02-16
> **Nikas said:**
> How soon can this be? ;)

I have tried to remove and reactivate mediabuntu from mcc but that made the mcc crash.
I have no sound from the flash player in mythweb. I had the same problem in 7.10 but activating mediabuntu made the sound work and conversion to xvid with nuvexport started to work too.

I have to sit in the closet to manage my server now .. i like vnc when it works! ;)
Something is wrong with the archive's publisher.  Archive admins aren't around on the weekend, so probably monday or tuesday.  As for medibuntu, crashes exactly like what you are describing are what we need reports on.  Please submit away :)

As for the VNC, there are alternative VNC servers out there.  You can see if you find one that works well for you under Hardy.  If you find one you really like, we can likely switch our code around to use it instead by default.

---

### Post by Nikas on 2008-02-17
Thanks.

So.. my server hard locks after like one hour or in some times a couple of hour all the time. Need to press reset. Where do i begin? :/

The last thing that mythtv did:
```
2008-02-17 05:11:12.421 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-02-17 05:26:12.459 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-02-17 05:40:33.223 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-02-17 05:40:33.232 UPnpMedia: BuildMediaMap Done. Found 9 objects
2008-02-17 05:41:12.496 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-02-17 12:03:43.992 Using runtime prefix = /usr, libdir = /usr/lib <- REBOOT
```

Last kern.log for that time:
```
Feb 17 01:39:06 mythtv kernel: [   82.421466] NFSD: starting 90-second grace period
Feb 17 01:39:15 mythtv kernel: [   91.316228] NET: Registered protocol family 17
Feb 17 01:39:31 mythtv kernel: [  107.435661] eth0: no IPv6 routers present
```

Nothing strange there..

Edit:
Big problems with my two nova t-500. Disconnects and i2c read/write error. Did NOT have this problems with 7.10.

---

### Post by superm1 on 2008-02-17
> **Nikas said:**
> Thanks.

So.. my server hard locks after like one hour or in some times a couple of hour all the time. Need to press reset. Where do i begin? :/

The last thing that mythtv did:
```
2008-02-17 05:11:12.421 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-02-17 05:26:12.459 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-02-17 05:40:33.223 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-02-17 05:40:33.232 UPnpMedia: BuildMediaMap Done. Found 9 objects
2008-02-17 05:41:12.496 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-02-17 12:03:43.992 Using runtime prefix = /usr, libdir = /usr/lib <- REBOOT
```Last kern.log for that time:
```
Feb 17 01:39:06 mythtv kernel: [   82.421466] NFSD: starting 90-second grace period
Feb 17 01:39:15 mythtv kernel: [   91.316228] NET: Registered protocol family 17
Feb 17 01:39:31 mythtv kernel: [  107.435661] eth0: no IPv6 routers present
```Nothing strange there..

Edit:
Big problems with my two nova t-500. Disconnects and i2c read/write error. Did NOT have this problems with 7.10.
Well that's not good.  Start out by looking for bugs on LP on the nova t-500 related to i2c.  If nothing around, post a bug and google a bit.  If you find something relevant that was say fixed in v4l-dvb (upstream), we can pull in those fixes.  When you file any bugs against Ubuntu packages, hit the "Also affects Project" and put Mythbuntu.  That will make sure that we're CC'ed on the bug and can track it

---

### Post by Ubeast on 2008-02-18
I'm not sure if I can file this as a bug, but I'll describe my upgrade experience here in the hope it helps someone.

I had a pretty standard 7.10 Mythbuntu install, thought I would try the 'sudo update-mananger -c -d' method.

The upgrade downloaded and installed without a hitch.

On reboot the machine paused for a long time on the mythbuntu loading graphic then went to a black screen with no input. I tried recovery modes, and older kernels from Grub's list too. At one point it made it into X but in a low low res mode and was unusuable.

Thinking perhaps my combination of sata and pata drives, plus sata dvd player might be cause grief I cut the system down to one sata drive and one usb external dvd player and did a clean install of Mythbuntu 7.10. From there I quickly configured mythtv to get it functional and tried the hardy upgrade again. Same deal. At best I could get to a 'busybox' screen with an 'initramfs' prompt. I tried a lot of things but couldn't sort it... so...

I downloaded the 8.04 Mythbuntu i386 Alpha 2 and did a clean install from the live cd.

This worked much much better and I was up and running in no time. Ok... some issues:

Now my HD channels were choppy, CPU usuage was on around 95+% which wasn't the case in 7.10. I tried to fiddle with XvMC and the like but I don't quite understand the new layout in MythTv 0.21 (I can't even find deinterlacing!).

Then my Mythtv menus because blank (just a background, no text or icons) so I deactivated the proprietry NVidia driver, rebooted, activated it again and rebooted. Now my menus came back and CPU usage on HD channels was back to a more reasonable 80% (and not choppy). My menus keep dissappearing though... it makes it pretty damn hard to do anything!!!!. I think it might be OpenGL releated, but that seems odd... never had a prob in 7.10.

Nvidia-settings seems to be missing?

The w32 codecs now download which they never did for me in 7.10. Yay.

---

### Post by tegwilym on 2008-02-18
Cool!  A new version is out (almost!).  

I see there are updates with the lircrc setup.  Is this new version easier to setup and configure an IR blaster?  I'm using a wireless keyboard to control the computer, then the computer goes to a serial --> IR emitter to change the channels on my DirecTV box.

I'm using Mythdora for MythTV right now and got it all working, but since I'm a big Ubuntu fan, I'd like to use Mythbuntu, but could never get the serial-IR working yet.  

Any comments on this part?  I'll download this newer version and give it a try on my spare drive. 

Tom

---

### Post by dallas8101 on 2008-02-20
Back to the first post in this series,  I am also having drift problems with the time.  I have done both the Ubuntu time howto suggestions (adding a line to the daily run cron, and setting up the automatic time sync in the ubuntu control panel). I end up losing the first couple of minutes of recordings because the clock seems to settle at about 1.5 minutes fast, even just after syncing it  seemed to be that way when I used time.ubuntu.com(?). I switched to a central time zone serve and it seemed better for a while but now its back to about 1.5 minutes fast.

I was wondering if 8.04 could include some controls on the web pages to actually help with initiating a manual (or checking the automatic?) sync without having to exit mythtv and going to the os level control panel.  I am still a newbie, so I always have problems getting back to the front end without rebooting.

I really like the web interface, and it has become my main interface, about 95% of the time.

---

### Post by jyavenard on 2008-02-22
Was trying mythbuntu 8.04 alpha 2.
Machine is a Gigabyte GA-P35-DS3P (v2.2) motherboard with a E8200 CPU (dual core 2.66Ghz) with 2GB of RAM.
Video card is a nvidia 6600GT

After booting the CD, all I get is a black screen. You can see the mouse cursor (which is responsive) but that's it.
After killing X with Ctrl-Alt-backspace it will show the login window and and after 30s will log in.

Double clicking "Install Mythbuntu", Selecting the languages etc.
Prepare disk space window.
Unfortunately, mythbuntu fail to see any of my existing LVM and show the individual disk, even though they are set as RAID0 (2x750GB)

I selected "Manual" not trusting what the installer would do with my existing partitions (been running mythtv on my machine for several years running CentOS 5.1)
It shows my existing CentOS / will be mounted as /media/sda1, it sees the existing 1GB swap partition , which I resized as 2GB (this 1GB partition is a left over from my previous machine). Resizing worked.

Selected the 40GB of free space I had on that disk to create a new partition: set to mount it as / (you really know what you're doing here, the installer doesn't make this obvious at all!)

Selected Standard Installation after entering my name and the account I want to create

My device isn't in the Remote Control List (It's a DVB-T DigitalNow Pro PCI card, which is recognised by the OS as Zarlink MT352 DVB-T as shown in dmesg)

Selected Modify Video Driver and Settings, selected nvidia geforce 5+ (nvidia-new) Forward. 
That's it, installer hangs there. no progress whatsoever. in the top right corner I see a message that one application has crashed. Great.

Rebooting the machine, restarted the CD, this time left the default settings for the video drivers, not selecting nvidia.
This time it installs

Running mythtv-setup, none of my DVB-T card are seen (even though they have been properly detected by the kernel).
So I set IPTV channels (IGMP broacast) at the end it crashed and asked me to reboot.

Now it has started mythfrontend, but I can't seem to be able to do anything else.

Well, can't say my experience with mythbuntu has been very pleasurable.

Will probably pass.

---

### Post by jyavenard on 2008-02-22
Okay, after a reboot and some hassle it's looking much better now.

I love the synaptic package manager and how easy it was to select a local mirror. Always had to enter this by hand with either fedora or centos

Not too please with how limited sound settings are. It recognised my sound card, but can't find a way to select what will be the default PCM output ( I want to use my SPDIF output)

Still can't see any of my LVM partitions :(

Jean-Yves

---

### Post by dflipb on 2008-02-23
Upgrading Messed me up :(

It is limping along, It is still recording my shows, but now when I go to watch HD, I just get a blank screen and I can't get out of it.  I have to kill the front end.  

I can play HD through vlc but only after I turn on the propritary codecs (something I did in 7.10, but it shut them off when I upgraded)

When I go into the terminal, it says "can not find host htpc" Htpc is the name of my computer.

I had my remote working in 7.10 (I'm using Happaug pvr 350), but again, now it's not working, I'll have to find how I set it up again and try that.

Over all the install went ok until I tried to use the stuff, then....not so much =\

Sad thing is I only wanted the upgrade to get the new add hard drive feature.

But I guess I'm just a glutten for punishment.

---

### Post by superm1 on 2008-02-23
> **dflipb said:**
> Upgrading Messed me up :(

It is limping along, It is still recording my shows, but now when I go to watch HD, I just get a blank screen and I can't get out of it.  I have to kill the front end.  

I can play HD through vlc but only after I turn on the propritary codecs (something I did in 7.10, but it shut them off when I upgraded)

When I go into the terminal, it says "can not find host htpc" Htpc is the name of my computer.

I had my remote working in 7.10 (I'm using Happaug pvr 350), but again, now it's not working, I'll have to find how I set it up again and try that.

Over all the install went ok until I tried to use the stuff, then....not so much =\

Sad thing is I only wanted the upgrade to get the new add hard drive feature.

But I guess I'm just a glutten for punishment.
Please file appropriate bugs for each of your issues.  Being a glutten for punishment will pay off in the end so that we can solve these issues for other folks upgrading.

---

### Post by dflipb on 2008-02-23
I will, I just haven't had time yet. I upgraded last night...now i'm at work =( 

Do you have any suggestions to get any of these things working? esp the "unable to resolve host htpc"  problem.

---

### Post by dflipb on 2008-02-24
> **superm1 said:**
> Please file appropriate bugs for each of your issues.  Being a glutten for punishment will pay off in the end so that we can solve these issues for other folks upgrading.


I can't find where to publish the bugs.

---

### Post by superm1 on 2008-02-24
If you are sure what source package they fall under, then:

```
https://bugs.edge.launchpad.net/ubuntu/+source/PACKAGE/
```

Where PACKAGE is that source package.  For example if the source package were mythtv:
```
https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/
```

Now, if you aren't sure what source package they are bugs in, put them against the mythbuntu project:


```
 https://bugs.edge.launchpad.net/mythbuntu
```

And they will be reclassed by one of us.

---

### Post by dflipb on 2008-02-25
> **superm1 said:**
> If you are sure what source package they fall under, then:

```
https://bugs.edge.launchpad.net/ubuntu/+source/PACKAGE/
```

Where PACKAGE is that source package.  For example if the source package were mythtv:
```
https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/
```

Now, if you aren't sure what source package they are bugs in, put them against the mythbuntu project:


```
 https://bugs.edge.launchpad.net/mythbuntu
```

And they will be reclassed by one of us.

Thank you!

I think this would be useful information to be posted in the sticky note at the top of the forums about 8.04
Thanks.

Also any ideas about "unable to resolve host htpc"????????????? Thanks

---

### Post by ebike on 2008-06-11
Multirecord doesn't work as expected. I am running Mythbuntu 8.04 with two satellite cards each setup with multirecord=2, this gives me two virtual tuners for each card, however this is what happens:

If frontend_a is watching a channel on multiplex_a and I try to watch multiplex_b on frontend_b, then myth won't let me, it only allocates the virtual tuners of the one card, which sucks, it behaves as though their is only one card.

Does anyone know if some setup option can fix this. Currently I have both tuners tuning all multiplexes and both tied to the same video source.

Thanks

---

### Post by Nesster on 2008-06-12
ebike: you should start a new thread with a specific title to your problem.

Good luck

---

### Post by ebike on 2008-06-12
Have done .... no one has an answer yet, and it seems such a fundamental promlem .. go figure ](*,)

---

### Post by ebike on 2008-06-14
Seems it is a problem with Mythtv ... see this thread.

--> [http://www.gossamer-threads.com/lists/mythtv/users/337494?page=unread#unread](http://www.gossamer-threads.com/lists/mythtv/users/337494?page=unread#unread)

Seems the developers see that multiple LiveTV's are not "normal" use :confused:

---


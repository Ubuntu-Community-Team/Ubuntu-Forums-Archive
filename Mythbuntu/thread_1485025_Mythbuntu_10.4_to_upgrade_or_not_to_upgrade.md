---
title: "Mythbuntu 10.4: to upgrade or not to upgrade?"
date: 2010-05-16
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-16
I'm currently running Mythbuntu 9.10, and was wondering about upgrading to 10.4 (especially given that it's the LTS version and I might then want to stick with it for a while).

However, I see there are quite a few threads here about problems other folk have had after upgrading, and I'm wondering if that's just a few who have been unlucky, or whether 10.4 is a bit more buggy than we'd like.

I have most things working at the moment (although not everything, chief among those things is that I've never got my remote control to work) and am wondering whether this is a time to apply the motto "if it ain't broke, don't fix it".

Any thoughts on how easy the upgrade is for most people? I'd be grateful if you could use the voting buttons to tell me how it went for you and leave any comments here.

---

### Post by jmeads on 2010-05-16
I've upgraded from Mythbuntu 9.10 to 10.4 without problem on a dedicated backend and 2 frontends, no problems with either except for having to disable the screensaver on the frontends.

Additionally I have also carried out a fresh install of 10.4 onto a acer revo, slight issue getting audio over hdmi working (was initially disabled and had to tick a check box in the volume dialog box)but otherwise all ok. (well happy with vdpau which worked out of the box)

---

### Post by laffinet on 2010-05-16
I tried upgrading my combined frontend/backend from 9.10 to 10.04. 
Could only start in low graphics mode afterwards, something was wrong with the nvdidia driver (module not found, or so, there's a thread that seems to deal with the same problem [here]("http://ubuntuforums.org/showthread.php?t=1480660")).

Tried for a while fixing it, but took too long and really wanted to use the machine. :(

Ended up restoring my system partition from a clonezilla image (lucky I spent the time creating that before the upgrade :cool:). Realised that I had forgotten to backup the database:rolleyes:, which got upgraded in the mythbuntu upgrade, so was left with a 0.22 system and a 0.23 database.:eek:

Added the nightly build repos, upgraded to 0.23 (but still 9.10) and everything's been working very well since.:P

Might try the overall upgrade again some time (not without another backup), but don't have the time at the moment.

---

### Post by nickrout on 2010-05-17
Did an upgrade from 8.04LTS to 10.04LTS on my backend. This is supposed to work and be supported. System would not boot, weird error messages that googling would not help with. Complete borkage. I did a fresh install onto an old IDE drive I added in, and then had to fix a whole lot of things but eventually it works.

Frontends I just blasted and installed the new version over the top. Why keep the old version on a frontend anyway?

But as a result of my experience with the backend my confidence in mythbuntu has taken a dive, I am looking at LinHES (formerly knoppmyth) very seriously. Ubuntu just don't seem to be able to provide an upgrade path that is suitable for an "appliance".

---

### Post by Chewiesw on 2010-05-17
I upgraded from  9.10 to 10.4 and now watch TV does work. Like a muppet I didn't manually write down all my previous working settings. If I were you I would defiantly follow the motto "if it ain't broke, don't fix it".

But if you decide to upgrade and you know you are going to... backup backup and backup everything. If I could go back I would possibly try to clone my old setup and just re-install if things don&#8217;t work out as expected.


Turns out that my database was poked, a quick repair was that was needed.

---

### Post by nickrout on 2010-05-17
> **Chewiesw said:**
> I upgraded from  9.10 to 10.4 and now watch TV does work. Like a muppet I didn't manually write down all my previous working settings. If I were you I would defiantly follow the motto "if it ain't broke, don't fix it".

But if you decide to upgrade and you know you are going to... backup backup and backup everything. If I could go back I would possibly try to clone my old setup and just re-install if things don’t work out as expected.

if you upgraded your settings stay the same, they are in the database which is carried through from version to version.

---

### Post by emillan on 2010-05-17
I am very happy with 10.04.  (I was running 9.04 and earlier before now.)  The MythTV and Mythbuntu teams are doing great work and I surely appreciate it.

Emilio

---

### Post by pauna on 2010-05-17
The upgrade process went very smoothly from 9.04, which was very nice. Had to reconfigure sound, but that was about it.

However, I had major problems with MythTV bugs (both DVD playback and DVB stream codec change caused frontend crashes) so in all honesty I could not give the best grade here.

Both of these issues have now been fixed in auto-builds, but that still does not remove the underlying problem that the non-auto-build release was sort of buggy. For me at least.

---

### Post by JMcFly on 2010-05-17
What does LTS mean?

---

### Post by NautiusMaximus on 2010-05-17
> **JMcFly said:**
> What does LTS mean?

Sorry, I should know better than to use abbreviations without defining them.

Long Term Support. See [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by nickrout on 2010-05-17
> **pauna said:**
> The upgrade process went very smoothly from 9.04, which was very nice. Had to reconfigure sound, but that was about it.

However, I had major problems with MythTV bugs (both DVD playback and DVB stream codec change caused frontend crashes) so in all honesty I could not give the best grade here.

Both of these issues have now been fixed in auto-builds, but that still does not remove the underlying problem that the non-auto-build release was sort of buggy. For me at least.

The version of mythtv released with 10.04 was NOT the official "release" of mythtv-0.23. It was a release candidate.

---

### Post by alien878 on 2010-05-18
The upgrade itself went smoothly for me.  I then re-installed the s2-liplianin for my capture card ([http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work)).  The card "worked", but had heavy pixelization.

Old videos played fine, new ones didn't, so it wasn't a graphics issue.  I tried the same version of s2-liplianin that worked on 9.10 as well as the latest.  I also tried [http://jusst.d/hg/mantis-v4l-dvb](http://jusst.d/hg/mantis-v4l-dvb) drivers. All had the same problem with pixelized pictures.

I ended up going back to 9.10.  Next time I will take a clonezilla before upgrading....

I would be interested in knowing if other people are having problems with the mantis drivers.  I'll probably try again when they are in the ubuntu kernel.

---

### Post by NautiusMaximus on 2010-05-18
> **nickrout said:**
> The version of mythtv released with 10.04 was NOT the official "release" of mythtv-0.23. It was a release candidate.

That's interesting. So what happens if I upgrade to Mythbuntu 10.4 now? Will I still get the release candidate for MythTV 0.23, or has that now been fixed so that I'll get the real thing?

---

### Post by tgm4883 on 2010-05-18
> **NautiusMaximus said:**
> That's interesting. So what happens if I upgrade to Mythbuntu 10.4 now? Will I still get the release candidate for MythTV 0.23, or has that now been fixed so that I'll get the real thing?

You will get the RC. You can install the mythbuntu-repos package and enable auto-builds. That will give you packages from the 0.23 fixes branch (not trunk, newer than 0.23 release)

---

### Post by NautiusMaximus on 2010-05-19
Forgive me if I'm being a bit slow here, but just to be sure:

If I upgrade to Mythbuntu 10.4, to start with I'll get MythTV RC, correct?

Then if I install the mythbuntu-repos package and enable auto-builds, MythTV will be upgraded to the officially released version, with some bonus bug fixes beyond it as well. In other words, I should get the most stable version of MythTV once I've done that. Correct???

---

### Post by nickrout on 2010-05-19
Correct, just make sure you specify 0.23 when answering the setup questions when installing mythbuntu-repos.deb. If you choose 0.24 you will get 'trunk' which is, by definition, not stable. If you choose 0.23 you will get 0.23 PLUS miscellaneous fixes, but not new features included in the current development build (aka trunk)

whats more you will get regular updates to the latest 0.23-fixes.

---

### Post by wyliecoyoteuk on 2010-05-25
Updated from 9.10 to 10.4, all looked well, then discovered no sound! turned out that Pulseaduio wasn't installed. installed it and PA volume control, and found both channels set to zero. Turned up, fixed.
Unfortunately, the remote for my Hauppuage Nova-T500 doesn't work properly, only some buttons work. Checked it using irrecord, the codes are there, and all the config files are correct.
However using the devinput driver doesn't work with the irremote event or lirc0. 
I think it may be something to do with the new Lircd namespaces, not sure yet.

---

### Post by colinnwn on 2010-05-25
My unresolved saga that you likely found/read
[http://ubuntuforums.org/showthread.php?t=1469226](http://ubuntuforums.org/showthread.php?t=1469226)

It all depends on how much you value your time, need Myth working quickly, and see improvements in Lucid/0.23 that you want.

Personally I'd suggest not doing the upgrade, and if you do anyway, back up your database, enable autobuilds, do a Synaptic update to get on Karmic/0.23, back up your database again, install MythBuntu Lucid from scratch, and restore your 2nd backup. The first backup is only if things really go south and you want to go back to Karmic/0.22.

Heck, even if you see something you want in 0.23, I'd suggest just backing up your database, enabling autobuilds, do a Synaptic update to get on 0.23, then restarting, and staying on Karmic. Don't test anything after the autobuild update before restarting. Mythweb, among other things will not be working until after a restart.

DO NOT AGREE TO A PARTIAL DIST UPGRADE AT ANY POINT. You will probably get offered this after enabling autobuilds and running Synaptic update. Bad things will happen if you do a partial dist upgrade:!:

---

### Post by NautiusMaximus on 2010-05-29
Just bumping this thread to see if we can get a few more votes on the poll.

Thanks for all the thoughts so far: still haven't decided whether to upgrade or not.

---

### Post by wyliecoyoteuk on 2010-06-01
Update:
resolved my remote issues.
see my howto [ here ](http://ubuntuforums.org/showthread.php?t=1140411&highlight=NOVA-T+500)

---

### Post by dibuntux on 2010-06-09
Dear All,
I did the switch, or better, I'm still switching to 10.04 - but I have big problems with GRUB.

In fact, to play it safe, I got another WD CaviarGreen 1,5TB, and made a CloneZilla copy of my old disk on it. 
Then from the BIOS I selected the new disk as the one to boot first, which it did, and from that one I did the network upgrade to 10.04 AMD64. Everything was ok - the only message I got was from network manager missing some components, but since I was monitoring the upgrade from a remote PC with VNC, maybe it was just that.
In the end, GRUB found all partitions on both disks, and told to select the one I wanted in GRUB. My response was just sda and sdb, since all the other were were just the details to all single partitions from the two specular disks.
At the boot the system could not start and throw me in to the grub rescue shell.

Using the Ubuntu grub wiki I had to manually do a
grub-install /dev/sda
update-grub

to get to boot to a grub menu again. From the grub menu I'm presented with all kernels 2.6.31 and some 2.6.32 - system will boot fine using 2.6.31 - AND EVERYTHING WORKS
but it will not boot with 2.6.32 saying that no kernel loaded.

For doing a grub-install I used a Ubuntu 9.10 amd64 and the grub that it installed is 1.97.

Now, what do I do to get it to work with the right kernel for 10.04 and to let it start in auto (becouse it just stuck at the grub menu)?

UPDATE: I found that I'm still running mythbuntu 9.10, but I believe some parts are updated - I configured the new Sound section, much different from before. Also, first time I run Myth it asked to upgrade database schema...
But if I run Update manager tells me that 10.04 is available... Any idea I should procede from here?
UPDATE2: I'm starting with the new HD, but GRUB can start the old system! So I have both... but still the kernel is the 2.6.31, even on the new Myth... what a mess... 
Thanks in advance

Mythbuntu 9.10 AMD64
Gigabyte GA-M720 2GB DDR2-800
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-t

---

### Post by newlinux on 2010-06-09
I went from 8.04-10.04 on most of my machines, and from 9.04-9.10-10.04 on my laptops. From myth .21 to .23. I keep daily backups of almost all important config files and databases,

My experiences were somewhat detailed at [avsforum here]("http://www.avsforum.com/avs-vb/showthread.php?p=18715541#post18715541"). For all but one machine it was successful, and probably would have been for all if it weren't for the flashplugin-nonfree I installed in 8.04. I maybe could have spent more time to figure out how it was screwing up apt, but I it didn't take long to restore my apps from a fresh install. Upgrading myth was the easiest part.

---

### Post by eascott on 2010-06-10
JFTR, I am experiencing the same problem... EXACTLY the same symptons. I have a slightly different configuration... naturally:

Mythbuntu 9.10 AMD64 --> Mythbuntu 10.4
Patriot 4GB DDR2-800
Zotac 8200-ITX
Athlon X2 4850e (CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02)
Nvidia 250MB
Hauppauge HVR-2250

I have installed Mythbuntu 4 times so far. My first attempt was with a CD gened up from the ISO. That just locked up. My next attempt was via the update tool in Mythbuntu 9.10. That went to compleletion but left me with the situation described by dibuntux. I then ran across some threads that suggested that card readers could cause the Mythbuntu Installation CD to lock up so I disabled my card reader and... surprise... I achieved a successful install from the CD... BUT I still have the grub 10.4 option won't boot but the 9.10 will problem. In addition, I have successfully installed the Hdr-2250 driver/firmware but it is being installed into 10.4 so, of course, it isn;t working in the (mostly) 9.10 successful boot.

When I run the 10.4 menu selection it stops streaming to the monitor with a "child-rip+0x0/0x20" in the last line. When I run the recover selection it ends with "system_call_fastpath+0x16/0x1b". 

I have examined the 9.10 dmesg logs which gave me some ideas but, at this point, I am figureing out how I can get the dmesg logs for the failed 10.4 boot... which is, of course, what I need to really figure out what is causing the problem.

Over in the forum's "Install problems" section (which is probably where this thread should be), I ran across [Re: Installing 10.04]("http://ubuntuforums.org/showpost.php?p=9425408&postcount=4") and the procedure outlined in this response actually resulted in the display of the Mythbuntu logo with five static red dots (which I haven't seen on the target machine previously) but the boot stopped at that point.

Anyway, like dibuntux, I could use some advice.

regards,

Evan

---

### Post by nickrout on 2010-06-10
That appears to be a kernel error, so grub is booting your kernel.

---

### Post by dibuntux on 2010-06-11
OK, so my good idea of cloning the disk turn out to be a "chinese mess". Wait, it was good if I had disconnected the disk after cloning and just upgrade the cloned disk (has I had planned, but then too lazy to implement).

So, with both disks, grub made a mix of the two, and both system disk were booting part of the other system. So I had an upgraded 10.04 myth booting the old kernel, and the old myth 9.10 booting the latest kernel... 
now the dbase is screwed, the system will not log me on anf gparted is not even recognizing the data partition as XFS.

At least the data partition on the original disk is still ok, but the system partition is messed up and I just deleted it.

That is too bad, becouse the upgrade, if the disks were not connected simultaneusly, would have gone OK!

Time to reinstall and manually copying the data partition. 

Do you have a procedure to reinstate the recordings back into the database? TIA

---

### Post by alien878 on 2010-06-11
I'm not sure which type of clonzilla clone you did, but in general, you need either "restore" the original disk from the clone or swap the clone for the original.  Usually, you don't want to have both the clone and the original mounted at the same time.

If you don't have a database backup, the easiest way to recover including recordings would be to restore the original disk from the clone and then disconnect the clone.

FYI:  A failed upgrade is generally a *bad* thing.  You might get lucky and get it to complete, but you will never know if there are other hidden problems waiting to bite you later.  If you have a backup, I would recommend using it.

One comment on root partition backups:  I have / as a small (15G) partition and have myth tv/video/music/etc. files on separate (big) partitions.  I can then use clonezilla to clone the root partition (ex. /sda1) to a file on one of the big myth partitions.  Then restoration is generally painless.

---

### Post by nickrout on 2010-06-11
you need to restore your database backup, there is no other way of reinstating your recorded programmes.

---

### Post by dibuntux on 2010-06-12
Thanks Mythich fellow for all your precious advice.
In the end, I did a clean install of 10.04 AMD64. It works, with some strange things and few problems.
1) tuning of DVB-T WORKS now - and this is GOOD. Still it is a mess to get order with channels numbering and wrong LCN guessing.
2) Told the installer to set language to italian, set nvidia driver, vnc & samba: did none of those, had to turn them on manually. Samba config is different & still not working. Vnc is different and had to learn how to set it.
3) My SkyStar 2 DVB-S card, that always worked, now is on error state. It worked OK when I upgraded the system...

As for partition: / is on a 20 GB /sda1 and /home is the big disk; guess I will make a clone of it on the big disk as suggested.
Recordings: I do not know if I can regain the db; I can manually rename the recs files and move them to video - is a pain, but it works.

Many things to do still...

---

### Post by AKADAP on 2010-06-12
Not quite mythbuntu, I'm running Ubuntu with a mythbuntu package on my main system.

I have attempted 3 clean installs, and 2 upgrades for Ubuntu 10.04, the score so far
upgrade that just worked 1
install that just worked 1
upgrade that worked after messing with it a bunch 1
install that kindof/sortof works 1
install that just does not work at all 1

Attempting to install on a via epia M 6000. This uses a Samuel II processor, a processor that is one instruction (cmov) short of being a 686 machine. Every linux I have tried including ubuntu correctly identifies this processor as a Samuel II, but goes ahead and installs 686 packages on the system. This leaves the system where windows will not scroll properly, and the system will lock up hard after moving about 5 cards in a game of spider 3 deck in AisleRiot.

On an AMD Athlon system with an ATI Radion All In Wonder video card connected to a Sony FW900 display. At first it booted into a garbage screen. After reporting this bug I was informed of a boot switch that got me to boot to a corrupted screen. What is happening now is that the system is selecting a video mode that the monitor can handle, but the video card can not. I have been able to change the resolution of the screen once logged in to something usable, but the login screen is still corrupted. I must also enter the boot switch every time I boot as I have no idea how to make it permanent.

On my main system, the one I run mythTV on, it initially booted to a corrupted screen. Using safe mode, I installed the ATI proprietary driver, and was then able to boot. Myth was unable to display video, and Google earth was crashing. I found that by changing Myth to not use OpenGL, it would display video but without proper vsync. When a new version of the ATI driver came out, I uninstalled the ATI proprietary driver, and found that the open source drivers were now working. vsync works with the open source driver, so that is where I left it. Google earth works again, but occasionally will crash in a way that dumps me at the login screen.

---

### Post by nickrout on 2010-06-12
> **dibuntux said:**
> Recordings: I do not know if I can regain the db; I can manually rename the recs files and move them to video - is a pain, but it works.

Many things to do still...

If you have a backup of the database getting it back is easy. See the wiki page for all the down and dirty.

My 2 skystar 2 cards work fine in a fresh install of 10.04, although I don't have a DVB-T card too.

dmesg should tell you what is going on with getting the drivers for the skystar going.

---

### Post by nickrout on 2010-06-12
> **AKADAP said:**
> Not quite mythbuntu, I'm running Ubuntu with a mythbuntu package on my main system.

I have attempted 3 clean installs, and 2 upgrades for Ubuntu 10.04, the score so far
upgrade that just worked 1
install that just worked 1
upgrade that worked after messing with it a bunch 1
install that kindof/sortof works 1
install that just does not work at all 1

Attempting to install on a via epia M 6000. This uses a Samuel II processor, a processor that is one instruction (cmov) short of being a 686 machine. Every linux I have tried including ubuntu correctly identifies this processor as a Samuel II, but goes ahead and installs 686 packages on the system.  Ubuntu only ships 686 packages, so its never going to work properly on your M6000.

I have an M9000. I ended up using minimyth on it, mini still ships packages that work with it.

> This leaves the system where windows will not scroll properly, and the system will lock up hard after moving about 5 cards in a game of spider 3 deck in AisleRiot.

On an AMD Athlon system with an ATI Radion All In Wonder video card connected to a Sony FW900 display. At first it booted into a garbage screen. After reporting this bug I was informed of a boot switch that got me to boot to a corrupted screen. What is happening now is that the system is selecting a video mode that the monitor can handle, but the video card can not. I have been able to change the resolution of the screen once logged in to something usable, but the login screen is still corrupted. I must also enter the boot switch every time I boot as I have no idea how to make it permanent.


I suggest getting an nvidia card to replace that ATi. However if you want to get X to run at a particular resolution you probably need to edit /etc/X11/xorg.conf> 
On my main system, the one I run mythTV on, it initially booted to a corrupted screen. Using safe mode, I installed the ATI proprietary driver, and was then able to boot. Myth was unable to display video, and Google earth was crashing. I found that by changing Myth to not use OpenGL, it would display video but without proper vsync. When a new version of the ATI driver came out, I uninstalled the ATI proprietary driver, and found that the open source drivers were now working. vsync works with the open source driver, so that is where I left it. Google earth works again, but occasionally will crash in a way that dumps me at the login screen.

ditto my comments about ATi cards (probably not the advice you want to hear sorry)

---

### Post by Erkander on 2010-06-15
> **nickrout said:**
> Correct, just make sure you specify 0.23 when answering the setup questions when installing mythbuntu-repos.deb. If you choose 0.24 you will get 'trunk' which is, by definition, not stable. If you choose 0.23 you will get 0.23 PLUS miscellaneous fixes, but not new features included in the current development build (aka trunk)

whats more you will get regular updates to the latest 0.23-fixes.


Ok, so I'm a newb.  How do you go about doing this exactly?

--Erkander

---

### Post by colinnwn on 2010-06-15
> **Erkander said:**
> Ok, so I'm a newb.  How do you go about doing this exactly?

--Erkander

I don't think you need to add the mythbuntu repos. From memory, go into MCC and enable autobuilds. Choose "fixes" or "stable" whatever they call it, (i.e. not "trunk" or development"). Close MCC. Update Synaptic. If you get a dialog suggesting to do a partial upgrade **DO NOT DO IT**. Synaptic should then show the most current Myth modules ready to install. Click on _update_. Restart Ubuntu before doing anything else. MythWeb at a minimum will not be working, and throwing a hissy fit until you restart.

---

### Post by Erkander on 2010-06-15
Thanks!  I'll try that tonight.  I'm having some video playback issues that maybe that will help.

--Erkander

---

### Post by tgm4883 on 2010-06-15
> **colinnwn said:**
> I don't think you need to add the mythbuntu repos. From memory, go into MCC and enable autobuilds. Choose "fixes" or "stable" whatever they call it, (i.e. not "trunk" or development"). Close MCC. Update Synaptic. If you get a dialog suggesting to do a partial upgrade **DO NOT DO IT**. Synaptic should then show the most current Myth modules ready to install. Click on _update_. Restart Ubuntu before doing anything else. MythWeb at a minimum will not be working, and throwing a hissy fit until you restart.

Close. First download and install the autobuilds package from [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds). It asks you those questions during install, so no need to go to MCC to configure it. But then follow your instructions for upgrading with Synaptic

---

### Post by Erkander on 2010-06-16
Thanks for all of the help. The updates fixed pretty much everything. I have a fully functional system now!

---

### Post by Naoyuki Tai on 2010-06-16
I have tried to upgrade from Karmic to Lucid, and was a total disaster.
I ended up reinstalling Lucid from scratch.

I suspect that my setup was not somewhat uncommon. 

I run front/back end on one machine but the MySQL database is on FreeBSD, because I've been using FreeBSD server for last 15 years or so, and when MySQL database got corrupted a few times by a flaky hardware while ago, I moved the database on FreeBSD.

#2 was fglrx. fglrx on Karmic did not work for me, so I had to install without package.
#3 is that I use serial IrDA dongle which act200l does not work out of box, so I have to build from source.

Anyhow, after the update, I was able to get the backend going but Xorg / GDM got totally busted. /var/log/Xorg.0.log suggests flgrx is running, and startx did start the X from console, but GDM gets killed with "SIGABRT".

I gave up the upgrade and did a fresh install of Lucid.
I still have two glitches but not it's a usable state.

BTW, because the database is not on the same machine, I have no worries about losing it. I find it very convenient.

-- ntai

---

### Post by dibuntux on 2010-06-17
Ok guys, most everything works on my new 10.04 AMD64. My biggest problems are of permissions nature:
1) Samba - I can read the share /videos but cannot write to it; it has the same standard config in smb.conf and permissions are the same to /pictures, in which I can write. The only difference is that /videos is on storage group, but it was so in 9.10 and it worked. So I cannot move any video to it.
2) I used to use an user beckie for making the backup with Simplebackup to my myth mediaserver from my PC using ssh transfer. Here too I get "destination not writable with current permissions"; if I ssh from terminal to the media server using the same parameters I get full control no problem.

I can also VNC to the media server without problems and use myth web. So... Anybody has a suggestion?

Other glitches:
1) DTS Direct to digital ampli (spdif) STILL does not work
2) 5.1 upconvert (any setting, fast, good, best) works, but gives .5 sec of silence every 5 sec of audio

Everything else is just great. Even Boxee now works OK!

PS: for old recordings - I moved them to videos so I can watch them; jump ahead to skip ads just crash myth frontend. So I'm using Avidemux to reencode the old recs into Xvid - if you just reencode video, the audio track will be out of sync -> use -500 msec from the playback menu when watching or just encode the audio track. It is not as dramatic as it sound. I could watch the cup game in HD from DVB-T, record "24" on another tuner and run Avidemux; when the latter is finished it will show up on screen. Best to all.

---

### Post by newlinux on 2010-06-17
> **dibuntux said:**
> Ok guys, most everything works on my new 10.04 AMD64. My biggest problems are of permissions nature:
1) Samba - I can read the share /videos but cannot write to it; it has the same standard config in smb.conf and permissions are the same to /pictures, in which I can write. The only difference is that /videos is on storage group, but it was so in 9.10 and it worked. So I cannot move any video to it.
2) I used to use an user beckie for making the backup with Simplebackup to my myth mediaserver from my PC using ssh transfer. Here too I get "destination not writable with current permissions"; if I ssh from terminal to the media server using the same parameters I get full control no problem.

I can also VNC to the media server without problems and use myth web. So... Anybody has a suggestion?

Other glitches:
1) DTS Direct to digital ampli (spdif) STILL does not work
2) 5.1 upconvert (any setting, fast, good, best) works, but gives .5 sec of silence every 5 sec of audio

Everything else is just great. Even Boxee now works OK!

PS: for old recordings - I moved them to videos so I can watch them; jump ahead to skip ads just crash myth frontend. So I'm using Avidemux to reencode the old recs into Xvid - if you just reencode video, the audio track will be out of sync -> use -500 msec from the playback menu when watching or just encode the audio track. It is not as dramatic as it sound. I could watch the cup game in HD from DVB-T, record "24" on another tuner and run Avidemux; when the latter is finished it will show up on screen. Best to all.

I would suggest you create a separate thread for help with these issues. For your samba shares what options are you using when you mount them. What permissions does ls -l return both on the machine the share is mounted on and the machine the files are physically located on?

Does Dolby Digital passthrough work? What happens when you use DTS passthrough? 

As far as upmix goes, what's in your frontend logs when you try to use 5.1 upmix?

---

### Post by dibuntux on 2010-06-21
Thanks for your suggestions, I'll try to separate all the problems I have.

As for the samba share, options are standard ones set by mythbuntu, that always worked:

[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = ads

[videos]
comment = Videos
path = /home/mythtv/videos
browsable = yes
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[pictures]
comment = Pictures
path = /home/mythtv/pictures
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

I can write to pictures but not to videos.

If i ls -l the dirs have same permissions on the media center; do not know how to ls -l from the PC... 

TIA Dave

---

### Post by dibuntux on 2010-06-21
OK, dumb enough...
I create my videos dir in /home/mythtv using thunar file manager as root, so the owner was root... and has to be mythtv
so:
sudo chown mythtv mythtv -R
&
sudo chmod 777 -R mythtv

took care of the problem... now on the next

"Does Dolby Digital passthrough work? What happens when you use DTS passthrough?"

Yes Dolby Digital works perfectly - DTS, I get jerky & noisy "crackcrack" sound

TIA

---


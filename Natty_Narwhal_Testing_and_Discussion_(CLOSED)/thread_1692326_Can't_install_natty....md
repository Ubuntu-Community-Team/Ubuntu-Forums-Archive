---
title: "Can't install natty..."
date: 2011-02-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-02-21
I decided to start my testing with a fresh install, and find that the installer is not working for me. It gets as far as "Preparing to Install", and when I click on "forward", it just sits there forever with the animated cursor going. But it never moves beyond that.

I've tried the LiveCD versions from Feb. 19, 20, and 21 - same thing. I tried the Alternate versions, and upon trying to install, give a message to the effect of "can't find vmlinuz".

I've never had this problem before, and I don't see it mentioned in the forum after a search. Is this known behavior? Is there something simple I'm missing?

TIA

---

### Post by MWaddams on 2011-02-21
Just kill ubiquity in an other console. Check out / to see if the vmlinuz link is ok, otherwise relink it (ln -s /cdrom/casper/vmlinuz /vmlinuz).

---

### Post by VMC on 2011-02-21
Also, you have NVIDIA card, it won't work with X 1.10, you need 1.9.

---

### Post by sgage on 2011-02-21
> **MWaddams said:**
> Just kill ubiquity in an other console. Check out / to see if the vmlinuz link is ok, otherwise relink it (ln -s /cdrom/casper/vmlinuz /vmlinuz).

vmlinuz was linked to /boot/vmlinuz, which didn't exist. I tried relinking it, but still no joy.

Any other ideas?

---

### Post by sgage on 2011-02-21
> **VMC said:**
> Also, you have NVIDIA card, it won't work with X 1.10, you need 1.9.

NVIDIA cards work fine with X 1.10 with the default nouveau drivers. It's just the proprietary nvidia drivers that haven't caught up yet.

---

### Post by MWaddams on 2011-02-21
> **sgage said:**
> vmlinuz was linked to /boot/vmlinuz, which didn't exist. I tried relinking it, but still no joy.

Any other ideas?

What happens with Try instead of Install? Which processes show up on 'top', if the installer hangs?

---

### Post by VMC on 2011-02-21
> **sgage said:**
> NVIDIA cards work fine with X 1.10 with the default nouveau drivers. It's just the proprietary nvidia drivers that haven't caught up yet.

I tried the nouveau drivers, and it doesn't work for my geforce 6150 SE integrated video.

---

### Post by sgage on 2011-02-21
> **VMC said:**
> I tried the nouveau drivers, and it doesn't work for my geforce 6150 SE integrated video.

Until I decided to start over, nouveau was working fine with my geforce 8500GT card. I don't think that's it in any case, since the livecd desktop works fine (once I get it to show up).

---

### Post by sgage on 2011-02-21
> **MWaddams said:**
> What happens with Try instead of Install? Which processes show up on 'top', if the installer hangs?

If I click "Try", I get the same syndrome - it just sits there with the animated cursor going.

However, if I click "Install", let it run for a few seconds, then quit it, the live desktop comes up just fine after a few seconds. If I launch install from the desktop, the same problem occurs. Here's what the tail-end of a ps ax output looks like:

 ```
8470 ?        Sl     0:00 gksudo --preserve-env --desktop /home/ubuntu/Desktop/ubiquity-gtkui.desktop -- /usr/bin/ubiquity gtk_ui
 8474 ?        Sl     0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
 8477 ?        Ss     0:00 /usr/bin/sudo -E -S -p GNOME_SUDO_PASS -u root /usr/bin/ubiquity gtk_ui
 8478 ?        S      0:00 udisks --inhibit -- /usr/lib/ubiquity/bin/ubiquity gtk_ui
 8481 ?        Sl     0:01 /usr/bin/python /usr/lib/ubiquity/bin/ubiquity gtk_ui
 8484 ?        S      0:00 /bin/cat
 8486 ?        S      0:00 /usr/bin/python /usr/bin/zeitgeist-datahub
 8500 ?        S      0:00 gnome-pty-helper
 8501 pts/1    Ss+    0:00 tail -f /var/log/installer/debug -f /var/log/syslog -q
 9388 ?        S      0:00 /usr/bin/perl -w /usr/bin/debconf-communicate -fnoninteractive ubiquity
 9407 ?        S      0:00 log-output -t ubiquity --pass-stdout sh -c /usr/share/ubiquity/activate-dmraid && /bin/partman
 9408 ?        S      0:00 sh -c /usr/share/ubiquity/activate-dmraid && /bin/partman
 9414 ?        S      0:00 /bin/sh /bin/partman
 9527 ?        S      0:00 parted_server
 9736 ?        S      0:00 /bin/sh /lib/partman/display.d/10initial_auto
 9757 ?        S      0:00 /bin/sh /lib/partman/display.d/10initial_auto
 9860 ?        S      0:00 /bin/sh /lib/partman/automatically_partition/50biggest_free/choices
 9864 ?        Rl     0:00 gnome-terminal
 9871 ?        S      0:00 gnome-pty-helper
 9872 pts/2    Ss     0:00 bash
 9925 pts/2    R+     0:00 ps ax
ubuntu@ubuntu:~$ 
```

Sure would like to get this going - it's getting boring with no natty to test!

---

### Post by MWaddams on 2011-02-21
> **sgage said:**
> 
 ```
 9414 ?        S      0:00 /bin/sh /bin/partman
 9527 ?        S      0:00 parted_server
 9736 ?        S      0:00 /bin/sh /lib/partman/display.d/10initial_auto
 9757 ?        S      0:00 /bin/sh /lib/partman/display.d/10initial_auto
 9860 ?        S      0:00 /bin/sh /lib/partman/automatically_partition/50biggest_free/choices
ubuntu@ubuntu:~$ 
```


Well, I'd say parted is your problem, probably some device it doesn't like, maybe a corrupt USB stick or something. Might be easier to see if you run 'top'.

I had some problems with the daily builds too, Alpha 2 worked ok though, then just update.

---

### Post by cariboo on 2011-02-21
I just did a re-install due to what I thought was a failing hard drive, the first time, it failed at about 75% because it couldn't access the swap partition, after pulling the side cover off and reseating the sata and power connections, the installation went off without a hitch

---

### Post by sgage on 2011-02-21
> **MWaddams said:**
> I had some problems with the daily builds too, Alpha 2 worked ok though, then just update.

That's what I'll do - I wanted to see the latest and greatest installer-fresh setup, but I guess not this time.

---

### Post by seeker5528 on 2011-02-21
> **cariboo907 said:**
> I just did a re-install due to what I thought was a failing hard drive, the first time, it failed at about 75% because it couldn't access the swap partition, after pulling the side cover off and reseating the sata and power connections, the installation went off without a hitch

I ran into a similar type of a problem. System would complain about not finding a boot disk, then after messing with cabling and stuff would work fine. It later turned out to actually be the hard drive. Somewhere in the neighborhood of 1 to 1.5 months between failures. After the 3rd or 4th time, replaced the drive, haven't seen that computer back since. 

Whatever the issue was it wasn't a type of problem that shows up in the SMART record, which seems to happen more often than it used to 3- 4 years ago compared to older drives that would almost always fail completely, produce some kind of odd noise, or have read/write failures that would show up when doing the long test. Not sure how good the SMART system is at detecting cache errors, I have ran into that a few times too.

Time will tell, would not worry about it *too* much unless it happens again.

Later, Seeker

---

### Post by cariboo on 2011-02-21
This is an older SATA drive, it still also has a 4-pin molex connector, unsed, the cables just don't seem to make a very positive connection when plugged in.

---

### Post by seeker5528 on 2011-02-21
> **cariboo907 said:**
> This is an older SATA drive, it still also has a 4-pin molex connector,

The drive I was working with wasn't that old, but the power connector did seem loose, also the system had an older power supply, so had to use an adapter to go from the older molex connector to the SATA type connector, that adaptor was replaced with one that fit tighter the second time it was in.

Haven't had many issues with loose molex connectors as far as the whole thing being loose causing an issue, but I have had plenty of issue with the metal posts being loose inside the plastic connector and having to push the wires to make sure the metal posts on the male side of the connection gets fully seated into the female side of the connection. 

If the ends of the metal posts on the male side start to seperate and hang up when you are plugging it in, using some needle nose pliers to pinch them together again does wonders. 

Later, Seeker

---

### Post by VMC on 2011-02-21
> **sgage said:**
> I decided to start my testing with a fresh install, and find that the installer is not working for me. It gets as far as "Preparing to Install", and when I click on "forward", it just sits there forever with the animated cursor going. But it never moves beyond that.

TIA

I've been so troubled by my nvidia not working that I forgot about the last two ISO sessions. I get the exact same results as you do. I doubt its your HD since we both experience the exact same issue.

I was able to install Lucid 10.04.2 on another partition, so its more than likely ubiquity errors.

---

### Post by nm_geo on 2011-02-21
> **VMC said:**
> I've been so troubled by my nvidia not working that I forgot about the last two ISO sessions. I get the exact same results as you do. I doubt its your HD since we both experience the exact same issue.

I was able to install Lucid 10.04.2 on another partition, so its more than likely ubiquity errors.

I would agree with VMC.  I had the same issue and eventually I installed the Feb 2, Alpha2 Natty and did all the updates.  When it appeared I had a possible HD problem; I installed Maverick in the same partition I had planned for my second Natty. It worked just fine.

Now, I have two working Natty versions on this laptop. There have been some ubiquity bugs and some parted ones too with the daily iso builds. Try the Alpha2 Feb 2nd download and get ready to updates 200 or 300 files or more.:D

---

### Post by cariboo on 2011-02-22
I should add that I used the Feb. 18th daily live image, and I'm using nouveau with libgl1-mesa-dri-experimental on a 9400GT.

---

### Post by sgage on 2011-02-22
> **VMC said:**
> I've been so troubled by my nvidia not working that I forgot about the last two ISO sessions. I get the exact same results as you do. I doubt its your HD since we both experience the exact same issue.

I was able to install Lucid 10.04.2 on another partition, so its more than likely ubiquity errors.

That's my impression. I installed Alpha 2 without any problems yesterday to the same partitions on the same drive, using the same USB stick, created with the same utility. I really doubt it's a HD issue.

---

### Post by Yahoé on 2011-02-22
I experience the same problem with Ubiquity locking on the first screen, but only for the past three dailies, 22, 21 and 19 February. The 18th February works fine so this is a bug according to me.I'll see if there is a bug report opened for this.

---

### Post by sgage on 2011-02-22
> **Yahoé said:**
> I experience the same problem with Ubiquity locking on the first screen, but only for the past three dailies, 22, 21 and 19 February. The 18th February works fine so this is a bug according to me.I'll see if there is a bug report opened for this.

Thanks for checking into it. I never experienced this bug before the 19th, either.

---

### Post by VMC on 2011-02-26
Ubiquity still fails using todays ISO -daily-live [current-20110226].

Here's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/723990") on the subject. Please me too it.

---

### Post by jerrylamos on 2011-02-26
I've been testing Natty install right along, zsync from Daily Build and make bootable USB.  For the last several days cannot do an install:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/723990](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/723990)

Install gets to the point where it should be finding the existing partitions, there are three on two hard drives, then sits there cycling forever.  What's installed already are a 10.04, 10.10, and this 11.04 Alpha 2 updated.

I think I saw elsewhere there is supposed to be an update on Monday.....

Jerry

---

### Post by VMC on 2011-02-26
> **jerrylamos said:**
> I've been testing Natty install right along, zsync from Daily Build and make bootable USB.  For the last several days cannot do an install:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/723990](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/723990)

Install gets to the point where it should be finding the existing partitions, there are three on two hard drives, then sits there cycling forever.  What's installed already are a 10.04, 10.10, and this 11.04 Alpha 2 updated.

I think I saw elsewhere there is supposed to be an update on Monday.....

Jerry

I think this is the culprit here that's causing all our troubles. Prior to this change ubiquity worked. From natty changes:
```
ubiquity (2.5.18) natty; urgency=low

  * Automatic update of included source packages: partman-auto
    93ubuntu6.

Date: Thu, 24 Feb 2011 17:54:41 -0600
```

Also from natty changes, I don't see any activity for ubiquity.

---

### Post by williejones on 2011-02-26
This also happens to me with 64 bit amd desktop 2-23 and 2-25.  I am trying to install to USB from CD and DVD.  It just sits on "Preparing to Install".  I have added a comment and "Me too" to your bug report.  Intel I915 Video.

---

### Post by VMC on 2011-02-28
Using todays ISO [20110228], same result. Fails at installing ubuntu.

---

### Post by jerrylamos on 2011-02-28
Today's daily build 28 Feb same problem, hangs endlessly.

Went back to last previous .iso I had laying around, 12 Feb.  Installed fine, no hang at all, now doing updates.

My experience over years with Alpha & Beta:

1. New install shows up bugs that just updates don't

2. After weeks of updates dies.

So I like to frequently try a new update looking for bugs.

Jerry

---

### Post by jppr on 2011-02-28
[https://launchpad.net/ubuntu/natty/+source/ubiquity/2.5.19](https://launchpad.net/ubuntu/natty/+source/ubiquity/2.5.19)

---

### Post by sparker256 on 2011-02-28
> **VMC said:**
> Using todays ISO [20110228], same result. Fails at installing ubuntu.
Workaround

Make a usb thumb drive using startup disk creator using todays daily ISO with some persistence room. Boot thumb drive and pick try with out installing. Use Update manager to get the new ubiquity 2.5.19. Now reboot and see if it will installs correctly.

Bill

---

### Post by KegHead on 2011-02-28
Hi!

Workaround actually works.

KegHead

---

### Post by VMC on 2011-02-28
> **sparker256 said:**
> Workaround

Make a usb thumb drive using startup disk creator using todays daily ISO with some persistence room. Boot thumb drive and pick try with out installing. Use Update manager to get the new ubiquity 2.5.19. Now reboot and see if it will installs correctly.

Bill

I just tried that a few hours ago. Actually I tried updating ubiquity to 2.5.19,  and it said I was using the latest.

Maybe it came through after I tried. I let you know. thanks!

EDIT:

Didn't work:

```
ubuntu@ubuntu:~$ sudo apt-get install ubiquity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]**ubiquity is already the newest version.**[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ ubiquity --version
[COLOR=Red]**2.5.18**[/COLOR]

ubuntu@ubuntu:~$** sudo apt-get purge ubiquity**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubiquity* ubiquity-frontend-gtk*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 15.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126771 files and directories currently installed.)
Removing ubiquity ...
Purging configuration files for ubiquity ...
Removing ubiquity-frontend-gtk ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
ubuntu@ubuntu:~$ **sudo apt-get install ubiquity**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude bogl-bterm libboost-iostreams1.42.0 libcwidget3 tasksel
  tasksel-data ubiquity-frontend-debconf
Suggested packages:
  aptitude-doc-en aptitude-doc debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude bogl-bterm libboost-iostreams1.42.0 libcwidget3 tasksel
  tasksel-data ubiquity ubiquity-frontend-debconf
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,763 kB of archives.
After this operation, 27.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main libboost-iostreams1.42.0 amd64 1.42.0-4ubuntu2 [55.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty/main libcwidget3 amd64 0.5.16-3ubuntu2 [445 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ natty/main aptitude amd64 0.6.3-3.2ubuntu1 [2,372 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ natty/main tasksel-data all 2.88ubuntu3 [8,580 B]
Get:5 http://archive.ubuntu.com/ubuntu/ natty/main tasksel all 2.88ubuntu3 [33.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ natty/main bogl-bterm amd64 0.1.18-4 [31.2 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ natty/main ubiquity-frontend-debconf all 2.5.18 [800 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ natty/main ubiquity amd64 2.5.18 [4,017 kB]
Fetched 7,763 kB in 1min 25s (91.2 kB/s)                                                                                    
Preconfiguring packages ...
Selecting previously deselected package libboost-iostreams1.42.0.
(Reading database ... 126181 files and directories currently installed.)
Unpacking libboost-iostreams1.42.0 (from .../libboost-iostreams1.42.0_1.42.0-4ubuntu2_amd64.deb) ...
Selecting previously deselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3ubuntu2_amd64.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.3-3.2ubuntu1_amd64.deb) ...
Selecting previously deselected package tasksel-data.
Unpacking tasksel-data (from .../tasksel-data_2.88ubuntu3_all.deb) ...
Selecting previously deselected package tasksel.
Unpacking tasksel (from .../tasksel_2.88ubuntu3_all.deb) ...
Selecting previously deselected package bogl-bterm.
Unpacking bogl-bterm (from .../bogl-bterm_0.1.18-4_amd64.deb) ...
Selecting previously deselected package ubiquity-frontend-debconf.
Unpacking ubiquity-frontend-debconf (from .../ubiquity-frontend-debconf_2.5.18_all.deb) ...
Selecting previously deselected package ubiquity.
Unpacking ubiquity (from .../ubiquity_2.5.18_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
Setting up libboost-iostreams1.42.0 (1.42.0-4ubuntu2) ...
Setting up libcwidget3 (0.5.16-3ubuntu2) ...
Setting up aptitude (0.6.3-3.2ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up bogl-bterm (0.1.18-4) ...
Setting up tasksel-data (2.88ubuntu3) ...
Setting up tasksel (2.88ubuntu3) ...
Setting up ubiquity-frontend-debconf (2.5.18) ...
Processing triggers for python-central ...
**Setting up ubiquity (2.5.18) **...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...

```

I noticed you said daily. I've been downloading daily-live and not daily. Hopefully 2.5.19 will appear in tomorrows daily-live.

---

### Post by sparker256 on 2011-02-28
> **VMC said:**
> I just tried that a few hours ago. Actually I tried updating ubiquity to 2.5.19,  and it said I was using the latest.

Maybe it came through after I tried. I let you know. thanks!


I noticed you said daily. I've been downloading daily-live and not daily. Hopefully 2.5.19 will appear in tomorrows daily-live.

This is where I got my ISO from.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Your thumb drive using 022811 ISO said that 2.5.19 was the latest? When I looked before updating my thumb drive is said 2.5.18. Just not sure what could be different.

Bill

---

### Post by VMC on 2011-02-28
OK, I was able to get it installed. Also my scrambled display is now fixed. I check the current against the one I downloaded early this morning. They don't match . My 20110228 ISO is from 07:25AM, they uploaded a newer one at 11:06PM. That one now works. Normally ISO's don't get uploaded twice in one day.

Thanks for the news.

---

### Post by mc4man on 2011-02-28
> Hopefully 2.5.19 will appear in tomorrows daily-live. 
likely will, though todays was installable here w/ basically the method as sparker256 mentioned (didn't use persistence
just going > try > enable and_ update sources_, > upgrade ubiquity to 2.5.19
The click on icon failed, running the icon's launch command in terminal worked fine

Unfortunately here with nvidia cards the recent iso's are continuing to boot to and produce installs w/ the older icon set and no way to change to Ubuntu-Mono-Dark (Mono_Dark is set as default on install
see screen
 (been doing this for a few weeks
maybe intended, can't change here

Edit - finally an iso that uses the mono dark - 03/01 - worth installing

---

### Post by VMC on 2011-02-28
Maybe the OP will come back and mark this topic as solved. As of the latest *current* ISO now works.

---

### Post by jerrylamos on 2011-02-28
Yes, mark the launchpad bug #723990 as fixed.  The second iso from today had ubiquity 2.5.19 which worked.

From the USB stick, the Unity 3D "Applications" hung up.  Wouldn't work at all.  I started a terminal and from command line issued "synaptic" then did a search on ubiquity and verified the 2.5.19 level.

Thanks much, all.

Jerry

---

### Post by sgage on 2011-02-28
> **VMC said:**
> Maybe the OP will come back and mark this topic as solved. As of the latest *current* ISO now works.

Done!

---

### Post by Yahoé on 2011-03-01
[SIZE=2]Tried to install twice with the latest daily (28th February), but install get stuck at 75 %.
Separate btrfs /boot partition, btrfs /, my usual set-up.
Updated Ubiquity to 2.5.21 but still have the same problem.[/SIZE]

---

### Post by t1497f35 on 2011-03-01
Try ext4 instead. Like 2 weeks ago there were hints btrfs on / might be ready in a few days, but it's still quiet. Possibly it'll be delayed for 11.10.

---

### Post by jerrylamos on 2011-03-01
> **Yahoé said:**
> [SIZE=2]Tried to install twice with the latest daily (28th February), but install get stuck at 75 %.
Separate btrfs /boot partition, btrfs /, my usual set-up.
Updated Ubiquity to 2.5.21 but still have the same problem.[/SIZE]

I'm having much better luck with 01 March 18:44.

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

Jerry

---

### Post by Yahoé on 2011-03-01
I've been using btrfs on / for months now and it's working very nicely. I also have a running system with a btrfs /boot partition, and btrfs /, so btrfs shouldn't be the issue. The last installable daily is 18 February for me.  Ubiquity just got updated to 2.5.22, will give it w try and see if installation completes. Well that did not change anything.
Just downloaded and tryied a fresh install with the latest Natty daily 2nd march 2011, and Ubiquity still gets stuck at about 75% of the system installation process. So this is definitely not working with my setup.

---

### Post by BackwardsDown on 2011-03-02
> I decided to start my testing with a fresh install, and find that the installer is not working for me. It gets as far as "Preparing to Install", and when I click on "forward", it just sits there forever with the animated cursor going. But it never moves beyond that.

I'm still having this problem with the daily build from 2 March.

---

### Post by VastOne on 2011-03-08
March 7 daily and still no luck for me, 75% done and the install quits

---

### Post by kuvanito on 2011-03-08
I had the same problem for a week
I solved my problem by disconeccting the internet and installed no problem,then I did the updates and I've been happy ever since.
Second to that,try a different Hard Drive,it once solved a problem for me too.

---

### Post by VMC on 2011-03-08
> **kuvanito said:**
> I had the same problem for a week
I solved my problem by disconeccting the internet and installed no problem,then I did the updates and I've been happy ever since.
Second to that,try a different Hard Drive,it once solved a problem for me too.
I always unplug the Internet, right after it determines my location. Otherwise it takes forever to complete.

---

### Post by sgage on 2011-03-09
Hello all,

I just tried a fresh installation of natty and had the same problem with it getting stuck at the "preparing to install" page. I was trying to install to a partition I'd prepared using Windows 7 disk manager, the way I've done for years on this dual-boot machine. I have found a workaround:

Get to the Live Desktop, run gparted, delete the Windows created partition(s), and make whatever partitions you need using gparted. Then fire up the installer, and it behaves just fine.

Wish I'd figured this out a while ago... :(

---

### Post by VastOne on 2011-03-09
> **sgage said:**
> Hello all,

I just tried a fresh installation of natty and had the same problem with it getting stuck at the "preparing to install" page. I was trying to install to a partition I'd prepared using Windows 7 disk manager, the way I've done for years on this dual-boot machine. I have found a workaround:

Get to the Live Desktop, run gparted, delete the Windows created partition(s), and make whatever partitions you need using gparted. Then fire up the installer, and it behaves just fine.

Wish I'd figured this out a while ago... :(

I wish it were that simple... :o

I do not have a windows created partition.. I have my standard setup that has worked perfectly (and still does) on every install except Ubuntu Natty

sda
sda1 = /
sda2 = /home
sda3 = swap
sda4 = /media/storage

all are ext4. sda1,2 and 3 are all removed and recreated (which means deleted and reformatted) , sda4 is a simple mount

The bizarre thing is, Xubuntu Natty installs fine on the same setup as does everything before Ubuntu Natty

For me, I had to re install Maverick and upgrade to Natty, it was ugly and painful, but it got me there

---

### Post by sgage on 2011-03-09
VastOne,

I think we have been experiencing different issues. I wasn't having a problem getting past 75%... I never got past "preparing to install ubuntu"!

Hopefully your issue will be adressed soon.

---

### Post by VastOne on 2011-03-09
> **sgage said:**
> VastOne,

I think we have been experiencing different issues. I wasn't having a problem getting past 75%... I never got past "preparing to install ubuntu"!

Hopefully your issue will be adressed soon.

Only in that they both appear to be gparted related...

Thanks, I hope it is resolved soon as well

---

### Post by snoopy-2009 on 2011-03-09
so have we come to a conclusion on which daily live to use? im waiting on my spash screen to load, i let it load while i went grocery shopping, came back in an hour and it actually loaded.. hung on the same "preparing to install" screen, so i rebooted once again, to attempt some o the workarounds mentioned on this thread. i dont seem to think it should take this long to load, none o my previous installs took this long..? im using the natty-desktop-amd64.iso (alpha 3)  any suggestions on iv i should try a divverrnt one?

---

### Post by snoopy-2009 on 2011-03-15
**so.. this is marked solved. so is not getting anymore attention.. ? this problem has NOT been fixed, NOR is there a workaround for everyone! **

My pc still will not let me get past that screen. Im at the conclusion, its because of the windows partition on my hdd. which i cannot remove, without losing all my data, and do not have enough removable media to back it all up, and reinstall it all. ive tried all of the "workarounds" with no success. ive even booted up natty install with my primary hdd unpluged, and natty installer makes it into the partitioner just fine, with out it. but will not let me install onto that hdd whatsoever!

---

### Post by VMC on 2011-03-15
> **snoopy-2009 said:**
> **so.. this is marked solved. so is not getting anymore attention.. ? this problem has NOT been fixed, NOR is there a workaround for everyone! **

My pc still will not let me get past that screen. Im at the conclusion, its because of the windows partition on my hdd. which i cannot remove, without losing all my data, and do not have enough removable media to back it all up, and reinstall it all. ive tried all of the "workarounds" with no success. ive even booted up natty install with my primary hdd unpluged, and natty installer makes it into the partitioner just fine, with out it. but will not let me install onto that hdd whatsoever!

This was marked "solved" by the OP. This error was fixed for me using amd64. Since I'm still subscribed to the bug report, I still see folks having troubles. What is the ISO name you using?

For example:

[" natty-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso") 15-Mar-2011 08:22  695M"

---

### Post by sgage on 2011-03-16
> **VMC said:**
> This was marked "solved" by the OP. This error was fixed for me using amd64. Since I'm still subscribed to the bug report, I still see folks having troubles. What is the ISO name you using?

For example:

[" natty-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso") 15-Mar-2011 08:22  695M"

I am the OP. I marked it "solved", because it was - temporarily. Then I figured out a couple of workarounds (described upthread). They, too, only worked on one day's build. The last build I was able to install was 3/8. I have just now marked the thread "unsolved".

Curiously, the CD I burned for 3/8 boots directly to the desktop rather than offering choices to try or install, etc. I wonder what's up with that...

---

### Post by mc4man on 2011-03-16
> **sgage said:**
> I am the OP. I marked it "solved", because it was - temporarily. Then I figured out a couple of workarounds (described upthread). They, too, only worked on one day's build. The last build I was able to install was 3/8. I have just now marked the thread "unsolved".

Curiously, the CD I burned for 3/8 boots directly to the desktop rather than offering choices to try or install, etc. I wonder what's up with that...

Well todays (03/16) iso, which includes the new ubiquity, also only boots to desktop, unfortunately ubiquity then fails completely and never starts up (i386

Edit - [fix committed on that]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/736060") - maybe tomorrows live cd will work

Tested the new ubiquity - 2.5.27 with todays iso - works fine. So probably the iso's tommorrow - 03/17 should work well (should also have new gdm in them

---


---
title: "Intel graphics worries"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-09-21
Since the 16th all dailies fail with my Hanns-G saying "out of range". I'm using Intel integrated 82945G/GZ.

I have an older set of hardware with a VIA P4M800 and it also fails with the Hanns-G, but works OK with a 17" CRT.

My Intel will not work even with the 17" CRT. It displays no error, but there is no display.

So, I'm thinking six days with a broken X I should maybe file a bug. But filing an X bug is horrendous!

And maybe it's not X, maybe it's a kernel thing.

Anyone else sharing this problem?

Maybe if we discuss it we can figure out what's up :)

Any thoughts?

I'm also quite busy so it may take quite a while for me to reply.

---

### Post by cariboo on 2010-09-21
An **out of range error** means that the frequency isn't set right. Have you tried creating an /etc/X11/xorg.conf file?

At the prompt type:

```
Xorg -configure
```

This will create an xorg.conf file in your home directory, you have to then copy it to /etc/X11.

This may get you a working desktop. I would check the horizontal and vertical refresh rates before trying to boot to the desktop, make sure they match what the manufacturer specified.

---

### Post by kansasnoob on 2010-09-22
> **cariboo907 said:**
> An **out of range error** means that the frequency isn't set right. Have you tried creating an /etc/X11/xorg.conf file?

At the prompt type:

```
Xorg -configure
```

This will create an xorg.conf file in your home directory, you have to then copy it to /etc/X11.

This may get you a working desktop. I would check the horizontal and vertical refresh rates before trying to boot to the desktop, make sure they match what the manufacturer specified.

Sorry, I wasn't very clear in my OP. I'm having that trouble with the Live CD's.

I have a fully updated 10.10 installed and it's running just fine.

So far I have only tried booting the Live CD w/nomodeset and also with "quiet splash" removed. Doing the latter does at least give me a tty :)

I may fiddle around a bit more this evening.

---

### Post by perspectoff on 2010-09-22
There are several threads on this problem. Hunt around a little bit more.

Here is the solution I use:

[http://ubuntuforums.org/showthread.php?p=9830905#post9830905](http://ubuntuforums.org/showthread.php?p=9830905#post9830905)

---

### Post by kansasnoob on 2010-09-22
> **perspectoff said:**
> There are several threads on this problem. Hunt around a little bit more.

Here is the solution I use:

[http://ubuntuforums.org/showthread.php?p=9830905#post9830905](http://ubuntuforums.org/showthread.php?p=9830905#post9830905)

No doubt I can find a work-around. That's not the point of my thread. As I said:

> So, I'm thinking six days with a broken X I should maybe file a bug.

I'm guessing that the devs would want to know that recent changes have had a negative effect :)

This same hardware has worked quite well with all Ubuntu since Hardy, including Maverick Beta, so it's either due to a recent change in Xorg or something with how the kernel itself handles Xorg config.

I just like to discuss things here before filing a bug report. Xorg bugs can be a real bear :(

This one is quite similar:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/529387](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/529387)

But it's quite hardware specific and it's also for Lucid.

FYI I have done a lot of Googling, as much as time allows, I just like to try and be thorough in my testing and try to get as many bugs as possible filed and hopefully fixed during testing.

---

### Post by kansasnoob on 2010-09-22
Just out of curiosity I now tried adding "i915.modeset=1" to the Live CD kernel boot parameters and it was still a no-go :(

I'm thinking I might try the 22nd daily on Live USB which has a separate Data partition. I have a custom xorg.conf that allows me to obtain a 1440X900@60 resolution, so if I save it to the data partition, I should be able to muck around in the TTY, move it to etc/X11, and try starting X from the TTY.

Or I might try this:

[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

> Testing with a live CD/media

This is the safest way of testing. Download the xorg-edgers-live-test script from the Xorg packaging tools repository and copy it to a Ubuntu Desktop CD (I suppose you are using a bootable USB stick to avoid burning CDs anyway). Then boot the CD/media, switch to a virtual console with ctrl-alt-F1 and type:

sudo sh /cdrom/xorg-edgers-live-test

and it will automatically download the packages from the "xorg crack testers" team, build kernel modules and restart X, all inside the "live" session without touching your hard drive.

I've had some luck in the past with xorg edgers :)

That should help at least troubleshoot exactly what's happening.

---

### Post by kansasnoob on 2010-09-23
Before heading off to bed I decided to give my update logs & the xorg changelogs a closer look:

> Commit Log for Mon Sep 13 15:19:23 2010
...............................
xserver-xorg-video-intel (2:2.12.0-1ubuntu3) to 2:2.12.0-1ubuntu4

And:

> Commit Log for Thu Sep 16 07:46:36 2010
...............................
xserver-common (2:1.9.0-0ubuntu5) to 2:1.9.0-0ubuntu6
xserver-xorg-core (2:1.9.0-0ubuntu5) to 2:1.9.0-0ubuntu6

And:

> Commit Log for Fri Sep 17 07:16:56 2010
...............................
xserver-common (2:1.9.0-0ubuntu6) to 2:1.9.0-0ubuntu7
xserver-xorg-core (2:1.9.0-0ubuntu6) to 2:1.9.0-0ubuntu7


So, I guess it's time to do a Beta Live USB and update only those specific packages :)

Oops, fell asleep in front of the keyboard again, this desk-chair is too darn comfy.

---

### Post by kansasnoob on 2010-09-23
Errrrm :confused:

Still testing here and I'm glad I posted what I did last night, specifically:

> Commit Log for **[COLOR="Red"]Mon Sep 13[/COLOR]** 15:19:23 2010
...............................
xserver-xorg-video-intel (2:2.12.0-1ubuntu3) to 2:2.12.0-1ubuntu4 

I was testing updates in a live USB and always got this:

> server-xorg-video-intel (2:2.12.0-1ubuntu4) maverick; urgency=low

  * debian/patches/101_copy-fb.patch: Explicitly disable copyfb functionality
    on gen6 (Sandybridge) where it is not working.
  * Update Sandybridge device id's. (LP: #632488)

 -- Robert Hooker <robert.hooker@canonical.com>  **[COLOR="Red"]Fri, 10 Sep 2010[/COLOR]** 07:39:32 -0400

I must sort some cobwebs from my old noggin :confused:

I get the same thing with my installed Maverick now so I suppose I need to wait until tomorrow and try a new daily.

I am curious how a changelog can just delete a previous change from the record?

I'd think if they roll something back they'd reflect that in the changelog :)

---

### Post by kansasnoob on 2010-09-24
Arrrrgh, cobwebs indeed :(

I must have just been tired, the devs didn't alter the changelogs, I was suffering from optical rectitis :)

I should have time to study this a bit more today, of course I'll begin by testing the new daily.

Next I'll check that Live USB just to be sure all xorg packages are properly updated. If so, and I think they are, then I'm leaning towards it being kernel related.

But I don't think it's possible to upgrade or downgrade the kernel in a Live USB :confused:

---

### Post by kansasnoob on 2010-09-24
Hmmm, I may be wrong about kernel upgrades in a Live USB:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489736](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489736)

I guess there's only one way to find out. Maybe I could even try the mainline kernel.

Or, if I'm lucky, todays daily will just work.

---

### Post by kansasnoob on 2010-09-24
No luck with todays daily but I've done a bit more studying. One thing I did figure out was that old 17" CRT failing from time to time was completely unrelated - it was due to a bad cable connection which I've now fixed. So, just to recap:

1) My old VIA P4M800 which uses the "openchrome" driver works just fine with either the 17" CRT or the 22" LCD.

2) My Intel 82945G/GZ (aka: i945) works fine with the 17" CRT, but fails with that "out of range" error using the 22" LCD. Questions about reading the Xorg.0.log will follow :)

3) I have 3 different Mavericks installed on this Intel machine. One that's fully updated daily & dates back to May 22nd, the other two leftover from Beta upgrade and iso testing. They, and the Beta Live CD, all boot just fine (by default to 1680X1050@61Hz).

4) This began on or around the 16th. I normally don't follow the dailies that closely other than in a VM but I've had several concerns regarding the new ubiquity so I've been watching very closely.

5) The Intel i945 has not typically been one of those effected by this:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Which is largely what I think perspectoff was referring to here:

[http://ubuntuforums.org/showthread.php?p=9830905#post9830905](http://ubuntuforums.org/showthread.php?p=9830905#post9830905)

Regardless adding "i915.modeset=1" to the Live CD boot option doesn't work, either with or without "quiet splash".

6) The only way I can get a TTY is by booting w/o "quiet splash". Once the monitor spits out "out of range" I'm totally in the dark :(

7) **[COLOR="Red"]Most importantly[/COLOR]** I'm really outside my "comfort zone" here. I've only had one other actual Xorg problem/bug in the past and I never did figure it out, but it's totally unrelated to this. (Just as a matter of being "complete" in my explanation it involved X freezes w/VIA openchrome in Karmic).

**[COLOR="Red"]Finally[/COLOR]** I have mucked around enough that I should now know how to transfer the Live CD's  /var/log/Xorg.0.log to my USB drive:

"sudo cp /var/log/Xorg.0.log /media/DATA/var/log/Xorg.0.log"

Laugh if you like but it's not particularly easy for my old brain to sort these things out with no GUI. I'm commonly a "copy-n-paster" :)

But I don't really know how to read the Xorg.0.log, and I'm still trying to sort out which other files might be helpful. This was largely just a huge, "I hope someone else is an xorg bug filing pro" thread :)

I am looking at the "info requested" parts of this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/529387](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/529387)

But an xorg pro sure would be cool right now :)

---

### Post by kansasnoob on 2010-09-24
I decided that I'll repeat some Live USB tests this evening regarding updates.

Tomorrow I'll probably be tied up, but Sunday I'll return to this and try the new daily. If it's still a no-go I'll file a bug report.

I'm not even sure how to title the bug or whether to assign it to x or the kernel.

I guess it's time to just shoot from the hip :)

---

### Post by perspectoff on 2010-09-24
> **kansasnoob said:**
> Just out of curiosity I now tried adding "i915.modeset=1" to the Live CD kernel boot parameters and it was still a no-go :(


yeah, that didn't work for me either, and is not the advice I gave.

It's 

i915.modeset=0

The guy who wrote the original thread said

i915.modeset=1 didn't work for him, either.

---

### Post by kansasnoob on 2010-09-25
My bad, if I use "i915.modeset=0" that just drops me to a TTY, and if I try startx I just get:

> Fatal server error:
no screens found

If I use "i915.modeset=1" I still just get that "out-of-range" error.

I'm at the point where I think I'll just file a bug report using my installed, up-to-date Maverick, and then try to add info from the non-X Live CD by booting w/o quiet-splash which will dump me to a TTY, and typing "apport-collect bug_number".

I just haven't quite made up my mind what package to file it against, I'm leaning towards "xserver-xorg-video-intel". I'll think some more about it today and try it tomorrow.

Somehow I think this is only non-directly an X-bug. All three of my installed Mavericks boot w/o tinkering, and updating only the xorg/xserver packages on a Live USB do NOT break X on boot.

Ultimately it's going to take someone much smarter than I to figure it out.

---

### Post by kansasnoob on 2010-09-25
Good stuff here:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

And looking at my commit logs I see that I upgraded "linux-libc-dev" on the 16th, then installed kernel "2.6.35-22" on the 17th. I sure wish I'd kept an iso with "2.6.35-21" :(

In the future I'm going to start copying my older iso's for a few days with a date extension. If only foresight were as good as hind sight.

I'm thinking that trying to downgrade the kernel in a daily Live USB would be nightmarish but I might try upgrading a Beta Live USB from "2.6.35-19" to "2.6.35-22". I fear the dreaded failed initrd error on reboot though.

At any rate I think I'll file the bug report against "linux" with the "xorg-needs-kernel-fix" tag. I'll give it a whirl either tonight or tomorrow :)

I know this'll sound nuts, but I've had very little time to spend on testing the past few months and this is the most fun I've had in a long time.

---

### Post by MacUntu on 2010-09-26
Long shot, you're maybe hit by this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

Easy to find out, just type the following at a tty:
```
sudo -u gdm gconftool-2 --type bool -s "/apps/gnome_settings_daemon/xrandr/turn_on_external_monitors_at_startup" false
```
And reboot (or restart gdm with 'sudo restart gdm').

---

### Post by kansasnoob on 2010-09-27
> **MacUntu said:**
> Long shot, you're maybe hit by this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

Easy to find out, just type the following at a tty:
```
sudo -u gdm gconftool-2 --type bool -s "/apps/gnome_settings_daemon/xrandr/turn_on_external_monitors_at_startup" false
```
And reboot (or restart gdm with 'sudo restart gdm').

You're onto something :)

I've fiddled a lot and I've found that I can get a gui if I start in recovery mode and then choose failsafeX. However, even if I create a known good "xorg.conf", and/or edit either "/etc/gdm/Init/Default" or "/etc/gdm/PreSession/Default", I still get the "out-of-range" error when I restart gdm.

With "turn_on_external_monitors_at_startup" unchecked restarting gdm does bring up my custom settings in either "/etc/gdm/Init/Default" or "/etc/gdm/PreSession/Default", I still need to try an actual reboot though.

What's odd is that I checked gconf in my working Maverick (which is fully updated) and it has "turn_on_external_monitors_at_startup" checked but works fine :confused:

Anyway this is the furthest I've gotten. I have tried twice to file a bug against "linux" using "ubuntu-bug linux" and it asks all the normal questions but then seems to fail at some point in collecting info.

Anyway I'm going to try a full reboot and perhaps compare some "gnome-settings-daemon" files between the working Maverick and the non-working Maverick.

I will certainly leave a comment at that bug report. Many thanks.

Oh, and I have now managed to reproduce this bug in an installed Maverick which has been much easier to troubleshoot than the Live CD or Live USB.

---

### Post by kansasnoob on 2010-09-27
Aaah, tried the reboot and it works :)

Now to gather my thoughts and try to reply in a helpful manner, many thanks again.

Also, something funny, I forgot to send that last message before rebooting. Good thing Firefox saves open tabs :)

---

### Post by kansasnoob on 2010-10-04
Following up on this I filed:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/654660](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/654660)

Which is one of several "duplicates" although as Tormod Volden says here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

> The recent g-s-d change also made bug 641525, bug 645377 and bug 646474  appear, but I am not marking them as duplicates since I believe xorg is generating wrong modes in these cases which should be fixed separately. g-s-d is only at fault for overruling the X server and selecting the bad modes.

This is a widespread bug, effecting a lot of hardware! How can we release with that?

If there ever was a show-stopper this has to be one, eh?

I'm quite busy dealing with unrelated things but I really think QA should get involved in this. At the very least we should come up with a coherent method to deal with both failed upgrades and failed Live CD boots, eh?

---

### Post by KristinaK on 2010-10-04
ubuntu 10.10 doesn't work with intell atom 450

where is fix?

---

### Post by kansasnoob on 2010-10-04
> **KristinaK said:**
> ubuntu 10.10 doesn't work with intell atom 450

where is fix?

Quite honestly I can't imagine someone being more vague :confused:

Exactly what doesn't work?

Are you talking about the Live CD, an install or an upgrade?

Did 10.04 work?

---


---
title: "Unable to boot (usually)"
date: 2011-02-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by afoglia on 2011-02-28
After installing some package last weekend, I am unable to successfully boot about 80% of the time.  Instead, my laptop (an Envy 14) just sits with the screen black.  (I believe it's off, but I could be misremembering.)  In addition, maybe only a a quarter of time it boots, do I see the usplash screen.  Instead, the first graphics I see are gdm.

I've waited up to 15 minutes for a boot to finish, so this is not impatience on my part.

When the boot crashes, it dies before the bootchart is saved (unsurprising.  IS there somewhere old boot logs are rotated to?

I am running off the integrated graphics, not the ATI card, though I do see the radeon module is loaded.  (I would try playing with my xorg.conf, but there's no such file in /etc/X11, and none of the locations listed in the manpage seem to have a conf file, other than the input stuff in /usr/share/X11/xorg.conf.d.)

I meant to reinstall maverick over the weekend, but didn't get around to it.  Any suggestions on how to debug this and offer some help, before I do?

---

### Post by Harry33 on 2011-02-28
> **afoglia said:**
> After installing some package last weekend, I am unable to successfully boot about 80% of the time.  Instead, my laptop (an Envy 14) just sits with the screen black.  (I believe it's off, but I could be misremembering.)  In addition, maybe only a a quarter of time it boots, do I see the usplash screen.  Instead, the first graphics I see are gdm.

I've waited up to 15 minutes for a boot to finish, so this is not impatience on my part.

When the boot crashes, it dies before the bootchart is saved (unsurprising.  IS there somewhere old boot logs are rotated to?

I am running off the integrated graphics, not the ATI card, though I do see the radeon module is loaded.  (I would try playing with my xorg.conf, but there's no such file in /etc/X11, and none of the locations listed in the manpage seem to have a conf file, other than the input stuff in /usr/share/X11/xorg.conf.d.)

I meant to reinstall maverick over the weekend, but didn't get around to it.  Any suggestions on how to debug this and offer some help, before I do?

File /etc/X11/xorg.conf is not needed (and usually does not exist) when an open source driver is in use, in your case xserver-xorg-video-radeon.
What ATI radeon model do you have (integrated into the mobo)?

---

### Post by afoglia on 2011-02-28
> **Harry33 said:**
> File /etc/X11/xorg.conf is not needed (and usually does not exist) when an open source driver is in use, in your case xserver-xorg-video-radeon.
What ATI radeon model do you have (integrated into the mobo)?

It's an ATI Mobility Radeon HD 5650.  And it's a discrete card.  It might be integrated in a hardware sense, but it's referred to everywhere as discrete, and I can shut off power to it while the computer is running.  The integrated graphics come from the Intel Core i5.

---

### Post by afoglia on 2011-02-28
> **Chauncellor said:**
> I've been having the same issue since Natty first came to development. I'm an i915 user. I think there's a problem with the backlight on my part - it will eventually boot and I can see the desktop faintly on the screen at an angle. My workaround has been to connect an external monitor, killing the session (via alt+sysrq+k), then unplugging the monitor (this somehow knocked the system into turning the backlight on for me.)

Are you sure that's not the same backlight issue that occurred in Maverick, as discussed [here]("http://ubuntuforums.org/showthread.php?t=1593079")?  I'm following the suggestion in the thread and put "echo 7 > /sys/class/backlight/acpi_video0/brightness" in my rc.local, and that worked under Maverick.

i915 is the kernel module used by integrated graphics, so I'll check next time I restart, but I'm pretty sure I tried playing with the backlight controls.  (I remember I panicked when the system started up all black when I upgraded from lucid to maverick.)  And this doesn't explain why it only occurs some of the time.

---

### Post by joffe on 2011-03-01
Happens to me as well. Acer TimelineX 3820TG with Core i5-450M and discrete ATI 5650. The radeon module crashes from time to time before reaching gdm. I don't know how or why X chooses the intel graphics but when the radeon module crashes it brings down the whole thing. Sometimes the screen goes black and I can unload the radeon module and restart gdm. Sometimes it shows the radeon stack trace and then the only way to restart is through rseiub.

I have tried both stock natty drivers as well as the xorg-edgers' with the same result...

---

### Post by afoglia on 2011-03-01
> **joffe said:**
> Happens to me as well. Acer TimelineX 3820TG with Core i5-450M and discrete ATI 5650. The radeon module crashes from time to time before reaching gdm. I don't know how or why X chooses the intel graphics but when the radeon module crashes it brings down the whole thing. Sometimes the screen goes black and I can unload the radeon module and restart gdm. Sometimes it shows the radeon stack trace and then the only way to restart is through rseiub.

How do you get a prompt?  When this happens to me, I can't even seem to switch virtual consoles.  (I saw "seem to" because again, it may be a brightness issue as well, but even when gdm is running, I can't switch virtual consoles.)

But you're probably right.  The xserver-xorg-video-radeon package was updated on Feb 18 to a new upstream release 6.14.0 (from 6.13.2), and that was roughly when this problem began for me.  From my bootcharts, my system does spend a very long time running modprobe at the beginning, before plymouth starts.

I feel much better now that I know it's not just my system.  What's the stacktrace?

If it wasn't for the new upstream, I'd try learning how to pin the driver to maverick version.  If that's possible, natty might be nearly usable.

---

### Post by joffe on 2011-03-01
> **afoglia said:**
> How do you get a prompt?  When this happens to me, I can't even seem to switch virtual consoles.  (I saw "seem to" because again, it may be a brightness issue as well, but even when gdm is running, I can't switch virtual consoles.)

I don't :)
Alt+F1 and then I have to log in blindly and trust my fingers not to slip while typing... Sometimes this approach works, sometimes not.

> **afoglia said:**
> But you're probably right.  The xserver-xorg-video-radeon package was updated on Feb 18 to a new upstream release 6.14.0 (from 6.13.2), and that was roughly when this problem began for me.  From my bootcharts, my system does spend a very long time running modprobe at the beginning, before plymouth starts.

I feel much better now that I know it's not just my system.  What's the stacktrace?

If it wasn't for the new upstream, I'd try learning how to pin the driver to maverick version.  If that's possible, natty might be nearly usable.

I haven't had time to look into any stack traces yet but if you or anyone else here know where to look for them and where to file a bug report I will gladly do that.

---

### Post by Harry33 on 2011-03-01
> **afoglia said:**
> 
...
I still have problems booting in the recovery mode, which, if it's anything like it was in the usplash days, won't hide the boot messages with a pretty picture.

Not sure what you mean by that sentence.

But for clarity reasons for those users that do not know this issue well:
- recovery mode only boots in a text mode (verbose mode) showing all messages. It does not show any splash nor plymouth pictures.
- if a package friendly recovery is installed (default: it is installed), recovery mode ends up showing a small window with several options to choose from (one of which is boot into "low graphics mode", and one widely used option is "drop to console with networking").
- recovery mode with dropping into console option does not need any graphics drivers at all.
- recovery mode with booting into low graphics mode uses vesa driver (xserver-xorg-video-vesa), not the actual graphics drivers built for specific graphics cards (like xserver-xorg-video-radeon for ATI Radeon cards).

To be able to show Plymouth, the system indeed needs graphics drivers.
It is also possible that Plymouth shows OK, but X segfaults (no gdm, login window either). This is also due to incompatibility issues of graphics drivers (like ABI).

---

### Post by afoglia on 2011-03-01
> **joffe said:**
> I don't :)
Alt+F1 and then I have to log in blindly and trust my fingers not to slip while typing... Sometimes this approach works, sometimes not.


Alt+F1?  Not Ctrl+Alt+F2?  Are you logging into Gnome (or some other wm)?  Then just "sudo rmmod radeon" and "/etc/init.d/gdm restart" I assume?  I want to get this right if I dare try to restart, especially if I'm going to be typing blind.

> I haven't had time to look into any stack traces yet but if you or anyone else here know where to look for them and where to file a bug report I will gladly do that.

I must have misunderstood you.  I thought you said you had a radeon stack trace.  As for where to file a bug report, I'd say both in Ubuntu under the [xserver-xorg-video-ati package]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bugs"), and with [the X.org radeon project]("http://wiki.x.org/wiki/radeon").  I checked, and didn't see anything related to the 5650 card directly, or any new bug reports that sounded similar.  (I would normally suggest only one, but this is a major issue, and should be fixed before natty is released.)

Let me know when you do, and I'll sign up to follow the issues.  (Otherwise I'll make the bug reports myself tonight.)

---

### Post by joffe on 2011-03-01
Since X won't start Alt+F1 is sufficient for switching. Then login, sudo rmmod radeon, sudo restart gdm

---

### Post by afoglia on 2011-03-01
> **Harry33 said:**
> Not sure what you mean by that sentence.

I meant what you said in your first bullet point.  You get to see the actual boot messages.  (I didn't mean to sound snippy, but plymouth/usplash is nothing but eye candy, which is appreciated 99.9% of the time, but candy nonetheless.)

> But for clarity reasons for those users that do not know this issue well:
- recovery mode only boots in a text mode (verbose mode) showing all messages. It does not show any splash nor plymouth pictures.
- if a package friendly recovery is installed (default: it is installed), recovery mode ends up showing a small window with several options to choose from (one of which is boot into "low graphics mode", and one widely used option is "drop to console with networking").

Now that worries me.  When I've started in recovery mode, I haven't gotten to a menu.  Instead, again the screen goes all black, and nothing happens.  I do have friendly-recovery installed.  I'll be sure to check next time I restart.

> - recovery mode with dropping into console option does not need any graphics drivers at all.
- recovery mode with booting into low graphics mode uses vesa driver (xserver-xorg-video-vesa), not the actual graphics drivers built for specific graphics cards (like xserver-xorg-video-radeon for ATI Radeon cards).

To be able to show Plymouth, the system indeed needs graphics drivers.
It is also possible that Plymouth shows OK, but X segfaults (no gdm, login window either). This is also due to incompatibility issues of graphics drivers (like ABI).

No.  I'm definitely not getting plymouth (in most cases).  Or at least I'm not getting the screen that says kubuntu with the fix dots underneath that slowly blink on and off.  I assume that's plymouth.  It ain't gdm.

---

### Post by Harry33 on 2011-03-02
> **afoglia said:**
> 
...
Now that worries me.  When I've started in recovery mode, I haven't gotten to a menu.  Instead, again the screen goes all black, and nothing happens.  I do have friendly-recovery installed.  I'll be sure to check next time I restart.
...


OK afoglia,
Please note that if recovery mode does not show any text, you have another problem than Plymouth or any graphics driver.
Plymouth is not used during recovery mode and no graphics driver is used during recovery mode.
The recovery mode will show a user-friendly menu at the end. For that, whiptail is used, not any graphics driver.

Xserver-xorg-video-vesa (the vesa drivers) gets pulled in only after you choose
"low graphics mode".

Try reinstalling grub-common and grub-pc and after that run:
```
sudo update-grub
```

Have you modified these files?
/etc/default/grub
/etc/grub.d/00_header

---

### Post by afoglia on 2011-03-02
I finally saw the stack and call trace that joffe mentioned.  I got it one of the half-dozen attempts to boot into recovery mode I made.  I took some photos and made a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620") in launchpad.

I don't think this is all my problems (I had problems before the video driver update), but it is something major.

---

### Post by afoglia on 2011-03-02
> **Harry33 said:**
> OK afoglia,
Please note that if recovery mode does not show any text, you have another problem than Plymouth or any graphics driver.
Plymouth is not used during recovery mode and no graphics driver is used during recovery mode.

You must be mistaken.  I booted into recovery mode tonight a half dozen times, and one time, when the brightness key actually worked, I got a screen of messages of the call stack of the radeon driver.  Here's the photo:
[[IMG]http://i.imgur.com/P0bQ0l.jpg[/IMG]](http://imgur.com/P0bQ0)

And at this point I did not get a prompt or menu or anything.

I have not modified any grub files.

You are probably right that it should not be loaded, and this is another bug, but I can't think of another reason why there would be radeon errors unless radeon was loaded.  Maybe because I have two video chips (discrete and integrated), and that's confusing the recovery.

Anyway, I'm beginning to think the original poster's problem is different, if only because [her boot chart]("http://ubuntuforums.org/showpost.php?p=10440613&postcount=12") doesn't show the 10-second long modprobe process [mine has]("http://ubuntuforums.org/showpost.php?p=10468165&postcount=21").  I feel sorry for commandeering this thread.

---

### Post by Harry33 on 2011-03-02
> **afoglia said:**
> You must be mistaken.  I booted into recovery mode tonight a half dozen times, and one time, when the brightness key actually worked, I got a screen of messages of the call stack of the radeon driver.

No I am not mistaken.
Using recovery mode (chosen from the grub menu only) up to the point where a small window is shown (friendly recovery shows this using whiptail) does not need Plymouth nor does it need Xserver or xserver-xorg-video drivers. If you then choose "drop to shell with net", you still do not need Plymouth nor xserver.

This is the very same situation if you only install ubuntu-minimal (with no desktop and with no xserver).
You end up in console (text mode only).

In fact installing Arch-Linux results exactly to the same situation first. You can then proceed installing desktop and X with drivers.

You should be able to do this even if you removed the graphics drivers.

---

### Post by afoglia on 2011-03-02
I am often unable to boot into recovery mode, and one time in particular I actually saw a call trace for the radeon module.  This was before I got the friendly-recovery menu.

Some people are claiming this is not possible.  Luckily I was taking a [video of the boot]("http://www.youtube.com/watch?v=vPIQrZnhLLs").  And here's a photo of the call trace:
[[IMG]http://i.imgur.com/P0bQ0l.jpg[/IMG]](http://imgur.com/P0bQ0)

Harry33 claims that I've changed my grub configuration.  I have not.  I had no reason to.  Unless dkms does something, the files should be untouched, except for the common update procedure.  At his suggestion I reinstalled grub-common and grub-pc with "sudo apt-get install --reinstall".  No mention of changed configuration files that it wants to rewrite.  I reran update-grub although I'm 99% certain the apt-get reran it.  I haven't tried rebooting, because rebooting this computer under natty is a crapshoot, and I had to sleep and now have to rush to work.

I've attached the results of the [boot_info_script.sh]("http://sourceforge.net/projects/bootinfoscript/").

---

### Post by afoglia on 2011-03-02
> **Harry33 said:**
> No I am not mistaken.
Using recovery mode (chosen from the grub menu only) up to the point where a small window is shown (friendly recovery shows this using whiptail) does not need Plymouth nor does it need Xserver or xserver-xorg-video drivers. If you then choose "drop to shell with net", you still do not need Plymouth nor xserver.

Would you believe a video?  I made [a new thread]("http://ubuntuforums.org/showthread.php?p=10512253") and posted a link to one there.

---

### Post by afoglia on 2011-03-02
joffe, are you able to boot successfully in recovery mode?  Because I am not, and would like to find another data point in support.

---

### Post by Harry33 on 2011-03-02
> **afoglia said:**
> Would you believe a video?  I made [a new thread]("http://ubuntuforums.org/showthread.php?p=10512253") and posted a link to one there.

Afoglia, I am not saying you do not have issues you just described.
What I am saying, your setup is not a common setup, and that recovery mode should not touch plymouth nor xserver.

You may get further by one package at a time uninstalling them.
I suggest you uninstall all xserver-xorg-video-* drivers first, but not vesa (xserver-xorg-video-vesa).
Then try to reboot in recovery mode.

---

### Post by Harry33 on 2011-03-02
> **afoglia said:**
> I am often unable to boot into recovery mode, and one time in particular I actually saw a call trace for the radeon module.  This was before I got the friendly-recovery menu.
...
Some people are claiming this is not possible.
...
Harry33 claims that I've changed my grub configuration.  I have not.  I had no reason to.  Unless dkms does something, the files should be untouched, except for the common update procedure.  At his suggestion I reinstalled grub-common and grub-pc with "sudo apt-get install --reinstall".  No mention of changed configuration files that it wants to rewrite.  I reran update-grub although I'm 99% certain the apt-get reran it.  I haven't tried rebooting, because rebooting this computer under natty is a crapshoot, and I had to sleep and now have to rush to work.
...


Afoglia, there is no need to create a new thread about this.
These should be merged.
And I never said you **did** change grub settings, I did not even suspect it.
All I did was asked **IF** you had done so.
You see it is very hard for me to help you, if you do not want to give decent info.
I think there is nothing wrong step by step removing from the table things that might have gone wrong.

Your setup seems not to be in ordinary condition.
But by all means, proceed as you wish.
Happy testing, after all .:guitar:

---

### Post by afoglia on 2011-03-02
> **Harry33 said:**
> Afoglia, there is no need to create a new thread about this.
These should be merged.

I split it out because both you and the original poster think it's a different problem than hers.  And you've convinced me that it's a bigger issue than the plymouth boot screen issue [the original thread]("http://ubuntuforums.org/showthread.php?t=1697215") is heading for.  As you claim, recovery mode should not be loading any video modules, but this is what I am seeing.  So regardless of whether the video module has an bug, something in my configuration is screwed up.

(Actually you said the graphics module was not loaded.  I said it was and showed you the stack trace, though I agreed it should probably not be.  You still said I was wrong, without any explanation of what I saw with my own eyes.  You did not say it should not be loaded.)

I would hope we could agree on my problems boil down to (a) recovery mode is trying to load the radeon module, though it should not be, and (b) that radeon module is crashing.  My goal here is to focus on (a).

> And I never said you **did** change grub settings, I did not even suspect it.
All I did was asked **IF** you had done so.
You see it is very hard for me to help you, if you do not want to give decent info.
I think there is nothing wrong step by step removing from the table things that might have gone wrong.

Your setup seems not to be in ordinary condition.
But by all means, proceed as you wish.
Happy testing, after all .:guitar:

You asked if I changed my grub configuration.  I have attached the results of the boot_info_script which includes a complete copy of my grub.cfg.  We can argue about whether or whether or not I changed it, but right there is a copy for you or someone else to check for yourself.

I will try rebooting in recovery mode tonight, but in the meantime, while I am at work, I thought maybe someone could see an obvious problem here.  I did not have time this morning to spend a half hour trying to get my laptop up and successfully booted, and not crash while I write a post.

---

### Post by cariboo on 2011-03-02
Instead of having this problem spread over three different threads, I have merged two threads, and moved posts from anohter.

---

### Post by joffe on 2011-03-02
> **afoglia said:**
> You must be mistaken.  I booted into recovery mode tonight a half dozen times, and one time, when the brightness key actually worked, I got a screen of messages of the call stack of the radeon driver.  Here's the photo:
[[IMG]http://i.imgur.com/P0bQ0l.jpg[/IMG]](http://imgur.com/P0bQ0)

And at this point I did not get a prompt or menu or anything.

I have not modified any grub files.

You are probably right that it should not be loaded, and this is another bug, but I can't think of another reason why there would be radeon errors unless radeon was loaded.  Maybe because I have two video chips (discrete and integrated), and that's confusing the recovery.

Anyway, I'm beginning to think the original poster's problem is different, if only because [her boot chart]("http://ubuntuforums.org/showpost.php?p=10440613&postcount=12") doesn't show the 10-second long modprobe process [mine has]("http://ubuntuforums.org/showpost.php?p=10468165&postcount=21").  I feel sorry for commandeering this thread.

That's exactly the same crash I get from time to time, just took a picture of it as well. I don't know how to trigger it though. It might be some race condition that can be avoided somehow.

---

### Post by afoglia on 2011-03-02
I just followed [Harry33's suggestions]("http://ubuntuforums.org/showpost.php?p=10511281&postcount=14") for my grub, and they had no effect.  I ran

```
$ sudo apt-get install --reinstall grub-common grub-pc
$ sudo update-gub
```

and at no time was there mention of config file conflicts.  Only the grub package configuration/update messages appeared.

Then I restarted in recovery mode 7 times.

Times 1 and 7, the screen went black, the brightness keys had no effect, nor did Alt+F1, nor enter.

Times 2, 3, and 4, the screen was flickered garbage (like static), then went black.  The brightness key worked.  The recovery mode menu appeared.  I dropped to root, ran lsmod, and saw that the radeon and i915 modules were already inserted into the kernel and running.

Times 5 and 6, the screen went black, the brightness button worked, and if I pressed it early enough, I could catch some messages scroll off the screen.  Then I got the radeon module crash stack trace.

I don't know other way of interpeting this than that recovery mode is trying to load the graphics drivers.  I did learn it was loading both modules for each videocard.

Then I tried rebooting into normal mode.  It took 7 times before I had success.  I have notes about the different kinds, but they only really differed in whether the screen backlight eventually came back on or not, and whether REISUB worked to reboot for the next attempt, or if I had to press the power button instead.  I did try [joffe's suggestion]("http://ubuntuforums.org/showpost.php?p=10510056&postcount=12") the first time, but had no luck.  I might have mistyped his suggestions.

Now I'm off to try the suggestions in [the bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620") of booting with a previous versions of the kernel and the ATI drivers (both open-source and official).

---

### Post by afoglia on 2011-03-02
> **joffe said:**
> That's exactly the same crash I get from time to time, just took a picture of it as well. I don't know how to trigger it though. It might be some race condition that can be avoided somehow.

Maybe.  But that photo was taken in recovery mode, where I assumed upstart would run in some single-process mode.  But I just found a bootchart from one of my recovery mode boots that shows multiple processes, with the chart covering nearly 4 minutes.

My guess is it's reading uninitialized memory and that's screwing it up.

Either way, the cause is too far down for me to fix, but that doesn't mean we can't get more information to help the devs.

Anyway... _now_ to test the previous drivers.

---

### Post by cariboo on 2011-03-03
Out of curiosity, is there a way to disable one of the graphics adapters in the bios? If it is loading drivers for both, that is most certainly what your problem is.

---

### Post by afoglia on 2011-03-03
> **cariboo907 said:**
> Out of curiosity, is there a way to disable one of the graphics adapters in the bios? If it is loading drivers for both, that is most certainly what your problem is.

No.  I see nothing about the graphics in the bios.  The only options deal with basic stuff (password, time, boot order) or features like hardware virtualization or function keys.

---

### Post by Harry33 on 2011-03-03
> **afoglia said:**
> No.  I see nothing about the graphics in the bios.  The only options deal with basic stuff (password, time, boot order) or features like hardware virtualization or function keys.

Just to try out what cariboo907 suggested.
Do two tests:
1) remove the radeon and ati drivers (xserver-xorg-video-ati, xserver-xorg-video-radeon + -mach64 and -r128 ) but not intel,
then reboot into recovery mode.
2) remove the intel driver (xserver-xorg-video-intel) but not ati nor radeon (reinstall those after test 1),
then reboot into recovery mode.

Let us know what happens, do you get any error messages.
Also, after booting into recovery mode, choose "low graphics mode" from the friendly-recovery menu.

---

### Post by afoglia on 2011-03-03
Following the suggestion of one of the commenters to my bug report, I tried booting old kernels, 2.6.38-3-generic and 2.6.38-4-generic.  The summary:

2.6.38-4-generic, normal: 1 success, 3 failures
2.6.38-4-generic, recovery: 4 successes
2.6.38-3-generic, normal: 4 successes
2.6.38-3-generic, recovery: 3 successes, 1 failure

Full details at [the bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620/comments/7").

For anyone else having the problem, I suggest booting in 2.6.38-3 for the time being.

I'm going to take a break for a few minutes and then try Harry33's suggestion.

---

### Post by Harry33 on 2011-03-03
> **afoglia said:**
> Following the suggestion of one of the commenters to my bug report, I tried booting old kernels, 2.6.38-3-generic and 2.6.38-4-generic.  The summary:

2.6.38-4-generic, normal: 1 success, 3 failures
2.6.38-4-generic, recovery: 4 successes
2.6.38-3-generic, normal: 4 successes
2.6.38-3-generic, recovery: 3 successes, 1 failure

Full details at [the bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620/comments/7").

For anyone else having the problem, I suggest booting in 2.6.38-3 for the time being.

I'm going to take a break for a few minutes and then try Harry33's suggestion.

I looked at the bug report.
The truth is you cannot downgrade the xserver-xorg-video-ati or xserver-xorg-video-radeon to the version 6.13.*.
This is because they have been built against the old xserver 1.9 and they do not support xserver 1.10 series.
I would not downgrade the whole xserver now, because that does not resolve anything.
Your graphics card must work with the new xserver 1.10 series.
It is interesting to note that the older kernels work better.
A kernel issue then maybe?

---

### Post by afoglia on 2011-03-03
> **Harry33 said:**
> Just to try out what cariboo907 suggested.
Do two tests:
1) remove the radeon and ati drivers (xserver-xorg-video-ati, xserver-xorg-video-radeon + -mach64 and -r128 ) but not intel,
then reboot into recovery mode.
2) remove the intel driver (xserver-xorg-video-intel) but not ati nor radeon (reinstall those after test 1),
then reboot into recovery mode.

Let us know what happens, do you get any error messages.
Also, after booting into recovery mode, choose "low graphics mode" from the friendly-recovery menu.

Okay, it's not as bad as I feared.  2.6.38-5 recovery failed 4 times. 2.6.38-3 failed the first time I tried it, which made me fear I was screwed.  2.56.35-25 recovery (from maverick) worked the first time.  Tried 2.6.38-3 twice more, with one success and one failure.  Didn't try failsafeX yet.

Original post:
[S]F***!  Everyone else, **DO NOT TRY THIS!**  I removed the four ATI driver packages, and now I can not boot into recovery mode, even in 2.6.38-3.

Unless anyone knows a trick to install packages on a system that can't be booted (maybe boot from a live cd and do a chroot?), I'm going to have to reinstall, and since 2.6.38-3 is not official in natty anymore, I'll stick with maverick.[/S]

---

### Post by lucazade on 2011-03-03
> **afoglia said:**
> Okay, it's not as bad as I feared.  2.6.38-5 recovery failed 4 times. 2.6.38-3 failed the first time I tried it, which made me fear I was screwed.  2.56.35-25 recovery (from maverick) worked the first time.  Tried 2.6.38-3 twice more, with one success and one failure.  Didn't try failsafeX yet.

(I'd strike out the below, but I don't see how and scrolling down there is a pain from my iPad.)

Original post:
[STRIKE]F***!  Everyone else, **DO NOT TRY THIS!**  I removed the four ATI driver packages, and now I can not boot into recovery mode, even in 2.6.38-3.

Unless anyone knows a trick to install packages on a system that can't be booted (maybe boot from a live cd and do a chroot?), I'm going to have to reinstall, and since 2.6.38-3 is not official in natty anymore, I'll stick with maverick.[/STRIKE]

You could get kernel from this repo:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Anyway it seems strange you're not able to run recovery mode w/o ati drivers installed, maybe it is a kernel bug.

Start a Livecd and chroot in your installation (where sdaX is your hd partition) to fix it.
```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

---

### Post by dino99 on 2011-03-03
> **afoglia said:**
> Okay, it's not as bad as I feared.  2.6.38-5 recovery failed 4 times. 2.6.38-3 failed the first time I tried it, which made me fear I was screwed.  2.56.35-25 recovery (from maverick) worked the first time.  Tried 2.6.38-3 twice more, with one success and one failure.  Didn't try failsafeX yet.

(I'd strike out the below, but I don't see how and scrolling down there is a pain from my iPad.)

Original post:
[STRIKE]F***!  Everyone else, **DO NOT TRY THIS!**  I removed the four ATI driver packages, and now I can not boot into recovery mode, even in 2.6.38-3.

Unless anyone knows a trick to install packages on a system that can't be booted (maybe boot from a live cd and do a chroot?), I'm going to have to reinstall, and since 2.6.38-3 is not official in natty anymore, I'll stick with maverick.[/STRIKE]

always stay tuned with vesa fallback in case of troubles, that way you can boot

---

### Post by afoglia on 2011-03-03
> **dino99 said:**
> always stay tuned with vesa fallback in case of troubles, that way you can boot

I had xserver-xorg-video-all installed (up until I did the apt-get remove of the 4 ATI-related driver packages).  Is there another video driver module that's not in all?

---

### Post by afoglia on 2011-03-03
Here's the success/failure counts for the different kernels I tried without the four ATI driver packages installed

2.6.38-5-generic recovery mode: 0/4
2.6.38-3-generic recovery mode: 1/5
2.6.35-25-generic recovery mode: 4/2
2.6.35-25-generic normal mode: 1/0

I imagine I would have been screwed if I had a clean natty install.  I still don't suggest other people with this problem try this, unless they really know what they are doing.

I eventually restored my system by downloading the removed packages on another computer and copying them on a flash drive.  I could get either wireless or wired networking to work in 2.6.35, though I imagine that's an issue with newer networking modules for 2.6.38 that aren't backwards compatible.

Considering that the ATI drivers were never really stable in maverick, and I should head into work, I'll skip the other suggestion of removing the intel drivers.

---

### Post by Harry33 on 2011-03-03
> **afoglia said:**
> Here's the success/failure counts for the different kernels I tried without the four ATI driver packages installed

2.6.38-5-generic recovery mode: 0/4
2.6.38-3-generic recovery mode: 1/5
2.6.35-25-generic recovery mode: 4/2
2.6.35-25-generic normal mode: 1/0

I imagine I would have been screwed if I had a clean natty install.  I still don't suggest other people with this problem try this, unless they really know what they are doing.

I eventually restored my system by downloading the removed packages on another computer and copying them on a flash drive.  I could get either wireless or wired networking to work in 2.6.35, though I imagine that's an issue with newer networking modules for 2.6.38 that aren't backwards compatible.

Considering that the ATI drivers were never really stable in maverick, and I should head into work, I'll skip the other suggestion of removing the intel drivers.

This really seems to be a kernel issue, somehow your system is incompatible.
Well let's hope your bug report solves this issue.

---

### Post by jerrylamos on 2011-03-03
I've got ati radeon xpress 200, runs Unity 3D, and ati radeon mobility 7500 does not run Unity 3D.  Runs Compiz sometimes until Compiz crashes.  This does not affect internet, office, ... so I don't care.  I run full screen applications so I wouldn't see any compiz "shading" anyway.

With 02 March CD Daily build insalled they are both on 38-5 and both boot O.K. with whatever ati driver came with Natty.

Now just after install the ati radeon mobility 7500, Thinkpad T40,  booted to the purple splotch screen and cursor.  I did 
Ctrl-Alt-F1
sudo service gdm stop
sudo service gdm start
after a while the purple splotch screen came up and then the desktop.
Boots O.K. since with Classic desktop no effects set.

Jerry

---

### Post by afoglia on 2011-03-03
> **afoglia said:**
> For anyone else having the problem, I suggest booting in 2.6.38-3 for the time being.

I just remembered/re-experienced one of the problems with 2.6.38-3.  Under it, my laptop won't wake up from sleep.  This isn't an issue in -4 and -5, but anyone else with this problem should be aware.

---

### Post by afoglia on 2011-03-03
> **jerrylamos said:**
> I've got ati radeon xpress 200, runs Unity 3D, and ati radeon mobility 7500 does not run Unity 3D.  Runs Compiz sometimes until Compiz crashes.  This does not affect internet, office, ... so I don't care.  I run full screen applications so I wouldn't see any compiz "shading" anyway.

Is that under maverick or a version of natty from before March 2?

> With 02 March CD Daily build insalled they are both on 38-5 and both boot O.K. with whatever ati driver came with Natty.

Now just after install the ati radeon mobility 7500, Thinkpad T40,  booted to the purple splotch screen and cursor.  I did 
Ctrl-Alt-F1
sudo service gdm stop
sudo service gdm start
after a while the purple splotch screen came up and then the desktop.
Boots O.K. since with Classic desktop no effects set.

When you get the prompt, can you see the prompt, or is the monitor off?  By "purple splotch screen" you mean the default Ubuntu background?  Do you check for any obvious errors in the dmesg output or /var/log/syslog, or in the log files in /var/log/gdm?

If you are getting the normal background, you have a different problem than me.  I can't get that far on most boots.

The gdm restart technique is what, earlier in the thread, joffe said worked for him.  I never was able to get gdm to restart, though I only tried a handful of times.

---


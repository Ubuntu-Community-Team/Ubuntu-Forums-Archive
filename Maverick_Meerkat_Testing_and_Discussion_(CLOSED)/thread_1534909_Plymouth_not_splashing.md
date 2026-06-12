---
title: "Plymouth not splashing"
date: 2010-07-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-07-20
Although I had allsorts of troubles with plymouth on my "big" comp with nvidia graphics, since switching to my laptop with intel graphics it has worked beautifully on Lucid.

However, on Maverick I cannot get a splash screen at all.
When booting up a daily livecd it displays the splash normally but once installed I get some errors about ureadahead and it says something about terminated status 1.
There is also an error about some conflict with the intelvfb module.

If I remove the line "load video" on grub the intel error goes away but the other errors are still there and no splash.

I'm sorry about the vague info about errors but it flashes up quickly and I can't make it out properly and I have been unable to find the errors in any logs.

---

### Post by zekopeko on 2010-07-20
Hahaha! Great post title! :)

---

### Post by x-shaney-x on 2010-07-20
Using the FRAMEBUFFER=y workaround gets the splash starting now but it goes off after about a second and I get a black screen with the stupid Glib warning about unknown PWUID or something.
Don't think that's related to the splash because I sometimes get that on mu Lucid install and splash works fine otherwise.

---

### Post by Catharsis on 2010-07-21
Remove "quiet splash" from the kernel parameters and see where it hangs/if you get any errors.

P.S. which intel chipset do you have (lspci | grep VGA)?

---

### Post by x-shaney-x on 2010-07-21
I get the same errors with splash disabled, as well as errors about ureadahead there are also errors about plymouth terminating (with or without the splash parameter).

Only difference disabling quiet splash is that I don't get the glib pwuid error thing.

According to lspci:```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

---

### Post by Catharsis on 2010-07-21
Sorry, but you're going to have to be a lot more specific about the errors; a log file would be best. "Something about plymouth terminating something" really doesn't tell us anything that would help in diagnosing the issue.

When you say you can't find anything in the log files, does that mean you can get into the Maverick machine somehow and get to these logs? It would be very helpful to upload /var/log/syslog so we can figure out what package to file a bug report to and get valuable debugging info.

See if removing "quiet splash" and adding "text" can let you boot to a command line ('text' basically stops X from loading on boot; this says whether it's a graphics issue). If that works, you should also be able to boot to the desktop with "nomodeset xforcevesa".

If there's no way to get to your Maverick partition, you might have to SSH in from your other computer to get a log file. Alternately, a digital picture of the screen with "quiet splash" removed should add some helpful information if it hangs with error messages still on the screen.

---

### Post by x-shaney-x on 2010-07-21
I know the errors are very vague, I suppose I was hoping it would jog someone's memory who has also experienced the same thing and who may have found more specific log files.

I can boot maverick, as it turns out it doesn't seem the errors were critical after all and in fact if I look at /usr/bin/plymouth-log-viewer in LUCID, it shows one of the error messages: ```
init: ureadahead-other main process (949) terminated with status 4
```

In maverick,  /usr/bin/plymouth-log-viewer just tells me /var/log/boot.log cannot be found.
I managed to get the first part of the errors on maverick earlier as it hung for a short while: 
```
init: ureadahead-other main process (949) terminated with status  4
/dev/sda4: 10436 files, 940524/6550316 clusters
init: plymouth (734) terminated with status 1
```
The main process and status numbers change each time.
I still didn't get a good look at the intel related error.

As I mentioned before, if I use FRAMEBUFFER=y, I still see the first two errors (but not the intel one) and the splash screen does pop-up before being replaced by a black screen with this message: ```
(process:383): GLIB WARNING ** GLib - getpwuid_r(): failed due to  unknown user id (0)
``` as discussed here: [http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

Since the errors aren't stopping lucid booting, the intel error is gone when using the framebuffer workaround and the glib warning is getting nowhere in bug reports I don't think there is a lot of point pursuing the matter.
I'll carry on testing and see if it sorts out.

---

### Post by ranch hand on 2010-07-21
Plymouth.d, the real works of plymouth is responsible for logging all that stuff.  As great as this boot manager is I am shocked, shocked I say, that you can't find the log.

Haven't had a log entry for 10.04 or 10.10 ever.  Errors all over the screen but no log.  No wonder everyone thinks it is fine.

Try fileing a bug with the fanboys working as devs.  Good luck with that.

---

### Post by Catharsis on 2010-07-21
Definitely a Plymouth problem. The ureadahead and GLib warnings are completely harmless. You can just ignore them.

See:
[https://bugs.launchpad.net/ubuntu/+source/plymouth](https://bugs.launchpad.net/ubuntu/+source/plymouth)
If you can't find a duplicate, 'ubuntu-bug plymouth' from your Maverick partition, or make a new one using that webpage if you can't get into Maverick.

---

### Post by x-shaney-x on 2010-07-22
I have finally tracked down the original intel related error message.
After a fresh install from a daily live today I went through all the logs and this time the error showed up in the logs:
```
conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
```

So this is the error that stops the splash appearing in the first place.
While the splash DOES appear for a second or so with the FRAMEBUFFER=y workaround I mentioned before.

I don't believe this intel error is related to the other messages at all so I would try to find a solution to this first.
No such message appears in Lucid so it is definitely something specific to maverick.

---

### Post by x-shaney-x on 2010-07-22
A possible answer related to the plymouth issues: > The problem here is the graphics drivers; on your system they're taking longer to load than it takes to check and mount the filesystem - so there's no reason to start the splash screen, since we can already start X.
On HDD-based systems this is worse because we do the ureadahead phase before loading drivers; thus it can take a long time for a splash to appear.
One "solution" is to use the initramfs and start plymouth as a critical step:
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
But that introduces a significant delay into boot just to get the splash screen up for the rest of it

I found the above info, apparently from an ubuntu dev but I cannot for the life of me find the page I saw it now.

But this has been issue since plymouth was first introduced in lucid so is there any hope plymouth will be properly working for all by the time maverick is released?

Again, I don't think the above is related to the intel framebuffer issue.

---

### Post by Catharsis on 2010-07-23
> **x-shaney-x said:**
> I have finally tracked down the original intel related error message.
After a fresh install from a daily live today I went through all the logs and this time the error showed up in the logs:
```
conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
```

So this is the error that stops the splash appearing in the first place.
While the splash DOES appear for a second or so with the FRAMEBUFFER=y workaround I mentioned before.

I don't believe this intel error is related to the other messages at all so I would try to find a solution to this first.
No such message appears in Lucid so it is definitely something specific to maverick.

Please file a bug report against the -intel driver using
```
ubuntu-bug xserver-xorg-video-intel
```
You must do this in your Maverick partition, ideally on the same boot as the error, but if you must, you can reproduce, reboot with "text" added to the grub line (so X doesn't start) and then file a bug. This will ensure the correct log files will be attached (if you have to reboot, also upload kern.log, since the dmesg log will be replaced once you've rebooted).

As I've said before, nothing is really _that_ helpful for bugfixing without a complete set of log files. For graphics bugs, this includes Xorg.0.log, dmesg, and lspci -vvnn as the bare minimum (all of which are captured by Apport, along with many others, when you file a bug with 'ubuntu-bug').

---

### Post by x-shaney-x on 2010-07-23
[DONE!]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/609044")  Never actually used ubuntu-bug before since the last couple of times it hung indefinitely on the browser page and never got to the form so I tend to report them more manually.
Went through ok this time though.

Hopefully enough info is there to help fix this one

---

### Post by Catharsis on 2010-07-23
Thank you, that's one step forward in hopefully getting it fixed.

It would also be nice if you uploaded kern.log or syslog, since all the logs but Xorg.0.log.old are from your boot with "text", so they're all irrelevant. Kern.log and syslog are persistent, meaning they continue logging multiple boots, so they'll have the log info from your failed boot (just try to upload them as soon after reproducing as possible, so we don't have to wade through the log file trying to find that one boot).

---

### Post by wnelson on 2010-07-23
I used the following to fix my plymouth problems.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by x-shaney-x on 2010-07-24
@ [Catharsis]("http://ubuntuforums.org/member.php?u=920304")

I assumed ALL logs would automatically be added but I will upload those if you think they will help.

Only concern there is it might add some confusion because I have been switching between using FRAMEBUFFER=y and I to make matters more confusing, I have been sometimes booting directly from a custom grub entry (from my lucid install) and other times using a chainloader in that grub to point directly to maverick's grub (which is installed in-partition) so it will have often booted with different flags and such (if that all makes sense).

---

### Post by x-shaney-x on 2010-07-24
@ wnelson

I don't think that would fix my problems.
When I used nvidia, it would never switch resolutions but ever since using an intel card, it IS switching resolution normally, just not displaying the actual splash.
With FRAMEBUFFER=y it IS also displaying splash and at the correct resolution but only for a second before being interrupted by that glib warning.

<EDIT>
Also, although I have used the above workaround, it is easily and quickly reversable from one boot to the next.  I want to avoid doing workarounds really in a maverick install because it is just masking problems and then hard to know if they are being fixed or not and introduces extra things to consider which may affect bug reporting.

---

### Post by jerrylamos on 2010-07-24
Splash slows down booting.  Plymouth is reportedly a lot of overhead and slow.

I boot frequently on test systems so my boot line just says
quiet.

Or on intel video graphics, 
quiet i915.modeset=0

Or on IBM Thinkpad T40 ati Radeon Mobility 7500 
quiet radeon.modeset=0

My impression those boot faster.  I don't need to see the same old splash screen time after time taking up processor time.  Oh, the modeset stuff is because black on black screen is boring.

Oh, my background is my wife in a bathing suit on an Australian beach.

Cheers, Jerry

---

### Post by x-shaney-x on 2010-07-24
After some more poking around, I tried removing the ureadahead package, since it has no dependencies.

I rebooted and I had the intel/vesa conflict appear but no other errors and the splash ran normally!!

So it would appear ureadahead or a conflict between that package and another is causing the problem.

I'll post a bug against ureadahead later and see if I get anywhere (no time now unfortunately).

---

### Post by Catharsis on 2010-07-24
> **jerrylamos said:**
> 
Or on intel video graphics, 
quiet i915.modeset=0

I sure hope you're not doing this in Maverick anymore, since it should cause a kernel panic. UMS hasn't been supported since the xserver-xorg-video-intel driver was updated to 2.11 about a month and a half ago :)

---

### Post by Catharsis on 2010-07-24
> **x-shaney-x said:**
> After some more poking around, I tried removing the ureadahead package, since it has no dependencies.

I rebooted and I had the intel/vesa conflict appear but no other errors and the splash ran normally!!

So it would appear ureadahead or a conflict between that package and another is causing the problem.

I'll post a bug against ureadahead later and see if I get anywhere (no time now unfortunately).

I came to the exact same conclusion. See the comment I just added to your bug report :)

---


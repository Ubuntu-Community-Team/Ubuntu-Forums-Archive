---
title: "no audio on Samsung Chromebook 2"
date: 2015-01-10
forum: Multimedia Software
---

### Post by ChrisC on 2015-01-10
I have installed Ubuntu 14.04 LTS on a Samsung Chromebook 2 (Intel), and I can't get the audio to work.  I've spent hours searching and trying and doing and now come to the hive mind for help.  I will try to remember everything I've already tried, but to cut to the chase, I have attached the output of alsa-info.sh (chopped up into 4 parts due to forum filesize limit) and hope someone here will spot the problem.

The speakers and headphone jack work when booted into Chrome OS, so it's not a hardware problem.

As you'll see from the attached alsa-info.sh, this computer has two kinds of audio hardware installed:
- HDA-Intel
- byt-max98090

I think the Intel hardware drives the HDMI port, and the byt-max98090 drives the speakers and the headphone jack.

The speakers and headphone jack don't produce any sound, using the Settings -> Sound -> Test Sound utility.  I also tried doing "aplay Front_Center.wav" as a test, and it ran OK but there was no sound.

The devices seem to exist and are running properly, per all of the tests that I found in searching.  Volume levels all seem to be turned up.  I dabbled in alsamixer, but was afraid to mess with the settings there, since somewhere along the way, I read the warning "alsamixer will fry your speakers!" -- perhaps that was a warning that applied only to this hardware.

I tried removing and reinstalling alsa-base.

If the solution involves disabling the HDMI port, I'm OK with that.  I really just want the speakers and headphone jack to work.

I have attached the output of alsa-info.sh and hope someone here will spot the problem.  (It's chopped up into 4 parts due to forum filesize limit.)

[ATTACH]259136[/ATTACH]
[ATTACH]259137[/ATTACH]
[ATTACH]259138[/ATTACH]
[ATTACH]259139[/ATTACH]

---

### Post by Yellow Pasque on 2015-01-10
> byt-max98090 drives

It looks like the main kernel support for this device was added in Linux 3.17. Quite simply, you're using a kernel that's relatively outdated compared to your hardware. Try a new kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.2-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.2-vivid/)

Oh, and in the future, just upload your alsa info and give the link (alsa-info script does this for you if you tell it to). Either that, or manually use pastebin. Looking at your info was a bit... painful.

---

### Post by ChrisC on 2015-01-10
Thank you Temüjin!

OK, so looking into kernel versions:
- Ubuntu 14.04 had kernel 3.13 in it, was released April 2014
- Ubuntu 14.04.1 had kernel 3.13 in it, was released July/Aug 2014
- Ubuntu 14.04.2 will have kernel 3.16 in it, expected release Jan-Feb 2015

I was considering waiting for the point release, but I see that even 14.04.2 will only have kernel 3.16 in it, and you said that my hardware gets support in 3.17 .

If I try the upstream kernel method above, I'm concerned about what it would do to this machine, considering that it's a Chromebook and may not have grub handling the bootloading.  I don't see any bootloader when booting, it just goes straight into Ubuntu.  If I want to switch back to ChromeOS, I have to manually run a sudo cgpt command.  So I'm afraid that putting in the upstream kernel may mangle things, where it won't boot at all.  Let me know if my concerns are unfounded.

Another thing ... Ubuntu 14.04.1 supposedly has kernel 3.13 in it.  "lsb-release -a" confirms that I have 14.04.1 installed, but "uname -a" says I have "3.10.18".  Am I misunderstanding the uname results?  I suspect that this has something to do with being a chrubuntu install.  Here's the full uname results:

Linux chrubuntu 3.10.18 #1 SMP Mon Nov 17 23:53:31 PST 2014 x86_64 x86_64 x86_64 GNU/Linux

Thanks for the ALSA info upload tip, duh!  I have now done that, and it is here:

[http://www.alsa-project.org/db/?f=5496b531627fc08e32aaf07f0f9fa506ad7576d2](http://www.alsa-project.org/db/?f=5496b531627fc08e32aaf07f0f9fa506ad7576d2)

If anyone else wants to take a look, I'm open to trying other solutions, other than the upstream kernel ...

Thank you for your help!

---

### Post by ChrisC on 2015-01-23
Hi all ... Giving this a bump in hopes that I can get another pair of eyes to look at my ALSA config.  Per previous posts, byt-max98090 hardware doesn't get support until kernel 3.17.  Can someone point me to evidence of that?  I don't want to wade down the 3.17 path (which may be risky for me, per above) unnecessarily.

Should the upstream kernel method work with a Chromebook install?  See my post above for my concerns about that.  How will I be selecting the desired kernel, without the grub bootloader?

Any way to get this working with a 14.04.1 system, or 14.04.2 which I expect will be out in a couple weeks?

See the post immediately above for the ALSA config, in one file.

Thank you all!

---

### Post by Yellow Pasque on 2015-01-23
> Giving this a bump in hopes that I can get another pair of eyes to look at my ALSA config
At this point, what you need help with is finding a new kernel for your Chromebook. You're spinning your wheels until you get a newer kernel.  

> Can someone point me to evidence of that? 
I'm not making this stuff up ;)
Initial support was added in kernel 3.16: [https://github.com/torvalds/linux/commit/9b351d46893e827940e2e8da04f1791e8ec452ca](https://github.com/torvalds/linux/commit/9b351d46893e827940e2e8da04f1791e8ec452ca)
The input/microphone code was fixed/cleaned up in 3.17: [https://github.com/torvalds/linux/commits/master/sound/soc/intel/byt-max98090.c](https://github.com/torvalds/linux/commits/master/sound/soc/intel/byt-max98090.c)
So you're going to need at least 3.16 kernel, though the mic may not work properly until 3.17

As for intalling a new kernel, the links I gave previously aren't applicable since this is a Chromebook and has an ARM CPU of some kind. (Sorry, I don't know too much about ARM or Chromebooks). If you install a new kernel and it doesn't work/boot properly, you can always boot into the old one using the GRUB menu.

---

### Post by ChrisC on 2015-01-23
Thank you again Temüjin, I really appreciate your help.

This Chromebook actually has an Intel CPU.  I know, if you search for "Samsung Chromebook 2" you get ARM results, but this newer one has an Intel sticker and everything.

So there is hope that 14.04.2 will support the hardware.  I'll wait until it comes out, then hope for the best.  I don't care about the mic, just the speakers and headphone jack.

If it still doesn't work, then I guess I'll risk the upstream kernel.  Again, though, THERE IS NO GRUB MENU, at least not currently.  Maybe it would show up if I installed the second kernel.  I just don't know enough about how bootloading works, especially on a Chromebook.

Question ... Ubuntu 14.04.1 supposedly has kernel 3.13 in it. On this Chromebook, "lsb-release -a" confirms that I have 14.04.1 installed, but "uname -a" says I have "3.10.18". Any idea what the disconnect is? I suspect that this has something to do with being a chrubuntu install.

---

### Post by Yellow Pasque on 2015-01-24
> THERE IS NO GRUB MENU

HOLD DOWN THE RIGHT SHIFT KEY DURING BOOT
[https://help.ubuntu.com/community/Grub2#GRUB_vs_GRUB_2](https://help.ubuntu.com/community/Grub2#GRUB_vs_GRUB_2)

---

### Post by ChrisC on 2015-01-24
Nope, does nothing.  It's not that the menu step is skipped, it's that grub isn't there at all.  There is no evidence of grub in /etc or /boot .  Grub is not doing the bootloading.

Any idea what's up with the kernel versions above?

---

### Post by Yellow Pasque on 2015-01-24
I have no idea why chrubuntu kernel version lags behind or what it uses for booting. I've given you as much advice as I can. Now you're going to have to find someone who's familiar with chrubuntu to answer your remaining questions. Good luck.

---

### Post by ChrisC on 2015-01-26
OK, thanks again!  Assuming nothing else happens before then, I'll report back in this thread after 14.04.2 has been released.

---

### Post by andrew196 on 2015-02-05
Hi Chris, I was wondering if I could pick your brain about what exact script you used to install Ubuntu on your Chromebook? I consider myself computer poweruser, but a Linux noob. I recently bought an extra SSD and installed Ubuntu on my desktop PC and I've fallen in love. I think we have the same Chromebook model, I have the [FONT=Verdana]500C12-K01 (purchased from best buy) -- All of the guides I've found are for the ARM chromebook, and every other guide is either vague and/or requires some education I don't have. I've tried various Chrubuntu scripts, the chrx mod for Acer chromebooks, etc. I think my main issue is that I can't get legacy boot working properly and/or GRUB is missing. Any advice you have for me would be greatly appreciated! [/FONT]

---

### Post by ChrisC on 2015-02-08
Ubuntu 14.04.2 was due late last week.  Then they delayed it by two weeks (this page* said Feb 5th until ... the Feb 6th edit).  ARGH.

andrew196, I used plain old chrubuntu.  The only complication I ran into during install was the "/dev/mmcblk0" tweak to the install script, noted below the procedure on the Chrubuntu page.  Since install, I've noted the following problems:
- audio doesn't work, per this thread
- PgUp/PgDn keys didnt work, had to use .xbindkeys to fix
- Backspace key doesn't work as "Back" in Firefox browser, haven't fixed yet
- sleep / hibernate doesn't work

I can live without sleep/hibernate, but lack of sound is a show stopper for me, for this particular laptop.  

Punting to Feb 19th ...

* [https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

---

### Post by ChrisC on 2015-02-20
Ubuntu 14.04.2 just cameout Thursday night, and I have upgraded the machine to it.  No sound.

However, again, I'm not sure that my install is following the expected kernel versions.

Here's is what I wrote on Jan 10th, early in this thread:

> **ChrisC said:**
> OK, so looking into kernel versions:
- Ubuntu 14.04 had kernel 3.13 in it, was released April 2014
- Ubuntu 14.04.1 had kernel 3.13 in it, was released July/Aug 2014
- Ubuntu 14.04.2 will have kernel 3.16 in it, expected release Jan-Feb 2015

 ... Ubuntu 14.04.1 supposedly has kernel 3.13 in it.  "lsb-release -a" confirms that I have 14.04.1 installed, but "uname -a" says I have "3.10.18".  Am I misunderstanding the uname results?  I suspect that this has something to do with being a chrubuntu install.  Here's the full uname results:

Linux chrubuntu 3.10.18 #1 SMP Mon Nov 17 23:53:31 PST 2014 x86_64 x86_64 x86_64 GNU/Linux

... and here is what it says now:

user@chrubuntu:~$ uname -a
Linux chrubuntu 3.10.18 #1 SMP Mon Nov 17 23:53:31 PST 2014 x86_64 x86_64 x86_64 GNU/Linux

user@chrubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

If I'm reading this right, I'm still running the 3.10.18 kernel, and the 14.04.2 update isn't giving me the newer kernel for whatever reason -- something to do with chrubuntu method?

Unless there are any ideas out there, I guess my next step is to attempt the upstream kernel update, which I had concerns about above.

---

### Post by peterburnett on 2015-03-24
I'm running Unity 12.04 Chrubuntu on a Samsung Chromebook XE303C12; I had no audio or mic until I followed alsamixer adjustments from [https://www.youtube.com/watch?v=bKSeZUzPtog](https://www.youtube.com/watch?v=bKSeZUzPtog) .

---


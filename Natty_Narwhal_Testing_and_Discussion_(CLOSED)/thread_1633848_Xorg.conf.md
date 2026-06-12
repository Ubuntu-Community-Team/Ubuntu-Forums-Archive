---
title: "Xorg.conf?"
date: 2010-11-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-11-29
My netbook has a 945GM chipset, I did an upgrade to Natty today, but was getting a black screen when it got to the login screen. I started in safe mode using:

```
i915.nomodeset
```

then dropped to the prompt and create an xorg.conf file using:

```
Xorg -configure
```

I rebooted, and now have a working desktop again. Has any one else run into this?

---

### Post by autocrosser on 2010-11-29
Interesting--I've finally ditched my xorg.conf (maybe for good) & that's no mean feat with a SLI-dual 9800GT nvidia card set......After all these years its weird to be running without one.....I did have to do nomodeset on the kernel line to get in, but once I installed the blob & rebooted---everything "seems" to be working well......

---

### Post by cariboo on 2010-11-29
Actually it only worked for the first reboot, and now I'm back to a black screen. It's a good thing I've got a backup Maverick install. :)

---

### Post by ronacc on 2010-11-29
seeing this thread I renamed my xorg.conf and rebooted , got to a desktop ok but at 1280x800 instead of 1920x1080 and no nvidia driver inspite of the fact that I had installed nvidia current via hardware drivers .I'll try again after I do a fresh install at A1 .

---

### Post by Anduu on 2010-11-29
I haven't used a xorg.conf in ages...not having any issues at present.

---

### Post by autocrosser on 2010-11-30
> **ronacc said:**
> seeing this thread I renamed my xorg.conf and rebooted , got to a desktop ok but at 1280x800 instead of 1920x1080 and no nvidia driver inspite of the fact that I had installed nvidia current via hardware drivers .I'll try again after I do a fresh install at A1 .

Well--I had the "fun?" of reinstalling both my Unity-Testing install & my Lucid>Maverick>Natty GS-Testing install this last weekend-----Something to do with a Curtain, a cord out of the back of my main unit & movement thereof---Not a good time at all...UPS units are all well & good....but if the cord to the power supply is pulled out of the back of your computer....they don't "really" help. :cry::?: Something to do with sudden power loss--caused all 4 of my OS installs to have one problem or another.

Thank all that see ahead of time that I was messing around with a 4G USB stick & had put the Friday current x86-64-alternate .iso on it Friday nite......:D:D must have has ESP or sumtin'):P

Long story short (or longer?)--marathon re-installs later I have both shiny new installs to maul/rend/b0rk!!!!! 

TIME FOR MORE BREAKAGE!!!!!!!!:p:p

---

### Post by cariboo on 2010-11-30
I removed /etc/X11/xorg.conf this morning, and my netbook booted up normally. This type of problem is one that is going to drive me nuts eventually. :)

**Update:** I just rebooted after doing an update and it booted to the desktop again.

---

### Post by nperry on 2010-11-30
Fresh install yesterday,  using daily-live.

Same kind of issue with my netbook,  booting into a black screen - but there is a log in sound.

But I don't have any sounds activated? 

This was happening without a xorg.conf then when I created a xorg.conf it still happened.

---

### Post by cariboo on 2010-11-30
There was just an update to xserver-xorg-video intel version 2:2.13.901-2ubuntu1, I rebooted to a black screen again. Strangely enough, if I connect a second monitor it boots to the desktop and if I then reboot without the second monitor, boots to the desktop.

---

### Post by disregard_this on 2010-11-30
I've got an asus eee 1000he with an intel mobile 945gme, and I've got the same problem.  Plymouth doesn't show up in the native resolution, and at least half of the times I try to boot up I just get a blank screen.  Everything else seems to be working, as the logon sound plays.  I'm using kubuntu if it matters.

Once I've booted up and the screen is black, if I put the machine to sleep and then resume, then the problem fixes itself.

---

### Post by nperry on 2010-12-01
Xorg-edgers has the same problem as well... Think it might be plymouth causing it.. Might be time to log a bug?

---

### Post by cariboo on 2010-12-01
I created bug# [lpbug][s]683909[/s][/lpbug] [lpbug]683775[/lpbug]. Add your me too's.

---

### Post by disregard_this on 2010-12-01
Based on the fact that the kernel mode setting was also giving me the wrong resolution during the boot, I had a suspicion that this bug was in the kernel itself.

Holding shift to get to the grub2 menu, I have not been able to reproduce this error using the 2.6.37-6-generic kernel: I'm only having problems with the newer 2.6.37-7-generic kernel.

Can anyone else confirm that the problem is only with the newest kernel?

---

### Post by cariboo on 2010-12-01
I've had the problem with the last 3 kernels. It's a weird bug. Connecting an external monitor brings the desktop back. THis isn't a problem if I'm at my shop as I use a kvm, so I always have a spare monitor cable lying around, but at home, I'd have to disconnect my monitor from my main system, which I'm not about to do.

---

### Post by disregard_this on 2010-12-01
After some searching, I found that there is already a bug report for this problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683775)

As you stated, this report suggests that this issue is only with the latest 3 kernels.  It can also be fixed by a suspend/resume cycle, as I noted.

You should probably mark the bug you created as a duplicate of this one.

---

### Post by nperry on 2010-12-02
If you aren't subbed to the bug report, here is the work around.. Worked for me on a warm boot.

As a work-around we can turn this off by adding the line below to /etc/default/grub and running update-grub:

    GRUB_GFXPAYLOAD_LINUX=text

---

### Post by zika on 2010-12-02
> **nperry said:**
> If you aren't subbed to the bug report, here is the work around.. Worked for me on a warm boot.

As a work-around we can turn this off by adding the line below to /etc/default/grub and running update-grub:

    GRUB_GFXPAYLOAD_LINUX=textThank You. That (I think) solved my problem... We'll see...

---

### Post by nperry on 2010-12-03
Further update, again this worked for me.


 If those of you affected by this issue could test the kernels below and report back that would be great:

    [http://people.canonical.com/~apw/blank-debug2-natty/](http://people.canonical.com/~apw/blank-debug2-natty/)

---

### Post by cariboo on 2010-12-03
Of course my netbook started properly the first two times I rebooted this morning, but I've installed the updated kernel and I will see what happens. :)

---

### Post by zika on 2010-12-03
> **nperry said:**
> Further update, again this worked for me.


 If those of you affected by this issue could test the kernels below and report back that would be great:

    [http://people.canonical.com/~apw/blank-debug2-natty/](http://people.canonical.com/~apw/blank-debug2-natty/)Wi'll be back (or not) in a jiffy...

No. It doesn't work... It works with GRUB_GFXPAYLOAD_LINUX=text, but, without it (i.e. with keep (default)) it is, I think, even, worse...

---

### Post by nperry on 2010-12-03
> **zika said:**
> Wi'll be back (or not) in a jiffy...

No. It doesn't work... It works with GRUB_GFXPAYLOAD_LINUX=text, but, without it (i.e. with keep (default)) it is, I think, even, worse...

Kind of forgot to try disabling it..

---

### Post by zika on 2010-12-04
Judging from changelog, we are not in for a solution in this version of kernel...?

---

### Post by nperry on 2010-12-05
Says that its fixed....

---


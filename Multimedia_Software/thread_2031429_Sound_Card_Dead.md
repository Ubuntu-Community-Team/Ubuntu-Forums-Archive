---
title: "Sound Card Dead?"
date: 2012-07-22
forum: Multimedia Software
---

### Post by DaimyoKirby on 2012-07-22
So my sound was working, and then it stopped one day.  And I fear the cause is overheating.  However, I want to make sure, so I went onto Launchpad Answers, and the user I was talking with seems to think it was because I'm missing the drivers:
[https://answers.launchpad.net/ubuntu/+question/202875]("https://answers.launchpad.net/ubuntu/+question/202875")

I decided to then try these debug instructions:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
But I got stuck on Step 10 - the only group I'm not a member of is pulse-rt. I couldn't even find a group called pulse-rt.  Also, root isn't listed under any of those groups, and I don't know how to add it.

I'm currently running Xubuntu 12.04 LTS on a HP Pavilion dv6000.
This is the latest alsa-debug-thing:
[http://www.alsa-project.org/db/?f=54d78c9e91c8dfb8e7cf06e75be7e95a8717d958]("http://www.alsa-project.org/db/?f=54d78c9e91c8dfb8e7cf06e75be7e95a8717d958")

So I'm just looking for help here. If you need more info, I'd be happy to post it.

EDIT: When I turned on my laptop my sound was working, but then it stopped working shortly thereafter. I also redid the alsa-info.sh after, since I didn't think to do it when my sound was working, but thought an updated info would be good.

---

### Post by BicyclerBoy on 2012-07-22
Your log show no alsa kernel module/driver is loading. This probably because the h/w is not identified/unclaimed.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1013183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1013183)

Seems that kernel 3.3 could be a solution..
Can you add the kernel ppa ?

If you like taking a risk then xorg-edgers ppa has kernel 3.5..

---

### Post by DaimyoKirby on 2012-07-26
What is the kernel ppa? I know how to add it in the software sources, I just don't know what it is.

I'm trying the xorg-edgers ppa right now, so I post when I see how that goes.
Update: I install all the xorg-edgers updates that popped up in update manager after I added the ppa, but it hasn't seemed to changed anything, and my sound still isn't working.

---

### Post by BicyclerBoy on 2012-07-27
There are multiple release versions of the kernel for different distros.etc..

The kernel ppa has dev/pre-release/proposed versions of kernel packages.

The audio bug fix (in the previous post) was fixed in 3.2.0-27.43..
This version has just come thru' as "pre-release" or "proposed" update for 12.04..

This does not means it is in 3.4 or 3.5 necessarily.

I think xorg-edgers is providing the kernel because it is required for the latest SNA/IvyBridge intel graphics.

So sorry..the bug fix would have appeared in your machine with normal updates..

If you know how to use "synaptic package manager" you can install 3.2.0-27.43   & then uninstall the xorg-edgers kernel..

I run xorg-edgers **without** their kernel because it kills the netbook wifi/LAN.

---

### Post by DaimyoKirby on 2012-07-27
Yeah, nothing seemed to change when I first added the xorg-edgers, and since then I've tried upgrading to 3.4. But now I want to go back just to make sure I didn't just miss that it was working, and so that I'm using a fully supported version.  But when I select 3.2.0-27 in grub, it loads like it's in safe mode - with just a terminal instead of the GUI and everything.

So do you have any idea how I could fix this?  It's not a big deal, since I may be reinstalling everything and switching to a different distro, but it'd be nice to fix, since it could be a few weeks until I do that.

---

### Post by BicyclerBoy on 2012-08-03
There's a note on the xorg-edgers ppa about removing their packages..

The terminal safe-mode is probably caused because you have SNA/ivybridge graphics & the kernel support for the xorg-edgers userspace driver is missing from 3.2.

---

### Post by DaimyoKirby on 2012-08-13
Well, my sound started working again randomly, so I did an alsa-debug quick, and this was its output:
[http://www.alsa-project.org/db/?f=2072e144b815a7da54f8f7726c02d1d736d75b2b]("http://www.alsa-project.org/db/?f=2072e144b815a7da54f8f7726c02d1d736d75b2b")

So honestly, I have no idea what's going on, and I just think my computer's stupid. Or maybe I am ;-)

Thanks for you help!

---

### Post by DaimyoKirby on 2012-08-16
So it stopped working again, and I even got a new card and tried to put that in.
It didn't help.
However, the cord it came with didn't fit my laptop, and the old one didn't look to be in the greatest condition, so I may try and find a cord that fits, unless another solution becomes present(or if anyone else has any ideas).

---


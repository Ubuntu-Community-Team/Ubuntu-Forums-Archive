---
title: "Linux disables internet on all operating systems"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by burnandshiver on 2011-02-08
I've been having this problem for a while, and no amount of google searches have helped.  Any time I try to install any Linux distro (usually this is Ubuntu, but I've been experimenting with Debian and Slackware) I lose internet access not only on the installed Linux distro, but on my existing Windows install as well.  Normally I install my Linux distros to a secondary internal hard drive (which I've never had problems with.  I used to use it for data storage, not operating systems.)  I was beginning to think that maybe it was a problem with this hard drive, so I removed it.  I checked in Windows and the internet was working again.  I then loaded an Ubuntu 10.10 live CD, went through the wizard up until it asked me to partition the hard drive.  I got nervous about resizing my existing Windows partition, and cancelled the install before anything was modified.  When I restarted, event hough I hadn't installed anything, the internet in Windows wouldn't work.  It was as if the cable was unplugged.  It took a couple restarts before it worked again.

I'm at a loss, seeing as it happens with different distros, it affects the Windows install even though most times it wasn't even installed on the same hard drive, and it even happened when I aborted an install from a live CD.  Anybody have any ideas on what this could be?

Thanks in advance. :)

---

### Post by robert shearer on 2011-02-08
It is unusual but not unheard of.
There are several discussions on Linux forums, this one has some interesting comments on router firmware and dhcp performance.
(as well as a lot of flac for the O/P, just ignore those bits and glean from the others. at least you know you're not alone.)

[http://forum.mepiscommunity.org/viewtopic.php?f=19&t=25429](http://forum.mepiscommunity.org/viewtopic.php?f=19&t=25429)

cheers,
Bob.

oh, and it's your router not linux, that's the good news. The bad news is you probably need a different router.

---

### Post by burnandshiver on 2011-02-08
Hm, this sounds like exactly what's happening.  I'm connected directly to the modem Comcast gave me, so I'll have to look into replacing that.  Thanks for the info, this should give me what I need to do more research and maybe find a solution besides replacing the modem.

---

### Post by cascade9 on 2011-02-08
> **robert shearer said:**
> It is unusual but not unheard of.
There are several discussions on Linux forums, this one has some interesting comments on router firmware and dhcp performance.
(as well as a lot of flac for the O/P, just ignore those bits and glean from the others. at least you know you're not alone.)

[http://forum.mepiscommunity.org/viewtopic.php?f=19&t=25429](http://forum.mepiscommunity.org/viewtopic.php?f=19&t=25429)

cheers,
Bob.

oh, and it's your router not linux, that's the good news. The bad news is you probably need a different router.

I'd suspect that its more likely the problem that carlops and JimC bring up on page #1, not a router issue.

---

### Post by Mark Phelps on 2011-02-08
Sorry to be discouraging, but I've run into this same problem on a new system I just built.  It's using a Gigabyte GPA-890 motherboard which hosts a Realtek 81xxx LAN chip.

After a month of use in two versions of Win7 and two versions of Ubuntu (with NO problems, I might add), suddenly, the LAN quit working -- in ALL the OS's.

The Gigabyte forum told me to upgrade/reinstall the LAN drivers.

I did this in 32-bit Win7 -- and LAN service returned.

When I booted into 64-bit Win7, LAN service was back, even though I had not done anything.

In Ubuntu, both 10.10 and 10.04, there was still no LAN service.

Out of desperation, to get SOME LAN service, I stuck in a $20 Linksys gigabit LAN card and -- voila -- LAN service is back in all four OS's.

Now that I had a "fix" for LAN service, I did some testing.

I booted back into 32-bit Win7 using the onboard Realtek LAN.  LAN service was still there.

Booted into Ubuntu 10.10.  LAN service was still gone.

Booted BACK into 32-bit Win7 -- LAN service gone now!

So, it looks like losing LAN service in any OS disables it in all the other OS's.

My "fix" (inserting a Linksys gigabit LAN card) is the only workaround I've found that works.

---

### Post by burnandshiver on 2011-02-11
Well, I've tried getting a new LAN card.  Didn't work, but I did notice that if I turn off my computer completely and unplug it for a few seconds instead of restarting, it seems to fix it.  I'm going to roll with it for now, until I can afford to try a new router.  Seeing as I have to shut it down to switch OS's anyway, it's not a bad work-around.

Thanks to both of you, I wouldn't have been able to escape WindowsXP hell without you! :D

---

### Post by robert shearer on 2011-02-11
> **burnandshiver said:**
> Well, I've tried getting a new LAN card.  Didn't work, but I did notice that if I turn off my computer completely and unplug it for a few seconds instead of restarting, it seems to fix it.  I'm going to roll with it for now, until I can afford to try a new router.  Seeing as I have to shut it down to switch OS's anyway, it's not a bad work-around.

Thanks to both of you, I wouldn't have been able to escape WindowsXP hell without you! :D

Ok, don't know if this is any help but the 'unplug and leave alone for a while' is something I have had to do for clearing odd glitches in bios, usually to do with boot order or hard-drive recognition.
This has been a result of install/partitioning actions that have not stuck or power failure whilst installing.

Especially on Compaq machines, where I have thought them 'bricked' only to get vengeful,unplug overnight, clear and reset the bios,  and do a complete wipe of the hard-drive.
Lo and behold they then behave as a pristine and eager Linux initiate, installing and running without fault. :)

I guess what I am saying is if this machine is 'spare' and you care not what it's eventual next life is then you may wish to be somewhat more radical in your treatment of it...:D
Short of percussive maintenance of course...:P

and checking the network settings in bios could be a low risk first step.

cheers, Bob.

---

### Post by burnandshiver on 2011-07-25
Just wanted to say that I found a workaround for this.  When you switch between operating systems, shut down the computer, switch the power off on the back (the switch on the power supply) and hold the front power button down for a few seconds.  Not sure why, but draining all the power seems to fix it.  Flip the switch on the power supply, turn it on, and it should work.

---


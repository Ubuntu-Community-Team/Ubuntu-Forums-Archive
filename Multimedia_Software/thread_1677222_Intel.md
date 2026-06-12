---
title: "Intel"
date: 2011-01-28
forum: Multimedia Software
---

### Post by kuckunniwi on 2011-01-28
Hi,

First of all, I'm quite a newbie, so please be patient with me! 

 I'm running Kubuntu 10.04 amd64 on an HP Mini 110 3050ss. The audio didn't work out-of-the box, but I was able to find a solution ([http://elblogdeparq.blogspot.com/2010/09/sonido-en-hp-mini-110-ubuntu-1004.html]("http://elblogdeparq.blogspot.com/2010/09/sonido-en-hp-mini-110-ubuntu-1004.html") > page in Spanish)

I installed ```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```, and found somewhere that it would be a good idea to block updates for this package to prevent having problems in the future:

```
sudo aptitude hold linux-backports-modules-alsa-lucid-generic
```

I'm starting to think this wasn't a very good idea...but live and learn, right? In the last security update, my kernel header were updated to v. 2.6.32.28. After reboot, I got the following message:

```
KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Output: HDA Intel (STAC92xx Digital)
Output: HDA Intel, STAC92xx Digital (IEC958 (S/PDIF) Digital Audio Output)
```

I tried to unblock alsa backport updates and update:
```

sudo aptitude unhold linux-backports-modules-alsa-lucid-generic
```

```
sudo aptitude update
```

After reboot, problem persisted, so I uninstalled linux-backports-modules-alsa-lucid-generic and went for reinstall, but get the following message:

```
$ sudo apt-get install linux-backports-modules-alsa-lucid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-alsa-lucid-generic: Depends: linux-backports-modules-alsa-2.6.32-28-generic but it is not installable
```

As the info already suggests, installation of "linux-backports-modules-alsa-2.6.32-28-generic" isn't possible:

```
$ sudo apt-get install linux-backports-modules-alsa-2.6.32-28-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-backports-modules-alsa-2.6.32-28-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-backports-modules-alsa-2.6.32-28-generic has no installation candidate

```

I tried uninstalling "linux-backports-modules-alsa-lucid-generic" andj running ```
$ sudo apt-get autoremove
```

then trying installation again, with no success. 

I've even tried falling back from kernel 2.6.32.28-generic to the old 2.6.32.27 version, under which I had no problems with the drivers, but still nothing.

I switched over to Ubuntu (from windows) about a year ago. I've been using a dual boot with Vista and Ubuntu since then, venturing less and less into Windows as I gained confidence in Ubuntu. For the last 6 months I have only used Windows for video edition & DVD authoring, tasks for which there are no GPL alternatives that suit my requirements. As fond as I've grown of Ubuntu & Kubuntu, switching over to Windows (even if it's just temporary) just because I can't resolve a driver issue is out of the question. I shall persist until the problem is solved! (with your help)

Any suggestions/workarounds would be terribly helpful 

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

```

```
$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Thanks, guys!



**[COLOR="Red"]Edit:[/COLOR]** When updating system (I updated kernel headers to current version), I get 1 blocked update:

```
linux-backports-modules-alsa-lucid-generic - 2.6.32.28.31(amd64)

Type: Blocked update
Issued: 01/14/11
New version: linux-backports-modules-alsa-lucid-generic-2.6.32.28.31
Updates: linux-backports-modules-alsa-lucid-generic-2.6.32.27.29 
```

Snooping around the web, I found this: [http://kubuntuforums.net/forums/index.php?topic=3103678]("http://kubuntuforums.net/forums/index.php?topic=3103678")

From what I understood, this means that one of its dependencies is not satisfied yet, and the full update hasn't yet been released...right? Why would they release the kernel images and header packages but not the alsa backport modules? Audio is unuseable until the update can be installed...

---

### Post by AimOn on 2011-01-29
Hi

Since yesterday, I've got the same problem on my Sony Vaio F11 with Kubuntu running on it.
Your last edit seems to point in the right direction.

As to your question why they would release only half. I wonder too.

I hope this issue can be resolved with the 'full' dist package update... Until then we can only wait and see.

Cheers

---

### Post by BicyclerBoy on 2011-01-29
You can get your alsa fix from here (for lucid anyway)
[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu)

That ppa has alsa 1.0.23 & the modules package

I have my lucid kernel at 2.6.37 from
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)

this has alsa 1.0.23 already..

---

### Post by kuckunniwi on 2011-01-30
I have defaulted back to previous kernel, but had already uninstalled alsa modules hoping a reinstall would fix the problem, and now, as you can see, I can't reinstall.

Through software sources, Kubuntu doesn't seem to let mey add the repositories...("OK button" is greyed out). I installed the alsa-base & alsa-utils debs...but alsa-base suggests during installation that I need to have a driver installed, and may build a custom alsa module from source?'I think I'll just wait for the alsa backports...

[COLOR="Red"] **Edit:** [/COLOR]

By the way, I was tired when I posted this string, browser locked up when posting, and ended up accidentally posting two different strings. I suggest continuing on the other string([http://ubuntuforums.org/showthread.php?t=1677903]("http://ubuntuforums.org/showthread.php?t=1677903")) so as to unify the two  posts (the other post's title is more accurate too). Thanks for the help!

---

### Post by BicyclerBoy on 2011-01-30
Remember the alsa backports package gets built into your kernel image..
Un-installing may not have triggered a kernel image update.
AFAIK Installing a kernel version does not guarantee it will be used on reboot.
The default is the latest version image (GRUB) or that picked in GRUB setup.

You need the default kernel image to be replaced & reboot.

The later kernels have alsa 1.0.23 so you will not need to do anything else to get alsa working..

You should have been able to pick the older kernel image (with your alsa) from GRUB boot menu.

Then purge the problem kernel packages.

---

### Post by kuckunniwi on 2011-01-31
I actually did default back to the previous kernel version in Grub menu, and purge didn't seem to solve the problem (possible because I didn't know which packages to purge) :-)

But a solution was proposed in this thread [http://ubuntuforums.org/showthread.php?t=1677903](http://ubuntuforums.org/showthread.php?t=1677903) which worked! 

Thanks!

---

### Post by AimOn on 2011-01-31
This problem was resolved with the last update. Can you confirm this?

---

### Post by kuckunniwi on 2011-02-01
> **AimOn said:**
> This problem was resolved with the last update. Can you confirm this?

Yes, I can confirm.

I was able to install *linux-backports-modules-alsa-2.6.32-28-generic*, and audio is back to normal.

```
sudo apt-get install linux-backports-modules-alsa-2.6.32-28-generic
```

*Note: I had to do this because I'd removed *linux-modules-alsa-lucid-generic*, thinking reinstallation would solve the problem, but until now, was unable to install again. To anyone else having this problem, who hadn't unistalled linux-backports-modules-alsa, the problem should be easily fixed by updating the system.

Many thanks to everyone!

---


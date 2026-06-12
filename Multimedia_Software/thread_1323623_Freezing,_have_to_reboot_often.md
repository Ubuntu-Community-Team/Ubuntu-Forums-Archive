---
title: "Freezing, have to reboot often"
date: 2009-11-11
forum: Multimedia Software
---

### Post by david.karr on 2009-11-11
I recently installed 9.10 on a Dell desktop box with Intel graphics.  If I leave the system alone for a while, when I come back I often find that the mouse pointer moves, but everything else is dead.  I can do nothing but reboot.

I've read some indications that I need to update my Intel video driver.  Does anyone know if that's a likely cause of this?

If that's the likely cause, how exactly do I do that update?  I tried adding "ppa:ubuntu-x-swat/x-updates" to my software sources, as one note indicated, but I'm not sure what else I do after that.

---

### Post by HappyFeet on 2009-11-11
After adding that PPA, do:
```
sudo apt-get upgrade xserver-xorg-video-intel
```
Then reboot.

---

### Post by david.karr on 2009-11-11
Thanks, but that's making no difference.  I'm still seeing it freeze.  In fact, I had forgotten that I had already done that earlier.  When I tried it just now, it said it had 0 things to update.  I've rebooted several times since doing that update.

---

### Post by HappyFeet on 2009-11-11
Are you sure you added the PPA correctly?

Do:
```
cat gedit /etc/apt/sources.list
```
and copy and paste the output here.

---

### Post by david.karr on 2009-11-12
Hmm, I'm pretty sure that "cat gedit /etc/apt/sources.list" doesn't make much sense, but I'll show the output of "cat /etc/apt/sources.list" here.  I don't see it in the output here, so I obviously didn't do it right.  However, I was following the instructions at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") . In the "Other Software" tab, I added "http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu" and enabled that source.

----------------/etc/apt/sources.list------
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Madvil on 2009-11-12
I got the same problem.

Left the system open for some downloads overnight and, when I woke up, I couldn't 'write' in the Downloads folder. Tried restarting... No response. After a hard reset, this happens within 5 minutes of waiting.

I know my disk has bad sectors (at least Ubuntu's utility reported it has) and I'm trying to find a way to mark them, since fixing them is out of the question.

---

### Post by david.karr on 2009-11-12
@Madvil: Your disk problem is obviously unrelated to this screen freezing problem.  Write a new base note and don't reply to unrelated notes.

I've done "sudo apt-get upgrade xserver-xorg-video-intel" and "sudo apt-get install xserver-xorg-video-intel", but it says I already have the newest version.

Someone on the IRC channel told me to look for "/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-karmic.list".  That file is there, and its contents are:

  deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main

Anything else I can try?

---

### Post by david.karr on 2009-11-13
I'm still struggling with this.  I'm pretty sure I've gotten the PPA installed, and I've updated the driver, but my system freezes, requiring a reboot, after about 20 minutes.  I've never sat here and timed it, however.

In "/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-karmic.list" I have "deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main".

I did "sudo apt-get update".

I did "sudo apt-get install --reinstall xserver-xorg-video-intel".  That reinstalled the driver, but it made no difference.

I don't know what else to do.

---

### Post by david.karr on 2009-11-14
I am still struggling with this.  I'm considering getting rid of this intel graphics card and replacing it with an NVIDIA card.  I at least know that an NVIDIA card works on my other old Linux box.

I've believe I've verified that I have the latest Xorg PPA installed, and updated to the latest Xorg driver.

One person in this forum suggested I enable KMS (kernel modesetting).  However, the link he provided for turning this on had a big bold statement saying that this is enabled by default at a certain kernel version, and my kernel version is newer than that, so I would assume it's already enabled.  I'm not sure how I can verify that.

This morning I looked in the "kern.log" for events that occurred just before long gaps.  I saw the following after I rebooted the box this morning (as usual):

----------------
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752046] INFO: task i915/0:227 blocked for more than 120 seconds.
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752054] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752059] i915/0        D c08145c0     0   227      2 0x00000000
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752068]  f6a61f04 00000046 f6a40cbc c08145c0 f6a40f28 c08145c0 7af12304 00000125
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752080]  c08145c0 c08145c0 f6a40f28 c08145c0 7af100e8 00000125 c08145c0 f5f0e000
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752090]  f6a40c90 f6872c14 f6872c18 ffffffff f6a61f30 c056f776 c0748e80 f6872c1c
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752101] Call Trace:
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752119]  [<c056f776>] __mutex_lock_slowpath+0xc6/0x130
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752125]  [<c056f690>] mutex_lock+0x20/0x40
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752171]  [<f822bc0a>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752184]  [<c0157a7e>] run_workqueue+0x6e/0x140
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752207]  [<f822bbe0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752216]  [<c0157bd8>] worker_thread+0x88/0xe0
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752225]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752231]  [<c0157b50>] ? worker_thread+0x0/0xe0
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752237]  [<c015bf8c>] kthread+0x7c/0x90
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752243]  [<c015bf10>] ? kthread+0x0/0x90
Nov 14 00:13:09 davidkarr-desktop kernel: [ 2520.752251]  [<c0104007>] kernel_thread_helper+0x7/0x10
----------------

Looking further back in the log, I saw this event several times in the houre before this.  This event was the last event in the log until I rebooted, several hours later.

Does that provide any useful information to anyone?

Another ironic piece of information:  I may have found a workaround for the problem.  It's not really a practical workaround, but I discovered something that I can do before I leave the computer that in a couple of cases has let it live for several hours.  I had been trying to get advice on this from the #ubuntu IRC channel.  Normally when I leave the computer I don't leave anything actively running, but one day I left the IRC channel running, which continually updates with new messages.  Somehow, when I came back several hours later, it was still alive.  Up to that point, that was the ONLY time it had ever ran for that long without freezing.

---

### Post by david.karr on 2009-11-27
Continuing with the odd workaround I found, I was able to find an even more convenient "solution".  I installed a "Wanda the Fish" in both my top and bottom panels.  This little panelet (did I just make that up?) is just a little fish that swishes around a tiny bit in place.  It runs continuously.  It hasn't frozen once since I did that.

---


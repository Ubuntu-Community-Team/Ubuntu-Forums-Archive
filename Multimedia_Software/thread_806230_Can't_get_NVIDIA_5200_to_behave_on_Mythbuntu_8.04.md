---
title: "Can't get NVIDIA 5200 to behave on Mythbuntu 8.04"
date: 2008-05-24
forum: Multimedia Software
---

### Post by Sixten on 2008-05-24
With the release of Mythbuntu Hardy, I decided to put a new, bigger HD in my PVR machine, and install a fresh OS. There have been a few struggles with this, but by far the most serious and annoying has been trying to get stable video support for my GeForce FX 5200.

I have tried the proprietary drivers installed by the Mythbuntu CD, the ones installed by EnvyNG, and both the 171.06 and 173.08 installers from NVIDIA. All show the same display artifacts. The image will freeze, or show random color "tearing" or pixelation, or things showing in the wrong location. (See the attached photo for an example.)

I'm pretty sure at this point that it's a driver issue: installation, conflicts, settings... something. The hardware was working fine in earlier revs of Ubuntu; doesn't have any issues under Windows, or Ubuntu with the generic video driver (when I revert to failsafe xorg.conf); and I ran memtest on the machine for like 19 hours without any problems.

At this point, I feel like I've tried every tweak I've been able to find trolling through the forums for advice. I'm about ready to just put the machine in a closet, or try to find a Windows-based alternative. This might be the most incredibly frustrating Linux struggle I've had.

Help? :confused:

---

### Post by tgm4883 on 2008-05-24
Try installing Mythbuntu 8.04, then fully updating, then installing the restricted driver.  

Is this an unmodded video card?  Those types of artifacts could be from over heating.

---

### Post by Sixten on 2008-05-24
> **tgm4883 said:**
> Try installing Mythbuntu 8.04, then fully updating, then installing the restricted driver.
Any particular reason (like a package that's been updating since release), or just something to try?

> Is this an unmodded video card?  Those types of artifacts could be from over heating.
Came out of the box and went into the machine ~2 years ago, and I've never seen this kind of problem with it before. No overclocking or anything like that.

I've been running things like Quake 3 timedemos on Windows to try to rule out heat/hardware failures, and haven't seen any of the same issues. At the moment, the machine is on a desk in my office, case totally open, so I'm pretty sure it's not overheating.

---

### Post by tgm4883 on 2008-05-24
It's just something to try.  Also, i'm not sure where the cutoff is, but you could try nvidia-glx instead of nvidia-glx-new

---

### Post by Sixten on 2008-05-25
> **tgm4883 said:**
> Also, i'm not sure where the cutoff is, but you could try nvidia-glx instead of nvidia-glx-new

I have, actually, along with at least one of the legacy drivers that EnvyNG knows how to install. Now, I can't swear that both were clean change-only-one-variable experiments, 'cause I was so frustrated/desperate by that point, but they didn't work any better.

---

### Post by tgm4883 on 2008-05-25
Did the live cd show this same problem?  Have you tried a regular Ubuntu Hardy install?

---

### Post by Sixten on 2008-05-25
> **tgm4883 said:**
> Did the live cd show this same problem?
I wasn't sure whether the live CDs were able to load the restricted drivers; I guess I always assumed that they were pretty bare-bones in that respect.

> Have you tried a regular Ubuntu Hardy install?
Nope.

If the live CD can load the proprietary drivers, though, I might try the mainstream distro that way. This machine was running MythTV on regular Ubuntu before, and doing so again would work. Mythbuntu is just *much* more convenient for what I'm actually trying to accomplish.

---

### Post by tgm4883 on 2008-05-25
Not sure what you are trying to accomplish, but you can install the package mythbuntu-desktop to get the mythbuntu look and feel.  You can also install mythbuntu-control-centre and configure and install it so it will auto boot into mythbuntu and have the necessary software that you require.

---

### Post by Sixten on 2008-05-28
> **tgm4883 said:**
> Did the live cd show this same problem?  Have you tried a regular Ubuntu Hardy install?
Well, you can add both of these to the fail list. The live CDs (both Mythbuntu and mainstream Hardy) appear to use generic graphics, with no option (that I could find) to load the proprietary drivers.

And, after installing Hardy, updating fully, and then switching to nvidia-glx-new (via the restricted driver manager)... same kind of artifacts I was seeing in Mythbuntu. Purged that, installed EnvyNG, tried that way, and the issues are just as bad or worse.

Having now exhausted the main "try this other install" options, can anyone offer any suggestions as to what might be causing these artifacts, or how I might correct them?

---

### Post by briandu on 2008-05-28
Follow this exactly and your screen probs should be resolved.

[http://ubuntuforums.org/showthread.php?p=5064980#post5064980](http://ubuntuforums.org/showthread.php?p=5064980#post5064980) msg #430

I have just sorted my upgrade probs right now - first time.

---

### Post by Sixten on 2008-05-28
> **briandu said:**
> Follow this exactly and your screen probs should be resolved.
I have tried NVIDIA's own installers, without success. But they [just released a new version]("http://www.nvnews.net/vbulletin/showthread.php?t=113919") today (173.14.05), so what the heck. (I'm also not sure that I've tried it on a clean system, which I will do this time.)

For the record, I was desperate enough that I actually downloaded and installed MythDora... same kind of problems with the display (not sure what version of the proprietary drivers that installs).

---

### Post by briandu on 2008-05-28
seems strange, I have just upgrade right now and follow as per note and no probs whatsoever. I cannot imagine that Mythbuntu can/will vary from the standard. NB it is up to nvidia not Ubuntu - that is why I find it strange.

I'm gonna dig into this.

---

### Post by Sixten on 2008-05-28
> **briandu said:**
> NB it is up to nvidia not Ubuntu - that is why I find it strange.
Yeah, at this point, it seems pretty clear to me that either a) the hardware is bad (in some weird way that doesn't show up in generic graphics mode or under Windows), or b) something weird is up with NVIDIA's drivers. I don't know whether they're broken, they don't like this particular card, or something very hinky is going on in the setup. But I'm not enough of an expert to really know what the useful information I could provide might be to narrow that down.

I'll reinstall Mythbuntu, try the new installer on the clean system, and see how it goes.

There's some [useful advice]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") on their NVnews.net forum that has [some details]("http://www.nvnews.net/vbulletin/showthread.php?t=58498") I don't think I've tried before.

---

### Post by briandu on 2008-05-28
What I did now is to go through routine as describe in the link again. And no prob at all - so it is strange.

Wish you luck on this one.

Cheers.

---

### Post by Sixten on 2008-05-30
> **briandu said:**
> What I did now is to go through routine as describe in the link again. And no prob at all - so it is strange.
Still no joy for me. In fact, kernel panics after some period of weirdness. :-(

But let me ask this: are you downloading the kernel module from NVIDIA (like it offers to do), or building it locally (which it will do if you say no to that)? The instructions in that post aren't explicit on that point.

---


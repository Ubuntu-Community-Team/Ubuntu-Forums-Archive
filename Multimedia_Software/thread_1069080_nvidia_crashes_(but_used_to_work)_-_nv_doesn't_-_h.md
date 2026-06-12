---
title: "nvidia crashes (but used to work) - nv doesn't - harware or software problem?"
date: 2009-02-13
forum: Multimedia Software
---

### Post by Redsandro on 2009-02-13
My computer crashes when X loads using nvidia proprietary driver. Suddenly. It used to work. If I change *nvidia* to *nv* in *xorg.conf*, all works fine. Except games ofcourse.

I am trying to find a solution for days now, of no avail. I am wondering if this is caused by a software issue or if my video card is all of a sudden broken in a way that crashes the system only when the proprietary driver is used.

This is about a nVidia geForce FX5200 @ Intel P4 2.4 GHz/Asus P4C800 with 2GB memory.

Is there a way other than format/reinstall to see if software or configuration is the cause of this?

---

### Post by xzero1 on 2009-02-13
Since the card works with the nv driver it doesn't seem hardware related. A few things you could try:  Check the xorg and system logs in /var/log for any useful info. Boot up with a live cd. Install the proprietary driver (don't reboot when told) but hit ctrl-alt-backspace and you should be able to log in using the nvidia driver. This will at least test the driver. Note that this is flaky and may not work on all systems. I would also consider posting in the hardware section instead of this one.

---

### Post by Redsandro on 2009-02-13
That's an excellent idea with the liveCD. I am curious as wether the same crash would occur.

But the LiveCd does not have a video card detected in the Hardware Drivers system application. I installed Nvidia-glx-new through synaptic but ctrl-alt-backspace doesn't start it. nvidia-xconfigure also doesn't work because the liveCD has a weird xorg.conf.

It it possible at all? I have the 8.04 live CD (also running 8.04 so it seems to make sense. :P)

---

### Post by xzero1 on 2009-02-13
If you have a hardy or feisty live-cd you might have better luck.  The restricted drivers detection has changed with the newer distributions. You might also want to try Envy to re-install your nvidia drivers, though I don't see any support for intrepid. See
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Redsandro on 2009-02-13
I thought 8.04 was Hardy? That's the one I just tried.
I remember having trouble with Envy, but I am not sure if it was this computer (I set it up some time ago and it just worked through upgrades).

I also have 7.04 (feisty) and 6.10 (edgy). They are *somewhere*, I will look them up and try the same!

---

### Post by Shazaam on 2009-02-13
Did you recently install an update for the kernel? This will usually bork non-Ubuntu supplied video drivers (drivers from the nvidia website) unless you have dkms installed. Installing the matching kernel headers and then reinstalling the drivers might fix it.
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Redsandro on 2009-02-13
Nope, I hardly ever update because even though updates are good, I've only had trouble with updates (admittedly with older machines though, but I've never had problems for not updating). I update once every few months and I THINK the crash came about a month after my last updates.

The problem is that usually the computer boots and does it's thing (downloading for mediacenter, fileserving and webserving)and I turn it off without actually switching to it (KVM with my workstation) so I don't know exactly when it began. But I do know I used to play Unreal on it when I had to wait for renders on my workstation.

When I did do updates, sometimes the stuff you mentioned got updated too but it was never a problem. I think I came from 7.04 by just updating and the video was never broke. I tried loading the different kernels from GRUB (they all remain in the list) and they all have the same problem.

When there is an issue with headers or some issue that makes the video fail, usually it just fails to load X. But now it does load, but shows some black lines and quicks, then crashes. Very occasionally it shows kernel panic on my keyboard, but usually it just freezes. Also very occasionally I can still SSH into the machine, but it will be very slow.

I found the 7.10 live CD back and will try tomorrow if I can live-try the proprietary driver.

Offtopic but curiosity: How bad is it to install for example 8.04 and never update? This is about a home machine, not a university network thing.

---

### Post by Redsandro on 2009-02-13
I should sleep but I couldn't help the curiousity. I tried 7.10 and indeed, it does offer me the ability to install the restricted driver from a live session, as opposed to the 8.04 cd.

However, I can't get it to use after restarting x. It keeps saying "not in use" even though it is checkmarked.

I mounted my / partition and copied my usual xorg.conf over, but then x failed to start and went to failsafe.

Should I try envy or will it result in the same?
(never tried it on live session)

---

### Post by Redsandro on 2009-02-25
I installed Ubuntu 8.10 and once I installed the hardwaredriver and rebooted, the screen would go black on GUI and I wasn't able to switch to TTY either, which to me means a crash.

I didn't know it was possible, but apparently my hardware has become worn out in a way that only messes things up when the restricted driver is active.

I am confused, but there is my conclusion.

Note that my MSX is still working. It seems like the newer a computer gets, the sooner it wears out. That's probably why a cheap phone is faster then the computers inside important satellites.

---

### Post by senatus on 2010-03-24
Old thread but same symptoms.  **Any** (i.e. I tried 177 through to 195 or whatever the latest is) proprietary nvidia driver will hang my machine as soon as it gets to X.  Cannot ssh, nor Ctrl-Alt-Bkspace, nor even numlock.  Or even reset button - only poweroff will work.  Only nv works, and it works flawlessly.  This only happened recently - but sticks around either when I translated up from Intrepid to Jaunty, then back down to a fresh Intrepid (i.e. I have tried just about everything).  So I hypothesize that either a part on my 6200 fried that only gets exercised under the accelerated driver, or, I failed to placate the angry god inside the machine.

---

### Post by Redsandro on 2010-03-24
> **senatus said:**
> Old thread but same symptoms.  **Any** (i.e. I tried 177 through to 195 or whatever the latest is) proprietary nvidia driver will hang my machine as soon as it gets to X.  Cannot ssh, nor Ctrl-Alt-Bkspace, nor even numlock.  Or even reset button - only poweroff will work.  Only nv works, and it works flawlessly.  This only happened recently - but sticks around either when I translated up from Intrepid to Jaunty, then back down to a fresh Intrepid (i.e. I have tried just about everything).  So I hypothesize that either a part on my 6200 fried that only gets exercised under the accelerated driver, or, I failed to placate the angry god inside the machine.

Nice to know I am not the only one in the world. I thought I was crazy. But I couldn't figure it out.

So like you I hypothesized that the special secret nVidia-proprietary undisclosed part of the chip burned out, and only the open (or figured) part still works.

I had to let the card go.

---

### Post by senatus on 2010-03-26
> **Redsandro said:**
> Nice to know I am not the only one in the world. I thought I was crazy. But I couldn't figure it out.

So like you I hypothesized that the special secret nVidia-proprietary undisclosed part of the chip burned out, and only the open (or figured) part still works.

I had to let the card go.

Misery loves company.

My half-serious theory is that something has gone wrong on the silicon that handles 3D.  Since the nv driver never executes in that space, it never triggers the freeze.

**Update** I confirmed it's the card - never trusting a vendor to *really* support anything but Windows, I transferred the card to an XP box - it worked fine until I installed the nVidia drivers and - bang.  Locks up.  So at least I feel better - this wasn't something stupid I'd somehow done to my Ubuntu configuration.

What card did you eventually go to?  In my case, this is for an AGP system, and there's not a lot of options out there for an accelerated 3D card with AGP and DVI together.

---


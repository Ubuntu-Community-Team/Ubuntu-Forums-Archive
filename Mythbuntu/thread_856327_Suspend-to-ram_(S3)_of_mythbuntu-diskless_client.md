---
title: "Suspend-to-ram (S3) of mythbuntu-diskless client"
date: 2008-07-11
forum: Mythbuntu
---

### Post by rune.evjen on 2008-07-11
I have been trying to get my diskless client to suspend (S3 mode), but the client stops in the suspend process with a blinking cursor. 

I am using an Acer L250 media center computer

I also tested the uswsusp method but it seems that the suspend to ram method (s2both) depends on a swap partition which is not available on the client.

My plan was to get the client to suspend and to wake up on lirc events, in order to save power.

Has anybody gotten suspend to work with diskless, or is my problem hardware configuration related ?

All help much appreciated !

---

### Post by laga on 2008-07-12
This is an interesting issue. I guess it breaks once the network connection is shut down. There's probably not much hope, but I'll take to ogra, the LTSP guy.

---

### Post by rlowery on 2009-03-06
Was there any outcome from this discussion.  Were you able to get suspend to ram working?

---

### Post by nuneza on 2009-03-31
Anyone figure this out?

---

### Post by Antharian on 2009-05-17
I wanted to bump this thread.  I've been playing with the same thing, with little to no success.

Regards

---

### Post by nuneza on 2009-07-09
anybody?

---

### Post by bcgrown on 2010-01-01
It's probably a hardware compatibility issue.  On my previous system (Intel P4 with Intel D865 chipset) pm-suspend worked, but didn't resume properly.

On my current system (Pentium Dual Core w/ Intel G41 chipset) pm-suspend works perfectly and I am able to wake on USB activity or by Wake on Lan magic packet.

---

### Post by ruddypict on 2010-02-09
> **bcgrown said:**
> It's probably a hardware compatibility issue.  On my previous system (Intel P4 with Intel D865 chipset) pm-suspend worked, but didn't resume properly.

On my current system (Pentium Dual Core w/ Intel G41 chipset) pm-suspend works perfectly and I am able to wake on USB activity or by Wake on Lan magic packet.

 So you have one system that is a) diskless and b) suspending fine?  Just wondering as it wasn't clear -- and I haven't heard of someone successful with both yet.  I have a system here that was able to suspend until I went diskless.

---

### Post by bcgrown on 2010-02-09
> So you have one system that is a) diskless and b) suspending fine? Just wondering as it wasn't clear -- and I haven't heard of someone successful with both yet. I have a system here that was able to suspend until I went diskless.

No, neither system is diskless.  I don't have the P4 system anymore, and the C2D system suspends okay but I wasn't able to make suspend play well with MythTV.  I've settled on auto power-on and off, combined with a scheduled wake-up.  Sorry I can't help you with this one.

---

### Post by ruddypict on 2010-02-19
Well, I've been monkeying around with my diskless frontend some more.

The good news is, I got suspend to work!  The bad news... resume doesn't seem to be working well.  When I resume, X comes up, but mythfrontend never restarts.

Here's a bit from my pm-suspend log on the frontend:
```
Thu Feb 18 23:34:52 EST 2010: Awake.
Thu Feb 18 23:34:52 EST 2010: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume suspend: /usr/lib/pm-utils/sleep.d/99video: 219: deallocvt: Input/output error
Returned exit code 127.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00myth resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: xprop:  unable to open display ''
success.
/usr/bin/mythfrontend: 16: /usr/bin/zenity: Input/output error
/usr/bin/mythfrontend: 16: whoami: Input/output error
/usr/bin/mythfrontend: 16: whoami: Input/output error
/usr/bin/mythfrontend: 16: gksu: Input/output error
/usr/bin/mythfrontend: 16: /usr/bin/zenity: Input/output error
```

---

### Post by rileyp on 2010-03-04
So you got suspend to work on diskless front end thats awesome! Well done
Did you have mythfrontend running when you suspend?.... perhaps if you closed it prior to suspending it might work on resume? 
maybe you could add a script somewhere..  rc.local perhaps? To check if mythfrontend is running and if isnt to open it... Or will this just cause havoc when you really want to close mythfrontend? Does rc.local only execute commands once on start up? and is x running when rc.local is executed? things to ponder....
I honestly thought resume from suspend to ram on a diskless system was pie in the sky sorta stuff.
Obivously not.....:D
cheers rileyp

---

### Post by ruddypict on 2010-04-29
Rileyp: I have a script called 00myth in /usr/lib/pm-utils/sleep.d/ it handles all the fun stuff (shutdown of mythfrontend, lirc and other stuff on suspend, and startup on resume).  Everything works perfectly when used on a frontend with a hard drive.  Its only when it goes diskless that I get the errors I posted previously.

I am more than likely going to give it another shot when I upgrade to the latest Mythbuntu.  But its probably going to be my last shot.  It seems that diskless + suspend = broken and there seems to be no strong move to fix it.  I love investing my time in projects but don't really like investing in a time-waster :D.

---

### Post by rileyp on 2010-04-30
ruddypict are you going to post up your script for me wrapped in code tags so I can use it as well or you just teasing me?
My diskless front end actaully did suspend to ram a few times  (asrock ion) but I have given up on it for a while as I need to relocate my diskless files to another partition other than / as sometimes the logs fill the drive and then mysql in mythtv gets sad as it cannot write to disk... then I get sad....
I read in a lucid thread somewhere that a new version of ltsp was being released with lucid which is meant to be better as well.
I did give lucid diskless a go but I had trouble... that was probably 2 months ago so it might be worth another try.
cheers rileyp

---


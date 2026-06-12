---
title: "Ubuntu's Sound Worked Great ... Until Today"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by BlueSun on 2006-10-09
I've had Dapper on my old Dell box for several months with no sound problems.  I could even listen to multiple audio sources simultaneously, like XMMS, Totem, and a Firefox Flash movie.  Today, ZILCH.

I read through the [Comprehensive Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") and thought, "You've got to be kidding."

The soundcard is on the Intel motherboard:

```

$ aplay -l

\**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$ lspci -v

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
        Subsystem: Intel Corporation: Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at e800 [size=256]
        I/O ports at ef00 [size=64]

```

I'm currently running kernel version 2.6.15-27-386.  I can't pinpoint the exact moment I lost sound; I may not have had it all morning.  Today I ran the automatic Add/Remove utility to get updates, but I didn't look to see if there was a kernel update or something else that may have affected my audio driver.  I installed Lyx using Synaptic just prior to noticing the problem.  I can't imagine either of these additions could have killed my sound, but then again, I'm still a noob.

Is there a local configuration change I need to make, or do I need to go through the process of installing and configuring a new driver?  I'm still a little lost because, as I said, Dapper took care of all of this automatically the first time.

Thanks

---

### Post by gandalf2041 on 2006-10-09
I had the same thing happen after following one of the mini how-tos on the Ubuntu Guide.  I ended up having to reinstall libesd-alsa0. 

You could also try cranking up all the volumes under alsamixer. Not sure how it would've gotten changed since you had sound before but, it's worth a look.

---

### Post by magicrobotmonkey on 2006-10-10
Ever since the -23 kernel, i lose sound every few boots and right now the only fix I've found is to reboot and pray. Not sure whats up with it.

---

### Post by deadgobby on 2006-10-10
You are not the only one with the problem. Load of people are and I am going to to above sudjestion and see if that works. Cause I lost every thing yesterday and not too peppy happy about it....Grrrr
Gobby

---

### Post by deadgobby on 2006-10-10
Well to let you know this. I reinstalled libesd-alsa0.
and no go. So I uninstalled it and that was a big F NO NO. I had to reinstall  Gnome from safe mode, at least I got the terminal. At least that little lesson is not to do that. At least I got Gnome back up and running. yet no sound yet. ](*,)

---

### Post by gandalf2041 on 2006-10-11
Sorry the reinstall didn't work.  X gets pretty cranky (as you discovered ;) ) if you UNinstall libesd-alsa0. I'm glad to hear you were able to get back up in relatively short order.  Did you try cranking up all the channels in alsamixer...it's a long shot but...

magicrobotmonkey said:
> Ever since the -23 kernel, i lose sound every few boots and right now the only fix I've found is to reboot and pray. Not sure whats up with it.

I have a similar mysterious problem with gdm...my machine freezes at a blank screen right before loading gdm.  Usually works OK with 1 or 2 reboots...VERY annoying :evil:

---

### Post by BlueSun on 2007-03-01
Running **alsamixer** from the Terminal was the answer for me.  The **PCM** value -- for whatever reason -- will sometimes mute itself (I have no idea why), and whenever I have no sound that's the first place I check.  There's a nice rundown of the features at [[COLOR="Blue"]http://en.wikipedia.org/wiki/Alsamixer[/COLOR]]("http://en.wikipedia.org/wiki/Alsamixer").

To run:
```
~$ alsamixer
```

---


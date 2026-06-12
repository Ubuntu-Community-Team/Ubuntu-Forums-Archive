---
title: "PulseAudio has high &quot;peaks&quot; of CPU usage that cause problems"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Malcolm on 2008-11-01
Hello, I was posting about my issues in a thread about Rhythmbox skipping. Whenever I'm listening to music, watching flash videos and similar the sound pauses every now and then. It's not predictable, and sometimes it becomes increasingly frequent until it makes the program I'm using (for example, Rhythmbox) freeze.

After observing the output from "top" for a while I noticed that when these "pauses" happen, the pulseaudio process is suddenly using 100% CPU, which is a 2GHz AMD Sempron - undoubtedly not the most recent, but this still doesn't justify it.

Is there a way to solve this, other than removing/disabling PulseAudio as suggested in other threads? Is it normal for PulseAudio to have such an irregular CPU usage with those annoying peaks?

Thanks

---

### Post by Malcolm on 2008-11-01
Here are two links that seem to describe the same problem...

[https://bugzilla.novell.com/show_bug.cgi?id=437835](https://bugzilla.novell.com/show_bug.cgi?id=437835)

[https://bugs.launchpad.net/paconfig/+bug/190754](https://bugs.launchpad.net/paconfig/+bug/190754)

The first one in particular describes exactly what I'm experiencing. But of course it doesn't help. The Launchpad link is more helpful, although the workaround proposed at the end of the discussion didn't help in my case.

EDIT: I've killed the pulseaudio process, have been listening to music for a while now and it's perfect. Those "peaks" would slow down other programs as well anyway, and the pauses in sound playback were just a predictable sound effect of the CPU's high load. So how do I stop pulseaudio from loading at startup? Removing the "70pulseaudio" file from /etc/X11/Xsession.d/ didn't help.

---

### Post by gfxfreak on 2008-11-01
Hi, I've had the same problem back when I used Hardy along with an Audigy SE card (no hardware mixing), Rhythmbox used to skip ugly specially when using compiz-fusion but I found the perfect solution: OSS4, it's perfect for onboard sound and clean software mixing, no high cpu load, no compatibility problems (openal games like openarena + rhythmbox + pidgin + flash), if you have onboard sound or any card without hardware mixing I suggest you try it.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Malcolm on 2008-11-02
Thank you, I'll definitely try that out. I do have an onboard sound card so your solution looks like the way to go. At the moment, however, I'd just like to disable pulseaudio permanently, because those high CPU usage peaks happen and slow down everything for a few seconds even if I'm using ALSA or OSS.

---

### Post by domi007 on 2010-03-10
Same here..listening to music or watching a DVD and then BANG! pulseaudio uses suddenly 100% CPU making my computer freezing my DVD stopping and jumping...please, if you have a solution I would really appreciate it.

Sorry for bumping up an old thread...

My PC:
Ubuntu 9.10
Intel P4 Mobile 2.2 GHz
AC'97 Sound

DOMy

---

### Post by RJARRRPCGP on 2010-03-10
> **domi007 said:**
> Same here..listening to music or watching a DVD and then BANG! pulseaudio uses suddenly 100% CPU making my computer freezing my DVD stopping and jumping...please, if you have a solution I would really appreciate it.

Sorry for bumping up an old thread...

My PC:
Ubuntu 9.10
Intel P4 Mobile 2.2 GHz
AC'97 Sound

DOMy

Sounds like DMA possibly got disabled! You must check the logs for stuff relating to ATA.

You may have a damaged IDE cable!

---

### Post by domi007 on 2010-03-10
> **RJARRRPCGP said:**
> Sounds like DMA possibly got disabled! You must check the logs for stuff relating to ATA.

You may have a damaged IDE cable!

Nope, that's not it. I checked, and DMA is enabled.

Anyway I just disassembled and re-assembled this laptop, and checked everything inside carefully. It uses anyway a MultiBay DVD which means there is no IDE cable, the optical drive connects directly to the motherboard (and so does the HDD too).

And the problem exists also when I am not playing a DVD but playing some music from the HDD.

DOMy

---

### Post by matt-fender on 2011-03-19
Maybe not a solution for it works for me, but I go to

system > Administration > System Monitor > Processes

and right click pulseaudio and change its priority to a nice value of 0.

There is a way to make this a permanent setting, you will have to Google how to do it as I cannot remember.

A search along the lines of, "change priority permanent ubuntu" should throw up some interesting results. :D

---


---
title: "pulseaudio"
date: 2008-12-01
forum: Multimedia Software
---

### Post by nzadLithium on 2008-12-01
I am wondering what pulseaudio does that alsa doesn't already do? 

Everytime I start up my pc, to get apps able to record from my sound card I have to killall pulseaudio. I then leave it dead for the rest of the time i'm on and have currently found no apps that require pulseaudio for sound.

Are there any apps that won't run without pulseaudio? Why would I actually want pulseaudio when sound works absolutely fine without it loaded?

At the moment I can't see any viable reason why I would want pulseaudio. So i guess basically i'm asking why is pulseaudio included with ubuntu?

---

### Post by kostkon on 2008-12-01
PulseAudio offers many things but the most important is audio mixing.

Most of the soundcards (especially the on-board ones) don't have hardware mixing capabilities (or their driver does not use it. Some may have, but very limited (like only two sounds at the same time). Thus, you need something that will offer this at the software level, a software audio mixer. This will allow you to have many sounds at the same time, very important for a desktop operating system.

---

### Post by nzadLithium on 2008-12-02
Well, I had software mixing in edgy, and feisty, and gutsy, and none of them had pulseaudio. Plus I got a hardware mixing card once I found that enemy-territory would not be able to use sound while alsa apps were. What other advantages does it give? XD

---

### Post by kostkon on 2008-12-03
> **nzadLithium said:**
> What other advantages does it give? XD
Other things include the ability to have individual volumes per application, move an audio stream from one device to another on the fly, network sound, conditional volume adjustment (e.g. when a VoIP call starts, the volume of all the other applications is automatically lowered) and some others.

What do you think? Does it worth it? [-o<

---

### Post by psyke83 on 2008-12-03
> **nzadLithium said:**
> Well, I had software mixing in edgy, and feisty, and gutsy, and none of them had pulseaudio. Plus I got a hardware mixing card once I found that enemy-territory would not be able to use sound while alsa apps were. What other advantages does it give? XD

It offers enhanced sound mixing, the ability to dynamically move audio streams between cards and across computers, per-application volume controls and much more.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Look at the appendixes for more information.

---

### Post by Conan on 2008-12-04
> **kostkon said:**
> What do you think? Does it worth it? [-o<

Honestly, no, it's not, not as long as apps like Wine don't play nice with it. The need for a software mixing daemon isn't nearly as pressing now as it was a few years ago; while there are still problem cards out there, most machines have pretty decent support with just ALSA now. The additional features are nice, but they're not really features most users will take advantage of, and pulseaudio causes enough problems to be a net negative overall.

I'm not saying it's bad tech, but I do think its premature for distros like Fedora and Ubuntu to be shipping it by default.

---

### Post by nzadLithium on 2008-12-04
well, I'm not sure if the padsp thing there will work for me, I shall have to try it, but assuming it does, how do i setup pulseaudio properly? ie enable 5.1, allow control of volume mixers properly so it doesn't mix things i don't want being mixed (ie pcm in with mic in?), etc etc. Is there some way to do this? Or is it done through the alsa and oss mixers?

Also, it says > WINE: Open the Wine Configuration application ("winecfg"). On the Audio tab, choose the ALSA driver, and leave everything else to default. If your sound stutters, choose the OSS driver instead, and use the "padsp" wrapper to launch the wine executable (via the terminal, or edit your shortcuts). I did this a long time ago, but pulseaudio still doesn't allow wine to access my microphone? Any ideas whats up with that?

---

### Post by vanadium on 2008-12-04
See the thread psyke83 linked to. The issue is that currently pulseaudio is poorly implemented in Ubuntu.

---

### Post by nzadLithium on 2008-12-05
ah kk XD Thx for your help guys :D

---


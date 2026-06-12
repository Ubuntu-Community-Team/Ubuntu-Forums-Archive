---
title: "Sound gets stuck while playing Torcs and in OOo"
date: 2008-11-26
forum: Multimedia Software
---

### Post by chandru.in on 2008-11-26
Hi,

When playing Torcs and when opening presentations with sounds effects, my sound system seems to get stuck (starts repeating same noise) and the app crashes.

However, I'm able to play music in Rhythmbox for long time without any problem.

---

### Post by chandru.in on 2008-11-29
Any help here?

From lspci:

> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by malmjako on 2008-12-01
> **chandru.in said:**
> When playing Torcs

I have this problem too. Can the sound system be restarted? I've tried /etc/init.d/alsa-utils restart (and reset as well), but the noise comes back on when alsa-utils is started again.

---

### Post by chandru.in on 2008-12-01
I have managed to hunt down the solution with some help from people over at LQ.

Creating ~/.openalrc withe the below two lines fixed it. Basically it is supposed to instruct openAL to use Pulseaudio.
```
(define devices '(alsa))
(define alsa-device "pulse")
```

For a system wide change, edit /etc/openal/alsoft.conf and change the device value in the section titled [alsa] as below.
```
device = pulse
```

Ubuntu rocks again.

---

### Post by Asem on 2008-12-17
Hello 

i had the problem with sound skipping in games like warzone2100 and my solution then was to kill pulseaudio before starting the game 

i think that the problen *is* that openal uses pulseaudio because when i changed the device section in alsoft.conf to alsa the games work fine without killing pulse

---

### Post by cram869 on 2008-12-18
> **malmjako said:**
> I have this problem too. Can the sound system be restarted? I've tried /etc/init.d/alsa-utils restart (and reset as well), but the noise comes back on when alsa-utils is started again.

My sounds devices were stuck in a bad state just today after killing mplayer, and I noticed that it stopped after running

/sbin/alsactl restore

It silenced my sound device, but it may not be any help for this thread's issue.

---

### Post by Mottq on 2009-07-21
But how and where do you create the .openalrc file?

---

### Post by sebovespa on 2009-07-21
i'm also get stuck in my sound configuration for 8.10 version.

i found that only my movie player has sound.

get frustrated in troubleshoot the problem. so just do this:

sudo killall pulseaudio
sudo alsa force-reload 

it work very fine.

and i do this every time after boot the system.

:(:(:(

---

### Post by chandru.in on 2009-07-22
I had posted about this in my blog few months ago.

[http://tuxychandru.blogspot.com/2008/12/making-openal-use-pulseaudio-in-ubuntu.html](http://tuxychandru.blogspot.com/2008/12/making-openal-use-pulseaudio-in-ubuntu.html)

---


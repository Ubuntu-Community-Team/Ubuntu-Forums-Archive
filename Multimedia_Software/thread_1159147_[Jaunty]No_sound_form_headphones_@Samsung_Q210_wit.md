---
title: "[Jaunty]No sound form headphones @Samsung Q210 with Jaunty + PulseAudio"
date: 2009-05-14
forum: Multimedia Software
---

### Post by RoestVrijStaal on 2009-05-14
Hi there,

I don't get any sound form my headphones at Jaunty.
Sound form the speakers goes luckily fine, but it's creepy silent when i put the headphones in my laptop.

Could somebody help me to make more live in my headphones?
I use Jaunty,  Samsung Q210 and Pulseaudio.

I've eaten the stickies, however, they didn't help...

---

### Post by RoestVrijStaal on 2009-05-23
1 week waiting -> Bump worth

Is there really anything I can do to solve it?:frown:

---

### Post by RoestVrijStaal on 2009-07-14
BUMP again :cry:

---

### Post by igorzwx on 2009-07-14
Do you need PulseAudio?
Remove the evil.

sudo killall pulseaudio

then complete removal

---

### Post by RoestVrijStaal on 2009-07-14
Well, I really don't know if need pulseaudio, but when i do lspci -v, a piece of the output is this:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Samsung Electronics Co Ltd Device c041
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Then I looked at [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel), the ICH9 Family isn't even mentioned. 

So I guess the whole sound handing at my installation is a kind of a chaotic  combination of ALSA/OSS/PulseAudio...and pulseaudio could be an essential part for playing audio, because it seems that alsa support my soundchip half....

Do you maybe have some more command to find it out how my sound is controlled / made?

---

### Post by igorzwx on 2009-07-14
You may need this:
[http://ubuntuforums.org/showthread.php?t=1211713](http://ubuntuforums.org/showthread.php?t=1211713)

I cannot help more, because I removed both ALSA and Pulse,
and installed OSS4

---

### Post by RoestVrijStaal on 2009-07-14
igorzwx, the topic you pointed to me refers to so many solutiontryings / topic  that i completely don't know which I could try. :? Could you maybe more specific please?

---

### Post by igorzwx on 2009-07-14
If your headphones are USB thing, then you need ALSA.
Otherwise, you may try OSS4.

With OSS4, no USB audio devices at all.
Something else is not suppoted too:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS) 
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

read this:
[http://ubuntuforums.org/showthread.php?t=1212887](http://ubuntuforums.org/showthread.php?t=1212887)

I installed OSS4 on my boxes.
You have decide for yourself.

---

### Post by RoestVrijStaal on 2009-07-14
Well, the situation was easier than I thought.
After installing pulseaudio, ALSA is doing it's job normally and except my build-in mic, everything is working perfectly. 
The front mic does not really matter because it's covered by my hands when i'm typing. 

Thanks for the help igorzwx ;)

---

### Post by igorzwx on 2009-07-14
It looks like without Pulse one cannot now make his ALSA working.
It may change soon in some unpredictable way.
I had been combating the problems for months.
Now I have OSS4 and less headache.

---


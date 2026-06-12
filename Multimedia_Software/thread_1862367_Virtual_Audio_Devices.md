---
title: "Virtual Audio Devices"
date: 2011-10-16
forum: Multimedia Software
---

### Post by M1GEO on 2011-10-16
Hi All.  I am looking for something like Virtual Audio Cable for Windows, or vsound for Linux.

Essentially, I have a program that makes audio on the sound-card, but I want to feed this as a 'virtual line input' into another program.

Can anybody suggest a method of doing this? Vsound looks like it used to do it, but it uses old OSS device nodes (/dev/dsp), etc.  I just doubt it will work well with my Natty's sound architecture.

I also see references to packages like: snd-aloop and pcm-loopback; neither of these packages seem to exist in the repositories and so I am hesitant as to if they would work now?

Thanks in Advance.

---

### Post by M1GEO on 2011-10-20
Bump. Anyone?

---

### Post by M1GEO on 2011-11-15
Still no body?

---

### Post by TiberiusT on 2011-11-17
Not much help but better than what you've recvd so far ;)....I'm no expert but I reckon that a Pulseaudio monitor could do this. Whatever, I doubt yu need any extra packages. ALSA and Pulseaudio combined is an extremely powerful PC audio setup - I'd sugest reading up on those two, the possibilities seem endless.

Further, I'd really recommend going 11.10. It's got an upgraded Alsa and Pulseaudio 1.1 - the latter has a load of bugfixes which makes the whole experience much smoother.

This is a good place to start understanding ALSA [http://alsa.opensrc.org/Main_Page](http://alsa.opensrc.org/Main_Page) Unfo I can't really find a good upto date guide on Pulseaudio - it's one of those endless Google moments I'm afraid.

T

---

### Post by MoreOrLess on 2011-11-17
You can try emulating OSS with padsp:```
sudo apt-get install pulseaudio-utils
padsp vsound #or whatever the vsound command is
```

---

### Post by M1GEO on 2011-11-17
Thanks guys; I'll check those suggestions out. I'm not really after emulating anything in particular; just the most simple solution.  I have some audio coming on an alsa device (say hw:2) and usually it leaves on an alsa device (say hw:1). The software in between does demodulation of Phase/Quadrature signals on the incoming baseband (via hw:2) and returns pure audio (speech) on hw:2.  What I am looking to do, is to then feed this speech into another program.

I in essence need to create two imaginary devices in ALSA and link them together, so that, for example, anything put to hw:3 appears at hw:4.

This way, the demodulator program can write to hw:3 (instead of hw:2 - speakers) and another program (e.g. DSP audio processing software or a recorded such as audacity) can read hw:4 and gets the audio.

It's kinda hard to explain. Thanks for any input however though, I'll check those suggestions.

---


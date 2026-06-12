---
title: "Surround sound choppy as if cpu was overloaded"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by tszanon on 2006-12-02
Hi,

I'm having a problem similar to one I had in the past...here it goes:
I use xmms to play audio files, mostly mp3. I bought this new computer with an onboard sound card (it's a Gigabyte GA-M55SLI-S4, powered by the NVIDIA nForce4 SLI chipset, Realtek ALC850 Audio Codec -- in xmms I saw "Nvidia CK804" as a 'mixer card', but don't know exactly what it is).

When I play music using stereo sound (configuring ALSA, in xmms, to use the "default" device), no problems. The problems begin when I try to use surround sound. It doesn't matter if it's just plain surround sound (using just 2 of the 6 channels) or if it's a custom device (in order to use all 6 channels, simulating surround sound).

And what happens? Simple. It looks like the cpu is overloaded. The music is played slowly and, a few times per second, it is interrupted, as if it were briefly paused.

It's strange to me, because it works, for example, in games (Doom3). No problems.

I don't know what may be the problem. I tried to check this problem in RhythmBox, but there was no option for me to choose the sound device. :( 

Anyone got a suggestion on what should I check?

---

### Post by Sigudian on 2006-12-25
I have the exact problem.
at first i had it working, but the right speaker had a so low volum,
since it was a 5.1 soundcard i created a file called ~/.asoundrc
and i wrote
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

```
in the file. i did this to enable 5.1 channel, but now its all choppy at 2.1(have not tested running at 5.1.

---

### Post by ViperKnight on 2007-01-08
I've had the same problems with my Realtek/Nvidia ALC850.

At first I could only get sound out of the front 2 speakers but I eventually got 5.1 working but XMMS was ridiculously choppy.  Turned out to be buffer problems (which is what I suspected).

Try this:
1. Go to the XMMS Preferences.
2. Configure for ALSA.
3. Set Audio Device to "default"
4. Click the "Advanced" tab.
5. Change values to this:
Buffer Time = 5000ms
Period Time = 1ms
XMMS Buffer Time= 1000ms
6. Click Apply and restart your song playback.

Hopefully that helped :)

---

### Post by tszanon on 2007-01-08
> **ViperKnight said:**
> I've had the same problems with my Realtek/Nvidia ALC850.

At first I could only get sound out of the front 2 speakers but I eventually got 5.1 working but XMMS was ridiculously choppy.  Turned out to be buffer problems (which is what I suspected).

Try this:
1. Go to the XMMS Preferences.
2. Configure for ALSA.
3. Set Audio Device to "default"
4. Click the "Advanced" tab.
5. Change values to this:
Buffer Time = 5000ms
Period Time = 1ms
XMMS Buffer Time= 1000ms
6. Click Apply and restart your song playback.

Hopefully that helped :)

What can I say? It just worked!!! The only different thing I had to do was selecting "ch51dup", not "default" audio device (ch51dup was the one I created in .asoundrc in order to use all 6 channels).

Thanks a lot! Your suggestion was worth the wait!

---

### Post by ViperKnight on 2007-01-08
The funny thing is........I've only been using Linux for 2 days now :P

Although I do know my fair share about audio systems.........

Ubuntu is the first Linux installations I've ever used (although I have got dual-boot with XP just in case) and I'm lovin it :D

---

### Post by tszanon on 2007-01-09
> **ViperKnight said:**
> The funny thing is........I've only been using Linux for 2 days now :P

Although I do know my fair share about audio systems.........

Ubuntu is the first Linux installations I've ever used (although I have got dual-boot with XP just in case) and I'm lovin it :D

So, welcome! Hope Ubuntu fits your needs!

---

### Post by panteraz on 2007-10-26
> **ViperKnight said:**
> I've had the same problems with my Realtek/Nvidia ALC850.

At first I could only get sound out of the front 2 speakers but I eventually got 5.1 working but XMMS was ridiculously choppy.  Turned out to be buffer problems (which is what I suspected).

Try this:
1. Go to the XMMS Preferences.
2. Configure for ALSA.
3. Set Audio Device to "default"
4. Click the "Advanced" tab.
5. Change values to this:
Buffer Time = 5000ms
Period Time = 1ms
XMMS Buffer Time= 1000ms
6. Click Apply and restart your song playback.

Hopefully that helped :)

OMG!!! It works like charm!!!! THANKS A LOT!!! I OWE YOU!!!! respect!

---


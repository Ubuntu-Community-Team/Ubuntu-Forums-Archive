---
title: "Realtek ALC882 driver installation"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by eXecu7or on 2006-07-21
Hello,

I am somewhat new to the linux world, but I have a lot of Windows experience.

I've just installed 6.06 and, so far, I've managed to:

1. update the distro and install various components using guides available on the net.
2. Get xgl to work on my X800 (wow, it's quite a treat).

However, I am yet to discover how to enable the digital output on my ALC882 codec (Asus P5WD2 Premium mobo). Or maybe even get DD Live to work? :). It would be great to get the digital out to work, since I own a 5.1 speaker system with a decoder box and the only way to get more than stereo is by using coaxial digital out.

Thank you in advance for your answers.

P.S.

I've tried compiling the driver from [www.realtek.com.tw](www.realtek.com.tw), but I don't seem to get anywhere. [(driver download location)]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True")

---

### Post by jay_cee on 2006-07-22
I'm not an expert, but I struggled through my SPDIF. I think I've got a slightly different chipset, but I'll throw this out anyway.

Are you sure you need new drivers? Mine worked out of the box (after some configuration twiddling)

do

>aplay -L

is there an "spdif" device?
If so - good, if not - dunno! Maybe you do need new drivers.

Now launch alsamixer
>alsamixer

scroll to the right until you see "IEC958 Playback AC97-SPSA". Move that setting to 100%. This can also be acessed through other mixers. I know that I can see it with the KDE audio mixer (I'm on Kubuntu). I'm sure it is there on the gnome equivalent as well.

Then launch "totem" (my media player of choice), go to "preferences->audio" and select AC3-passthrough. Now see if you can play a DVD. 

I've had mixed success with other applications, but here are a couple of things I've learned about my setup:
1) Audio setup is a bit different for every app. Pretty annoying, I feel like I'm back in 1980. I've gotten most apps working at this point. I still don't have audio mixing working. Only one app can access the sound card at a time. ALSA has a built in mixer called dmix, but I haven't gotten that working yet.

2) My SPDIF setup (not sure whether its my soundcard or my receiver) will only work with 48000 KHz stream. DVDs are 48K (which is why I recommend starting with a DVD). I was able to get 44100 KHz MP3s working, but I had to configure ALSA to do sample-rate conversion. I can post my config for that later if you decide you need to go that route.

g'luck!

---

### Post by moeFinley on 2006-07-22
You can do a test of you digital output using:

aplay -Dplug:iec958 "test.wav"

I have a similar problem, I can't get anything to playout through the digital except when I run the command above?!?

Anyway I hope this helps.

---

### Post by eXecu7or on 2006-07-22
jay_cee's ideea worked. Unmutting digital out did the trick. :)

One question, though: is it possible to somehow redirect the line-in and/or cd-in input so it gets digitized and then outputed on the coaxial conection? I ask this because I have a tv tuner card and it's annoying to consantly switch between digital and analog on my sound system.

---

### Post by jay_cee on 2006-07-23
Cool beans. Glad you got it working.

I don't have a clue about your followup question. I'm sure its possible, but I don't have a tuner card. Installing mythtv might be the path of least resistance...

---

### Post by eXecu7or on 2006-07-24
The TV tuner works very well using tvtime (it's a winfast tv2000/xp  expert based on the Conexant chipset). But I have to switch to analog every time I want to watch TV. So I was wondering if this sound rerouting can be done at OS level.

---

### Post by LTBP5WD2 on 2006-11-02
I also have the Asus P5WD2 Premium motherboard.  I use the digital sound as well and have no sound.  How do I get sound out of this motherboard?  I am just 1 hour into using Ubuntu.

---

### Post by moeFinley on 2006-11-03
> **LTBP5WD2 said:**
> How do I get sound out of this motherboard?

Type the following into the terminal
```
aplay -Dplug:iec958 "test.wav"
```
Replace "test.wav" with a uncompressed wav file on your computer.

This worked on mine, but of course isn't very useful other than for testing you have everything connected correctly and drivers setup.

Another thing to try is in Movie Player (totem) switch 'Audio output type' t AC3 Passthrough. 

I never got my built in sound card's digital out to work the way I wanted (all audio output through it).  I'm currently using a Sound Blaster Extigy which I had spare.  This work perfectly as soon as I plugged it in.

---


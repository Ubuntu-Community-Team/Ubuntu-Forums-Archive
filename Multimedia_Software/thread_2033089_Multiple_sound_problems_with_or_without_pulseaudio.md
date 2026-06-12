---
title: "Multiple sound problems with or without pulseaudio"
date: 2012-07-25
forum: Multimedia Software
---

### Post by landeel on 2012-07-25
Kubuntu 12.04 here.

This system is built for heavy gaming and videos, it has a Zogis GeForce GTX 550 Ti which connected to my TV via HDMI.

I'm using the sound card that's integrated into the GPU, I have made it my primary card in alsa by changing "/usr/share/alsa/alsa.conf":

> 
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0


became:

> 
defaults.ctl.card NVidia
defaults.pcm.card Nvidia
defaults.pcm.device 7


I have never liked pulseaudio, and alsa does everything I need faster, so pulseaudio is usually the first thing I remove in my installation.

> sudo apt-get purge pulseaudio

However those are the problems I have without pulseaudio:

1) dolphin-emu produces some weird noises randomly.


2) The 2 games I have developed which use SDL for sound have sound distorted and failing a lot. 
[http://cmcgames.darkphear.com/2012/01/yagac.html]("http://cmcgames.darkphear.com/2012/01/yagac.html")
[http://iceroyds.darkphear.com/]("http://iceroyds.darkphear.com/")
Other games that use SDL for sound seem to have the same behaviour.
When I run it in the console I have a LOT of:
> ALSA lib pcm.c:7339:(snd_pcm_recover) underrun occurred


3) MAME has serious latency in sound (about half a second). It uses SDL for sound too.


4) MAME running old games such as twinbee have a terrible crackling sound that makes it unplayable.
There are two lame workarounds for this; one is reducing sampling rate below 22050 (argh!); other is using the alsa oss wrapper : "aoss mame twinbee -audiodriver dsp" which is a little better.



I have tried removing the Ubuntu SDL packages and installing SDL from the official page, but it didn't change a thing. The bug seems to be deeper, maybe in libasound2 or in alsa itself.

Well, with all this trouble I was FORCED to reinstall pulseaudio to see if things would just work.

> sudo apt-get install pulseaudio

It does solve the described problems I had with just alsa.

However I'm developing this small HTML5 game: > [http://darkphear.elementfx.com/webgames/test1/](http://darkphear.elementfx.com/webgames/test1/)

Sound works fine with alsa, but it has problems with pulseaudio. (Press ENTER or Z to shoot.)

1) In firefox the sound effect sometimes plays at the right timing, sometimes it plays half a second later, sometimes it doesn't play at all.

2) In google-chrome the sound effect always plays at the right timing, but it seems to cut before the sample finishes.


I have tried other HTML5 games, and they seem to have the same issues with pulseaudio: [http://www.html5games.net/shooter/ninja-jarimaru/]("http://www.html5games.net/shooter/ninja-jarimaru/")


Right now I have disabled pulseaudio ("autospawn = no" in "/etc/pulse/client.conf"), and I only execute it when needed. This is a major annoyance and not really a proper solution.

Things won't just work with pulseaudio and things won't just work without pulseaudio. Why a desktop distro needs a sound server is beyond me, I don't really want pulseaudio, I just want alsa to work. 

But I would accept to shut up and use pulseaudio if things just worked.

What to do?

---

### Post by landeel on 2012-07-26
Nothing?

Well, I have made 2 bug reports:

Pulseaudio:
[https://bugs.launchpad.net/bugs/1029419]("https://bugs.launchpad.net/bugs/1029419")

Alsa:
[https://bugs.launchpad.net/ubuntu/+bug/1029414]("https://bugs.launchpad.net/ubuntu/+bug/1029414")

---

### Post by landeel on 2013-05-02
Well, for the record, I have fixed this issue by changing:
/usr/share/alsa/pcm/dsnoop.conf  -> period_size -> default -> changed 512 to 1024
/usr/share/alsa/pcm/dmix.conf  -> period_size -> default -> changed 512 to 2048

---


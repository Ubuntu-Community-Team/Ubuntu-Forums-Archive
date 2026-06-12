---
title: "Setting up audio from minimal install"
date: 2012-08-02
forum: Multimedia Software
---

### Post by sithpigeon on 2012-08-02
Hi there!

So, just for fun I decided to do a command line install of Ubuntu on a small partition on my laptop using the minimal installation disk (mini.iso). I've been having fun choosing each package I install so as to keep the install small, and have really only installed xorg, fluxbox, xterm, xfe, and chromium-browser so far in addition to what the minimal install put on. 

I'm at the point where I'd like to get the audio working, but the more I research audio with linux, the more confused I get. 

So my question is, what would one need to do in order to "install" audio on a minimal installation of Ubuntu? I presume I need to install an audio mixer and driver, but that seems too simple from what I've been reading. I'm guessing I'm quite confused at this point, and probably just need some clarification.

Thanks in advance!

---

### Post by Rodney9 on 2012-08-02
Thanks to Lidex

Re: Sound after minimal install
Along with your clean minimal install you'll need these packages:

```
alsa-base
alsa-utils
alsa-oss
gstreamer0.10-alsa
libasound2
libasound2-plugins
```



Fluxbox Guide

[http://tinyurl.com/7yf5o6s](http://tinyurl.com/7yf5o6s)

Openbox Guide

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

Rodney

---

### Post by sithpigeon on 2012-08-02
Hi Rodney9,

Since I'm trying to really understand what's happening with what I install, would you mind briefly clarifying what each of those packages does, or pointing me to something that would?

Also, I installed the packages, restarted and then typed:

```
sudo aplay sound.wav
```

and I don't hear anything but I see:

```
Playing WAVE '/home/adam/downloads/sound.wav' : Signed 16 bit Little Edian, Rate 32000 Hz, Mono
```

In addition, 

```
sudo lspci -v | grep -A7 -i "audio"
```

outputs

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97Audio Controller (rev 03)
...
```

---

### Post by sithpigeon on 2012-08-25
Started looking into this problem and randomly decided to try

```
alsactl init
```

and my sounds started playing. Now it's always working even after restart. Not sure what I did, but glad it's working now. If anyone can explain what I did that would be awesome.

---

### Post by funyotros on 2012-09-17
```
alsactl init
```

Works for me too!!
Thanks! Can someone explain this?

---


---
title: "HDMI Sound Help--No Sound"
date: 2011-05-12
forum: Multimedia Software
---

### Post by AndreasMet on 2011-05-12
Hi,
Can someone point me in the right direction.  I cannot figure out how to get sound through my HDMI.  I'm a newbie.

I can get sound through my headphones.

Any help is much appreciated.

Thanks.

Here is the result of my aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Generic USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by lidex on 2011-05-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by d3ngar on 2011-05-15
Hi,

I also can't get sound working on my HDMI ATI card.

I posted the output here:
[http://www.alsa-project.org/db/?f=a7687c3bbe5773092dbcb9c4ce9686d6c598ca23]("http://www.alsa-project.org/db/?f=a7687c3bbe5773092dbcb9c4ce9686d6c598ca23")

The device in question should be card 1 device 3. I can't get 
> aplay -Dplughw:1,3 SOMESOUND.wav 
to play.

But the device is definitely there and I can select it in alsamixer. I made sure it's unmuted..

Any suggestions?

---

### Post by lidex on 2011-05-15
> **d3ngar said:**
> Hi,

I also can't get sound working on my HDMI ATI card.

I posted the output here:
[http://www.alsa-project.org/db/?f=a7687c3bbe5773092dbcb9c4ce9686d6c598ca23]("http://www.alsa-project.org/db/?f=a7687c3bbe5773092dbcb9c4ce9686d6c598ca23")

The device in question should be card 1 device 3. I can't get 
 
to play.

But the device is definitely there and I can select it in alsamixer. I made sure it's unmuted..

Any suggestions?

Try adding this to alsa-base.conf:
```
options snd-hda-intel probe_mask=3 position_fix=3
```
No joy with that remove and try this instead:
```
alias sound-slot-0 snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer position_fix=1
```

To edit:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save your changes and reboot to initialize.

---

### Post by d3ngar on 2011-05-16
> **lidex said:**
> Try adding this to alsa-base.conf:
```
options snd-hda-intel probe_mask=3 position_fix=3
```

Unfortunately this just got rid of the other audio device that is on the motherboard, the Realtek one. I can still see it in alsamixer, but I can't select it in the Sound preferences, so nothing works at all.
> 
No joy with that remove and try this instead:
```
alias sound-slot-0 snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer position_fix=1
```

This too didn't solve the problem, but the Realtek card is again not recognised properly. It does work however as some generic device and is labeled Internal Audio by Linux.

Please let me know if there is anything else I could still try.

Thanks, C

---

### Post by cullyjoker on 2011-05-18
Have you upgraded to Ubuntu 11 yet?

I could not get any sound out of my HDMI and tried everything I could find to get it to work. So eventually gave up (this was 6 months ago).

upgraded to ubuntu 11 last week and HDMI sound magically appeared :-) without me doing anything else.
Seems to be either/or though (can't have sound out of the headphone jack and HDMI simultaneously)

This was on an Acer Aspire r3700

CJ

---

### Post by d3ngar on 2011-05-19
> **cullyjoker said:**
> Have you upgraded to Ubuntu 11 yet?

I could not get any sound out of my HDMI and tried everything I could find to get it to work. So eventually gave up (this was 6 months ago).

upgraded to ubuntu 11 last week and HDMI sound magically appeared :-) without me doing anything else.
Seems to be either/or though (can't have sound out of the headphone jack and HDMI simultaneously)

This was on an Acer Aspire r3700

CJ

Hi Cj,

Yes, I have! Unfortunately this didn't really work for me.
The sound is still not working via HDMI.

Thanks,

Chris

---

### Post by xzyzzy on 2011-05-19
I spent many hours systematically toying with alsa and then pulseaudio, trying different drivers, Xorg configs etc. but still couldn't get any HDMI audio output. 

What finally did the trick for me was disabling the standard sound device in the sound settings. After that, it just worked :) Disabling normal audio (but obviously not HDMI audio!) in the BIOS might have the same effect if you have an option to do so (I didn't).

---

### Post by d3ngar on 2011-05-20
> **xzyzzy said:**
> I spent many hours systematically toying with alsa and then pulseaudio, trying different drivers, Xorg configs etc. but still couldn't get any HDMI audio output. 

What finally did the trick for me was disabling the standard sound device in the sound settings. After that, it just worked :) Disabling normal audio (but obviously not HDMI audio!) in the BIOS might have the same effect if you have an option to do so (I didn't).

Thanks for the suggestion, but I tried this. Unfortunately no result.

---

### Post by Toz on 2011-05-20
I'm not sure from your initial post whether you are getting any sound out the speakers at all or not. Unfortunately, I won't be able to help with that. 

However, I have ATI HDMI on my laptop and to get sound to go through HDMI and out of my TV, I had to install pavucontrol (Pulseaudio Volume Control) ```
sudo apt-get install pavucontrol
``` and manually set the application to use the HDMI port. To do this, I would fire up pavucontrol and then start up the video file. Back in the pavucontrol application, on the Playback tab, a new entry for the application playing the media file will show up. I simply change "Internal Audio" to "HDMI" and the sound works.

---


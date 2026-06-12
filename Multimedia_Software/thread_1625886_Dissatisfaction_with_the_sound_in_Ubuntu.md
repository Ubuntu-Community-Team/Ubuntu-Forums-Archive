---
title: "Dissatisfaction with the sound in Ubuntu"
date: 2010-11-19
forum: Multimedia Software
---

### Post by RasH on 2010-11-19
I've been searching the web trying to solve my audio problems for quite a while. Nothing seem to help, so I've decided to actually ask...

I'm having problems with the sound on Ubuntu. I'm using 10.10 at the moment but it was just the same on 10.04.

Let me start by saying that the sound actually works. The problem is that it's far inferior to the sound I get on Windows 7 (and XP as well). This is how I know it's not a hardware problem. 

#1
First and most important issue is that the sound is way too quiet. I have all the sliders set to maximum in alsamixer. Nothing seems to help. It's at least twice as loud on Windows.

#2
The sound is also slightly distorted. It's not terribly distorted but still it's far from clear and it's definitely noticeable.

#3
The sound is very flat. I've tried to find a system-wide equalizer - no luck. Also, some system-wide environmental effects would be nice (like Concert Hall, Bathroom, Sewer, Corridor etc.). This kind of stuff comes with the drivers to my sound card on windows and it really makes the difference. Is there anything like that for linux?

#4
This is not really an issue but it might be somehow related. I use headphones. I go to the Sound Preferences > Output and I choose connector: Analog Output - I can hear the sound. When I choose Analog Headphones - no sound. Also in alsamixer headphones are set to 00 and can't be changed (the slider is missing as well). I know I can just use the Analog Output and I do, but why the heck the Headphones option doesn't work?

This might be useful to anyone who could help:

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any help appreciated.

---

### Post by RasH on 2010-11-20
Bump?

Please someone help with any of these problems. I've tried everything I've found and nothing helped.

---

### Post by cchhrriiss121212 on 2010-11-21
Try comment #4 on here:
[http://forums.opensuse.org/english/get-help-here/hardware/402500-no-sound-realtek-alc889a-under-11-1-a.html#post1913148](http://forums.opensuse.org/english/get-help-here/hardware/402500-no-sound-realtek-alc889a-under-11-1-a.html#post1913148)

---

### Post by RasH on 2010-11-22
> **cchhrriiss121212 said:**
> Try comment #4 on here:
[http://forums.opensuse.org/english/get-help-here/hardware/402500-no-sound-realtek-alc889a-under-11-1-a.html#post1913148](http://forums.opensuse.org/english/get-help-here/hardware/402500-no-sound-realtek-alc889a-under-11-1-a.html#post1913148)

Thank you for your reply. Unfortunately this doesn't help me because as I said, I do have sound. It's quality is the problem.

---

### Post by cchhrriiss121212 on 2010-11-23
I did read your post, and I can tell from searching that your low sound is affecting all users with this chip. I thought you might like to try changing the asoundrc to a different model, which was the best idea I could come up with.

---


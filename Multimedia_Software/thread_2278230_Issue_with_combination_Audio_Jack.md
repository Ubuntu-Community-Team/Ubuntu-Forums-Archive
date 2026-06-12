---
title: "Issue with combination Audio Jack"
date: 2015-05-14
forum: Multimedia Software
---

### Post by aaroncampbell2 on 2015-05-14
Well, it's been about 11 months since I posted this the first time ([Issue with combination Audio Jack]("http://ubuntuforums.org/showthread.php?t=2230136")), and I'm still struggling with it. For almost a year I've been doing all voice/video chats through my tablet because I can't use a headset with my laptop if I'm running Ubuntu (and dual boot is such a pain).

Basically, I have an Asus S400CA laptop. When I installed 14.04 on it the first time, almost everything seemed to work great (seriously: wifi,  touchscreen, audio, everything...it was SO nice!). Unfortunately, the one thing that didn't was a headset. I has a single 3.5mm jack that handles both output and input (the  kind commonly used with all cell phones), but with Ubuntu it will only use the jack for output, and doesn't seem to recognize the mic. The single combo-jack for audio/mic works under Windows 8 (ugh) so it's not a hardware issue.

Old Alsa Info from 14.04 11 months ago: [http://www.alsa-project.org/db/?f=be165c9f5ebb9907ebba53db923f44bf762d0894](http://www.alsa-project.org/db/?f=be165c9f5ebb9907ebba53db923f44bf762d0894)
Current Alsa Info: [http://www.alsa-project.org/db/?f=b2d205e49d5a715e4504ec50d5797e1d9659ff10](http://www.alsa-project.org/db/?f=b2d205e49d5a715e4504ec50d5797e1d9659ff10)

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
```

I opened a bug but have had no responses at all: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1332233?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1332233?comments=all)

Does anyone by chance know of a work around? Or any other relevant data I could supply?

---

### Post by dino99 on 2015-05-15
ubuntu use pulseaudio now; so its not a surprise you only get one answer helping you.
install pavucontrol to find the good settings

---

### Post by aaroncampbell2 on 2015-05-15
I installed pavucontrol, and looked at it. It seems pretty similar to the built in controls I already saw in the system sound settings. Having said that, when I plug in a headset it shows two options in the "Output Devices" tab, "Speakers (Unavailable)" and "Headphones (plugged in)" (unplugging the headset makes Speakers available and sets the Headphones to unplugged). However, the "Input Devices" tab only offers "Microphone" which uses the internal mic and not the headset mic.

Basically: I have a different UI but the exact same problem.

---


---
title: "Sound Blaster X-fi Problem"
date: 2008-09-30
forum: Multimedia Software
---

### Post by Soilworker on 2008-09-30
So I'm fairly new to linux and ubuntu so bare with me here. I followed the OSS installation guide in the Ubuntu community docs section and I got that to work fine and everything but I can't get sound to come out of my speakers when I use Amarok or any other application. If I use "osstest", when the test reached the part where it tests my Sound Blaster X-Fi I get sound. I have tried to configure the GNOME Mixer/Volume Control but when I go to "Volume Control Preferences" the only device is "High Definition Audio Ad1988b..." device which produces no sound when I run "osstest" but does not explicitly fail. I have changed the output plugin in Amarok to oss but still no luck, any ideas?

I'm running:
EDIT: Ubuntu 8.04 64bit
Sound Blaster X-Fi Xtrememusic

Thanks in advance!

---

### Post by nightcrawler27 on 2008-09-30
Have you tried using ALSA instead of OSS? Despite OSS supposedly being the "standard, cross-platform, open API" I I have had much greater success with ALSA than OSS. If you are worried about compatibility with "OSS only" applications, ALSA does have OSS emulation. But since you said you are new to Linux I doubt you have any specific preference or requirement, you just want the damn thing to work right :)

Nightcrawler27


> **Soilworker said:**
> So I'm fairly new to linux and ubuntu so bare with me here. I followed the OSS installation guide in the Ubuntu community docs section and I got that to work fine and everything but I can't get sound to come out of my speakers when I use Amarok or any other application. If I use "osstest", when the test reached the part where it tests my Sound Blaster X-Fi I get sound. I have tried to configure the GNOME Mixer/Volume Control but when I go to "Volume Control Preferences" the only device is "High Definition Audio Ad1988b..." device which produces no sound when I run "osstest" but does not explicitly fail. I have changed the output plugin in Amarok to oss but still no luck, any ideas?

I'm running:
Ubuntu 8.10 64bit
Sound Blaster X-Fi Xtrememusic

Thanks in advance!

---

### Post by Soilworker on 2008-09-30
Well what I read was that the Sound Blaster X-Fi cards only worked with oss so I just tried that right from the get go. I believe in the guide I stopped alsa from running so now I can't get that to work. I think my problem is that I need to change the device that the oss mixer uses from the "High Definition Audio AD1988B" to my sound blaster card but I'm not quite sure how to do this. I also could be completely off on my inuition lol. But yeah I don't really care what it uses provided that it works.

---

### Post by nightcrawler27 on 2008-09-30
Well, I'm a bit rusty on OSS, so I can't say I can totally help you with OSS. However:

[http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

It's a beta, but I have read on other forums that it does work. Give it a spin, what do you have to lose?

Nightcrawler27

> **Soilworker said:**
> Well what I read was that the Sound Blaster X-Fi cards only worked with oss so I just tried that right from the get go. I believe in the guide I stopped alsa from running so now I can't get that to work. I think my problem is that I need to change the device that the oss mixer uses from the "High Definition Audio AD1988B" to my sound blaster card but I'm not quite sure how to do this. I also could be completely off on my inuition lol. But yeah I don't really care what it uses provided that it works.

---


---
title: "Sound Sputtering"
date: 2009-05-30
forum: Multimedia Software
---

### Post by wellimaginethat on 2009-05-30
I've been using Ubutnu on and off for the past two years but am still terrible at fixing problems, apologies in advance.

Recently, while I've been playing music on songbird the music will stop and be replaced by a strange series of sounds. The only way I can really describe it is a sputtering sound. It happens with anything that makes sound after that point. Usually the only way to get the sound to work again is to restart the system. Over the past week the interval between the system boot and the start of the sputtering has become shorter and shorter. Now it sputtering starts whenever I try to play music.

I've tried all the steps on the Comprehensive Sound Problem Solution guide up to the start of step four, but did not continue to get the drivers from a fresh kernel or any of the following steps because the guide seems to be geared towards the problem of no sound at all, rather than the wrong sound.

My soundcard is ATI IXP sb400, I checked the alsa project and found the driver atiixp. So I have tried the following ```
[SIZE=2]sudo modprobe snd-atiixp[/SIZE]
```

I've had a lot of problems with this soundcard and ubuntu over the past two years, but have never asked for specific help, just went through google hoping to find something.

If I need to provide more information, please tell me, I'm a bit of a newbie.

Thanks again

By the way, the Ubuntu start up sound is working.

---

### Post by madverb on 2009-05-30
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by rookcifer on 2009-05-30
Hate to say it, but Pulseaudio might be the culprit.  I really hate PA and that many distros are forcing it on us.

If you have exhausted *all* other possible troubleshooting steps, then I think you should uninstall pulseaudio (sudo apt-get remove pulseaudio).  I have noticed that my sound will often crackle with PA enabled, but it is rock solid if I remove it.

---

### Post by wellimaginethat on 2009-05-31
Thanks!
I followed the steps in the linked guide and that seems to have fixed the problem. If it starts acting up again I'll consider uninstalling pulse audio, but at the moment it's working.

---


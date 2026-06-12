---
title: "Pulse Audio... What Happened?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by talkingwires on 2008-06-14
I have been using Linux off and on since 1998. I deleted my Windows partition in 2004, when I started using Ubuntu as my primary operating system. I had heard about the "Linux audio problem", but never experienced it until Hardy dropped.

Ironically, Pulse Audio was supposed to fix many of the audio problems other Linux users had experienced. But now I find that Flash videos no longer have audio, or any other embedded objects on web sites, unless I stop Amarok's random playlist. But then, no applications can play audio and Amarok freezes.

It seems strange that after using Linux for ten years, I only start to have audio problems with Pulse Audio and Hardy. All the common problems that other users have been complaining about for years, but never experienced. What happened?

---

### Post by Fingel on 2008-06-14
Yea its pretty unfortuneate that pulseaudio's main debut has been so buggy. And its even worse that the fix for the problem is so simple, it should be enable by default. Install libflashsupport and flash should play nice with other apps again.

---

### Post by dynamethod on 2008-06-14
Yeah that sucks actually, i dont know whats going on behind the scenes but its as if one program hogs the sound and others cant use it, like you say about flash etc.

I have to restart firefox after say watching a video on youtube with sound, to listen to music from amarok.

---

### Post by sonicb00m on 2008-06-14
I also never had audio issues until Pulse. It just doesn't work fullstop for me, so i've had to uninstall.

---

### Post by Tomatz on 2008-06-14
```
sudo apt-get install libflashsupport
```

Reboot

That will fix the flash "no sound" problem ;)

---

### Post by talkingwires on 2008-06-14
> **Fingel said:**
> Yea its pretty unfortuneate that pulseaudio's main debut has been so buggy. And its even worse that the fix for the problem is so simple, it should be enable by default. Install libflashsupport and flash should play nice with other apps again.Thanks for the tip. I need to restart anyway, as neither Flash or Amarok will play sound at the moment. I'll post again in a bit after I've tried it out...

---

### Post by markbuntu on 2008-06-14
The flash problem is fixed in flash 10 and the new libasound2 that is not in the repos yet. If you have Firefox3.0rc1 or rc2 or flash 10b you need to remove libflashsupportfor flash to work properly

I have given up on pulseaudio myself.

---

### Post by talkingwires on 2008-06-14
> **markbuntu said:**
> The flash problem is fixed in flash 10 and the new libasound2 that is not in the repos yet. If you have Firefox3.0rc1 or rc2 or flash 10b you need to remove libflashsupportfor flash to work properly

I have given up on pulseaudio myself.I installed libflashsupport as recommended above, so far it seems to have cleared up the problems I was experiencing. Why isn't it installed by default or required by the flashplugin-nonfree package?

Did you revert back to ESD?

---

### Post by ahildoer on 2009-02-17
I automated the process of installing flash 32bit and 64bit in Ubuntu Desktop. It even works with pulseaudio. It works in feisty, gutsy, hardy, and intrepid.

Automated Flash Install:
[http://www.hildoersystems.com/index.php?option=com_content&view=article&id=76:automated-install-of-flash-10-for-ubuntu-desktop-32bit-and-64bit&catid=39:multimedia&Itemid=59](http://www.hildoersystems.com/index.php?option=com_content&view=article&id=76:automated-install-of-flash-10-for-ubuntu-desktop-32bit-and-64bit&catid=39:multimedia&Itemid=59)

---


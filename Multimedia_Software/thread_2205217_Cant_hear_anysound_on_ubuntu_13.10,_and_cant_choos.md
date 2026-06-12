---
title: "Cant hear anysound on ubuntu 13.10, and cant choose soundblaster recond3d as my sound"
date: 2014-02-12
forum: Multimedia Software
---

### Post by ogedi on 2014-02-12
[COLOR=#333333][FONT=UbuntuRegular]Hey I just recently installed Ubuntu 13.10, and one of the first things that I noticed is that I could only hear the sound either directly from my laptop, or out of my HD monitor. This caught my attention because I have a speaker system plugged into one of the audio jacks in my alienware m14xR2 laptops, and I couldnt get sound to come out of it. So I started messing around online seeing what could fix this, and it appears I've just broken it even more! Now I cant hear sound anywhere lol. Halp ;3[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Let me know what debug logs are needed.[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-02-12
This is always a good place to start: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> So I started messing around online seeing what could fix this, and it appears I've just broken it even more!

Be more specific. No one can help you undo something unless you tell them what you've done...

---

### Post by jsgosselin on 2014-02-22
Hello there,

I also have a Alienware M14xR2 and running Ubuntu 13.10 64 bit. The Alienware M14xR2 has 3 left-side audio jacks: a headphone jack, and headset jack, and a microphone jack. So far, never been able to make the headphone jack working. I haven't tested the microphone jack yet. It is however easy to make the headset jack working (the middle one).

From *Ubuntu Software Center*, install *Gnome Alsa Mixer*.

From *Gnome Alsa Mixer*, check the *HP/Speaker* and *HP/Speaker Auto Detection*. The headset jack should now be properly working.

I'm still looking for a way to get the Headphone jack working.

Here are some link related to this issue:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1267675](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1267675)
[http://forums.creative.com/showthread.php?t=699748&page=12](http://forums.creative.com/showthread.php?t=699748&page=12)
[https://plus.google.com/114251447858061222694/posts/MnPLEVs486u](https://plus.google.com/114251447858061222694/posts/MnPLEVs486u)

---

### Post by jsgosselin on 2014-02-22
I think it is worth mentioning also that at some point, when I was trying to get sound working from the audio output jack in linux after a fresh install, I also ended up in the situation where the system was not seeing any audio card at all o.O.

I went back on my Windows 7 partition and applied the BIOS patch again (had to do it from time to time also when I was mainly in Windows...it is a known issue for a long time) and had my audio working again.

[http://www.dell.com/support/troubleshooting/us/en/19/kcs/kcsarticles/articleview?docid=564061](http://www.dell.com/support/troubleshooting/us/en/19/kcs/kcsarticles/articleview?docid=564061)

Good luck...

Jean-Sebastien

---

### Post by jsgosselin on 2014-02-22
In order to get your sound system back on track if you messed something up while trying to get it working, maybe you can try this :

[http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

Jean-Sebastien

---


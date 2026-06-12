---
title: "No audio after a fresh install on a Dell XPS 15"
date: 2011-06-28
forum: Multimedia Software
---

### Post by anthony62490 on 2011-06-28
Just got a brand new XPS 15 in the mail the other day. Under Windows 7, everything appears to work well enough. Once I installed Ubuntu though, the audio stopped working. 

After a quick Google session, I saw that a few other people have had the same problem, but no one seems to have a solution. Maybe I'll get lucky.

What makes this extra upsetting is that I sprung for the high quality JBL speakers with the built-in subwoofer.

Specs:

Processor	4x Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory	3012MB
Operating System	Ubuntu 10.04.2 LTS
Audio Adapter	HDA-Intel - HDA Intel PCH
HL-DT-ST DVD+-RW GT32N	
Kernel	Linux 2.6.32-32-generic (i686)
Desktop Environment	GNOME 2.30.2

---

### Post by beew on 2011-06-28
The Dell xps 15 has optimus and Linux doesn't work on it. If you cannot return it bumblebee may be your best bet.

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

You may also want to write to Nvidia, it is fine if they don't want to support graphic card switching for Linux, but it is ridiculous that with Optimus enabled you wouldn't be able to use the Nvidia card at all even though they support the card with Linux driver.

[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

---

### Post by anthony62490 on 2011-06-28
You mean to tell me that my Optimus graphics card also affects my audio? That is total crap! I expected to have a bit of trouble with video, but not with my music. Unbelievable.

---

### Post by anthony62490 on 2011-06-29
Okay, I have installed Bumblebee. It works just as intended. Video is crisp and skip-free; games are buttery smooth and without framerate issues.

But I still have no sound. Are you sure that sound is an Optimus issue? I'd like to know more about this.

---

### Post by beew on 2011-06-29
> **anthony62490 said:**
> Okay, I have installed Bumblebee. It works just as intended. Video is crisp and skip-free; games are buttery smooth and without framerate issues.

But I still have no sound. Are you sure that sound is an Optimus issue? I'd like to know more about this.

I am not sure, but I have read threads where basically nothing works on the XPS 15 because of Optimus.
Great that bumblebee fixes the video.

---


---
title: "Sound quality improvement (or at least try...)"
date: 2015-05-21
forum: Multimedia Software
---

### Post by Godgothic182 on 2015-05-21
Goggling for hours looking for a solution to the quality of linux sound and nothing appears to be feasible. I have read about equalizers, ALSA, Pulseaudio..... and no one seems to agree in a real improvement of the sound. In windows it is pretty easy, multiple programs able you to improve the sound. Actually, I use Hear in windows which allows me to enjoy really good sound in my HI-FI sound system.

 But what happens in linux? (currently using ubuntu 15.04), well it sounds, that's something, but for those who really love enjoying good sound and better in HI-FI systems, we found linux sound empty and really poor. 

I came across with ubuntu studio....looks nice and cool, but do it really sounds better? I mean, It is supposed to be designed for high quality sound editing, images, photographs, videos.... I wonder if ubuntu studio has different audio system than ubuntu (standard). If it does, could it be possible to implement it in normal ubuntu (probably I am saying something with nonsense, but I just want to ask ).

I know too many people have asked and talked about this, I just ask for a solution or something that could improve the sound and not just with a simple equalizer.

In terms of render and other things linux beats windows by far. However, other even basic thins such as sound....may not be so good (from my point of view)

Other thing that comes to my mind is the possibility of using a dedicated graphic card instead the intel one when you need it in laptops that have two graphic cards (one dedicated). I tryed to use bumblebee, not success on it..


Thanks for your atenttion

---

### Post by VMC on 2015-05-21
Sound is much better in Windows. Something as simple as google-talk works perfectly in Windows, but xubuntu, I get distorted sound for at least the first minute or so, then it works, but nothing like Windows sound. VLC works well from start though.

---

### Post by Rob Sayer on 2015-05-22
I get brilliant sound in linux ... and I have NO use for plugins that claim to improve the sound.  While I'll admit that it's not 100% straightforward the quality is fine.

---

### Post by Yellow Pasque on 2015-05-23
Sound always works just as well for me in Linux as it does in Windows. If you want Linux equivalents of Windows programs, then be more specific...
You don't even tell us what sound device you have. [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
There are some laptops (Lenovos) that come with speakers placed in a way that they're optimized to be used with proprietary "surround" audio software, but that's just poor design IMO..

---

### Post by Vladlenin5000 on 2015-05-23
> **Rob Sayer said:**
> I get brilliant sound in linux ... and I have NO use for plugins that claim to improve the sound.  While I'll admit that it's not 100% straightforward the quality is fine.

+1

---

### Post by Godgothic182 on 2015-05-23
For using the laptop speakers the sound is ok. However, when I want to use my HI-FI system connecting the laptop and listening FLAC music files (41.1 kHz) I cannot reach the same sound as in Windows. Drivers on linux allow me to have nice quality sound and with Hear even better controlling reverberation and getting close to an amazing sound for a laptop sound card. Some would say the FLAC files don't seem to be different to mp3 sound but with nice speakers the difference can be huge.


Laptop: MSI  CX61 2OD
Card: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio
         Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller

---

### Post by Yellow Pasque on 2015-05-23
> Some would say the FLAC files don't seem to be different to mp3 sound but with nice speakers the difference can be huge.
No dispute there.

You still didn't tell us what Windows program you're using to enhance your sound. And you didn't tell us what program you're trying to use to play music (I would recommend Audacious with the mild 'Crystalizer' effect).
You didn't give the ALSA info either.

---

### Post by Godgothic182 on 2015-05-24
The windows program is called "Hear" [https://www.prosofteng.com/hear/hearfeatures/](https://www.prosofteng.com/hear/hearfeatures/) It has no version for linux, and I haven't found any similar program.

Currently I'm using VLC

---

### Post by richie60 on 2015-05-25
What you should do is use a USB DAC when you connect to the HiFi.  Also, use a music player such as Audacious, Deadbeef, Clementine etc where you can set the output to use ALSA and connect directly with the hardware therefore bypassing Pulse Audio.

You will then have excellent sound quality.

---


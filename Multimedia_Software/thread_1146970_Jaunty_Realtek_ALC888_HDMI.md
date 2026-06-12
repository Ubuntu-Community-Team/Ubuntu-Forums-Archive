---
title: "Jaunty Realtek ALC888 HDMI"
date: 2009-05-03
forum: Multimedia Software
---

### Post by jim.webguru on 2009-05-03
Hello,

I can't seem to get the hdmi device of a realtek ALC888 to show up in ubuntu 9.04. Here are the video and audio controllers:

```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```I have tried several things.Like upgrading alsa to 1.0.19 and I even tried upgrading the realtek drivers with the auidio pack of 5.11. Some of the forum topics have advice on installing build-essentials package to install realtek audio package. Unfortunately that does not exist in synapitic.

I have even tried removing pulse audio. I have also tried the scripts on some of the forumns of upgrading alsa to 1.0.19.

I have also tried upgrading alsa through some third party PPA urls.

No matter what, I can not get the hdmi device to show up. It will say analog and digital as detected. No hdmi. Is there anyone that has the same combo for vga and sound? Some forums say that xorg has to be configured in a certain way. Unfortunately the video and sound are onboard of the motherboard. So I can not install another video card. No slots and it's a Dell Studio Hybrid 140G media pc. 

Any ideas would be appreciated. Right now I'm down to nothing as far as options.I think it's funny that I thought wireless and video would be the hardest things to get working. Here it's sound that is making my life a living hell.

The following are the devices. I would love to post my alsa info file, unfortunately 19 KB is the limit. Boo.

```

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

Thank You,
Jim

---

### Post by Gil-galad0 on 2009-05-19
I've the same machine as you with mythubuntu 9.04 and I've the same problem as you. Video is ok but no audio on HDMI. With Vista is working without problem.

Did you also try with the new Intel driver? and last kernel? (2.6.30) I saw Intel fix some HDMI audio out on the last drivers..

Thanks

---

### Post by ItsManaged on 2009-07-17
There are many more mother boards with the ALC888 chipset now, has anyone had success getting HDMI sound to work since these question were asked in May?

Also can anyone tell me if multi channel formats (DTS/Dolby) are possible through HDMI? (given that sooner or later ALC888 will or is already supported.)

I'm about to get a ALC888 mobo (GA-MA770T-UD3P) to run Jaunty with mythtv since my core duo Mythbuntu baked it's bits. The configuration I am after seems to land me with ALC888 sound every time.

Cheers,

---

### Post by johan_tre on 2009-07-18
I have a similar issue for HDMI sound.
Jaunty, but with ALC1200 chipset.

Many howto's in the open, but none of them seems to work. 

till now, no sound... a bit odd of a HTPC :)

---

### Post by Gil-galad0 on 2009-11-05
I try with the new version of Ubuntu 9.10 Karmic Koala but the problem still the same. The HDMI is not listed in the aplay -l output.

So the HDMI Video work but not the the audio.

Anyone found a solution or know if a Intel release is planned?

Thanks

---

### Post by Grove on 2009-11-09
hi there,

you might wanna try reading this post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8104997#post8104997](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8104997#post8104997) and chose your model...

---

### Post by Gil-galad0 on 2009-11-19
> **Grove said:**
> hi there,

you might wanna try reading this post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8104997#post8104997](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8104997#post8104997) and chose your model...

This post is not how to get sound from the HDMI so the problem still not resolved. I think this is not an ALSA problem but really an Intel driver problem.

---

### Post by rzlist1 on 2009-12-28
> **Gil-galad0 said:**
> This post is not how to get sound from the HDMI so the problem still not resolved. I think this is not an ALSA problem but really an Intel driver problem.

I requested support from Realtek earlier this year regarding this issue since their updated Linux driver did not support the ALC888 chip. They requested additional information which I provided, No update yet.

---

### Post by Gil-galad0 on 2010-05-10
With the last version of ubuntu (10.04 Lucid) every things work perfecly! I didn't try anything, but after the upgrade from 9.10 to 10.04, I can head sound on my TV through HDMI without any future configuration. :P

---


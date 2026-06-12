---
title: "Can't configure mic properly"
date: 2010-12-29
forum: Multimedia Software
---

### Post by st4tique on 2010-12-29
I have a built in mic in my laptop and I'm trying to get it to work for the first time.
I'm using kubuntu lucid, and I'm testing the mic with audacity and skype.
I can record, but the volume is very low.

Looking at alsamixer, I identified the relevant sliders as: Digital, Internal Mic Boost and Capture.
(I also have line-in boost and mic boost but afaik they're irrelevant to my built-in mic and I have them set to 0).

I'm playing with the sliders but not getting any consistent results at all.
Internal Mic Boost just adds lots of noise to the recording, so I set it to 0 as well.
The higher I set digital, the more volume, but also the more static, and very loud thuds at the beginning and end of each recording (louder than the actual recorded voice by far).
Set the capture too high - and there's no recording at all. When Digital is set to 100, I can only up Capture till 23 - any more than that and nothing works at all.
That just seems odd to me, I thought Capture controls the actual volume of the recording.
I don't know what the other two mean.

Help will be much appreciated.

---

### Post by lidex on 2010-12-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by st4tique on 2010-12-29
[http://www.alsa-project.org/db/?f=3aace2a04a0e9c662564bca108e1a4efd5646128](http://www.alsa-project.org/db/?f=3aace2a04a0e9c662564bca108e1a4efd5646128)

---

### Post by lidex on 2010-12-29
A couple of things. I don't like your mismatched alsa components and your model switch in alsa-base.conf is probably not helping either. You probably want this:
```
options snd-hda-intel model=acer-dmic
```
So try editing that and then reboot. No joy? Follow the link in my sig to upgrade your alsa install.

---


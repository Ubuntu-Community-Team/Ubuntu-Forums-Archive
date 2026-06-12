---
title: "flash plug-in no audio"
date: 2012-10-16
forum: Multimedia Software
---

### Post by robbofolle on 2012-10-16
Hi,
I've just upgraded from Oneiric to Precise.
I have problems with the flash plugin.

If I use the package adobe-flashplugin or the package flashplugin-installer I can get the video but not the sound.

If I use the package browser-plugin-gnash I can get both video and audio, but the flash plug-in verions is old: 10.1 against the last 11.2

Has someone experienced the same problem?

Thank you.

---

### Post by Trumusiate on 2012-10-17
Hello,
I have a different issue, but I think that we could share our experiences.
I installed Ubuntu Studio (but I also tried Lubuntu with the same results) and I have the (I think, but I'm not sure) **browser-plugin-gnash** installed, and old version that can't work properly on YouTube.

When I try to install the flashplugin-installer, the about : plugins page of both Firefox and Chromium correctly shows that there is (**only**) the flashplugin but then every video shows "the plugin could not be loaded" and the crash notify appears on my panel.

I think that in both our different cases, we should remove completely the browser-plugin-gnash... I'm going to try today.

Thank you and let's keep in touch!

---

### Post by robbofolle on 2012-10-17
If I completly remove the package browser-plugin-gnash and I install the package adobe-flashplugin, I have the same problem: the audio doesn't work!!

---

### Post by Trumusiate on 2012-10-17
> **robbofolle said:**
> If I completly remove the package browser-plugin-gnash and I install the package adobe-flashplugin, I have the same problem: the audio doesn't work!!

And does the audio itself work? can you hear an mp3 for example?

---

### Post by pompel9 on 2012-10-17
Install flash-aid for firefox. I have never had any problems with that installed.

---

### Post by pqwoerituytrueiwoq on 2012-10-17
assuming your music player gives you sound this fixed it for me
```
sudo sh -c 'echo "pcm.pulse {\ntype pulse\n}\nctl.pulse {\ntype pulse\n}\npcm.!default {\ntype pulse\n}\nctl.!default {\ntype pulse\n}" >> /etc/asound.conf'
```

---

### Post by robbofolle on 2012-10-29
Hello,

I tried flash-aid with all the options, but it works only with gnash!!!

My music player gives sound, anyway I tried what pqwoerituytrueiwoq wrote, but nothing changed: gnash works but it's an old flash palyer, adobe flash palyers are able to play video, but they are not able to play sound.

P.S.: I use pulseaudio.

---

### Post by acrider on 2012-10-30
Do you happen to have more than one soundcard?  I've had this problem with two sound cards because Adobe flash only works with sound card 0 and the system default usually assigns the wrong indices for the way I have my system set up (I don't use the built-in sound on my motherboard).  The solution in that case is to modify /etc/modprobe.d/alsa-base.conf to assign the correct indices.  In my case, I've added the lines

options snd-virtuoso index=0
options snd-hda-intel index=1

just before the comment
# Prevent abnormal drivers from grabbing index 0

---

### Post by robbofolle on 2012-11-14
Thank you all, but the right solution for my case was the one posted by acrider!!!
Now it works!!

---


---
title: "No sound in MythTV"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by visionviper on 2007-04-09
I have finally gotten MythTV to work, and now I have video but no sound. I am using a PVR-150 (I think, there is no model of the card). Sound in Ubuntu works fine, but not in MythTV. I have already been browsing several forums trying to find some answers, but I havn't found anything that has worked.

---

### Post by newlinux on 2007-04-09
What is the output of mythfrontend when you try to play something? Have you tried recording something and then playing it back? What do you have your sound output device set to? Have you tried playing myth recordings outside of myth using mplayer? What have you tried? We can try to help you if you give us more information...

---

### Post by visionviper on 2007-04-09
> ave you tried recording something and then playing it back?

yes, still no sound

> What do you have your sound output device set to?

 /dev/dsp, /dev/dsp1. /dev/adsp, /dev/adsp1,  ALSA:Default

---

### Post by Titus A Duxass on 2007-04-10
Check the master volume settings in the MythTV set-up screens.

---

### Post by majoridiot on 2007-04-12
in frontend setup: setup-->general--> audio(3rd page):

audio output device: ALSA:default
mixer device: default
mixer controls: pcm (or whatever you prefer)

then adjust the master and pcm mixer volumes.

---

### Post by reets on 2007-05-01
I am having the same issue. All the settings looked correct and even turned off the internal sound control, still no sound. I tried playing a music video from the media library and that works fine (not sure if it uses the same sound system as the cable though).

Also using the Hauppauge  PVR-150, all volumes were maxed and there was really only 1 setting avail for each sound output option. Any ideas would be awesome! Thanx :D

---

### Post by quade888 on 2007-05-03
i changed audio output device to /dev/dsp1 and maxed the volume settings

that helped me

---

### Post by emil10001 on 2007-05-03
Have you tested the video stream outside of myth?

mplayer /dev/video0

Do you get sound doing that?

---


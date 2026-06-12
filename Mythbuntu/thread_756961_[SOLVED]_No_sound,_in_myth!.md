---
title: "[SOLVED] No sound, in myth!"
date: 2008-04-16
forum: Mythbuntu
---

### Post by thusgaard on 2008-04-16
Hi 

I have a problem, a minor one I hope.

In my setup I have no sound. Here are the current facts:

- I have no sound on live TV
- I have no sound on recordings
- I can not view or hear video recorded with: 
```
cat /dev/video0 > test.mpg
``` The result is big colored blocks but no sound.
- I have bad a choppy sound with:
```
sox -c 2 -t alsa hw:1,0 -t alsa default 
```
- I do have sound on youtube video's
- I have near perfect sound with: 
```
sox -c 1 -t alsa hw:1,0 -t alsa default
```
- I have sound but no video when playing online streams!

I will gladly provide any hardware information you may need (if you can tell me how to) All the things I have tested are due to this posting: [http://ubuntuforums.org/showthread.php?t=737975&highlight=sound](http://ubuntuforums.org/showthread.php?t=737975&highlight=sound)

J;-)

---

### Post by aseriesoftubes on 2008-04-16
How are you outputting sound? That is, are you using the analog audio jacks on your soundcard, or a SPDIF output?

---

### Post by thusgaard on 2008-04-16
Analog, Center speaker.

---

### Post by thusgaard on 2008-04-16
Found the solution, sort of...

As a former PC support person I ought to RTFM before asking forums.
I found this: [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-6d34b9d499edd07bd0274db073efa1eed8c1067a](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-6d34b9d499edd07bd0274db073efa1eed8c1067a)

After connecting the cabel from capture card to sound card (CD) I had sound that was out of sync. After following the above link I have sound in sync, byt it's quite bad sound. I'll open a new question if I can not figure it out.

J;-)

---


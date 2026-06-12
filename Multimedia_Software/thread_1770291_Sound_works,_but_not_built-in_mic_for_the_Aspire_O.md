---
title: "Sound works, but not built-in mic for the Aspire One 532h-2588"
date: 2011-05-29
forum: Multimedia Software
---

### Post by vangbe on 2011-05-29
I have already installed my sound card.
____________________________________________________

[B]aplay -l
[/B]

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Followed through this:

[B]sudo gedit /etc/modprobe.d/alsa-base.conf
[/B]

and added

[B]options snd-hda-intel model=auto position_fix=0
[/B]
____________________________________________________

After all of this, the built-in mic still doesn't work.
I'm using a Aspire One 532h-2588 laptop. Please I need to get this working so I can use VOIP. If anybody is curious what I'm using. I'm using ZoIper.

---

### Post by vangbe on 2011-05-29
Just incase somebody mentions it. I already tried alsamixer.

---

### Post by ChrisKu on 2011-05-30
Had a similar problem although not with a build in mic. I also thought I had all my Alsamixer settings correct. I solved the problem as follows:
1. Started Ubuntu from a LIveCD
2. Checked the mic there (it worked)
3. Opened Alsamixer an made a note of all the settings
4. Rebooted to the installed Ubuntu Environment and set all Alsamixer setting to the settings copied from the LiveCD environment
For me this solved the issue.

---

### Post by vangbe on 2011-06-02
tried it and it still doesn't work

---

### Post by lidex on 2011-06-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


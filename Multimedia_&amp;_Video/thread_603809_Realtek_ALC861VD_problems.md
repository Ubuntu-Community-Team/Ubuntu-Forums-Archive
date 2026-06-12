---
title: "Realtek ALC861VD problems"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by stuoolong on 2007-11-05
I was really chuffed with my new Lenovo 3000 N200 laptop, until I installed Gutsy on it and found that the sound doesn't work. At all.

I'm ashamed to admit that while I've been a Ubuntu user since Breezy, I've only really grasped the bare basics of how to troubleshoot things. I've spent hours and hours going through these forums, the ubuntu wiki, the Alsa bug fix pages and a couple of other pages, tried various things including recompiling alsa, and tbh failed to understand most of it and couldn't get any result. For example, I tried to follow the guide on post number four of [this thread, ](http://ubuntuforums.org/showthread.php?t=506678)by ntlam, but got to step 11 and found the file I was to be editing was in fact empty. Now I am pleading for help!

The problem seems to be similar to [the one in this thread](http://ubuntuforums.org/showthread.php?t=507310), but I can't tell if it is exactly the same, hence new thread. Basically this sound card is not supported by alsa.

Output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So linux recognises the card (and yes, it works fine in Windows and I have the speakers switched on) and also recognises the onboard modem as a sound device, is that getting in the way? I don't need it, would it help if I could turn it off somehow?

I'm pretty sure the problem relates to a module called snd-hda-intel, but tbh I don't really understand what a module is or what to do with one...
Any input appreciated :)

---

### Post by stuoolong on 2007-11-08
I solved this after reading through [this thread.](http://ubuntuforums.org/showthread.php?t=452992&page=1) by adding the line:

options snd-hda-intel model=lenovo

to the end of the file /etc/modprobe.d/alsa-base. :guitar:

---

### Post by reinz on 2008-02-23
Thanks Stuoolong! You really helped me out!

I have the same lenovo laptop and tried several tutorials and fixes without success. But your solution worked at last.

Attention, if someone is trying to get the sound work the same way, before reboot mute the mic and mic boost channels. My ears were blown away because the mic feedback. The feedback sound was loud and terrible but I smiled - the sound works :)

---

### Post by sarthorks on 2008-06-28
Please help. i have lenovo n200, and i have been having the same sound problem. I was quite hopeful that adding the line at the end of alsa-base would make my sound work, but unfortunately when i try to save the changes made to the file, the following msg. comes up:

Could not save the file /etc/modprobe.d/alsa-base.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

in the permissions tab of the properties of alsa-base, the access is read-only and i can't change it. 
Please can someone help me change the permissions settings?

---


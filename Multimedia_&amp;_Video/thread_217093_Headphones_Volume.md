---
title: "Headphones Volume"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by walding on 2006-07-16
Hi,

I have an Asus A6VM laptop.  Sound works fine, except for the headphones.  The sound mutes when I insert my headphones, but there is no sound in it.
I have edited /etc/modprobe.d/alsa-base with 
options snd-hda-intel model=auto position_fix=1
or 
options snd-hda-intel model=A6VM position_fix=1

but it still doesn't work.

I don't have a headphones slider in KMix.  It isn't an option when choosing channels.

Can anyone help, please?

Cheers,

AW

---

### Post by precinto on 2006-07-27
Try right-clicking on the sound volume control and going to Preferences. Then select Headfones and check if it is silenced or something.

---

### Post by walding on 2006-07-27
Thanks for the reply...I have tried that (not muted).
I have also lost the right channel when playing music now.  No idea what I did.  Also, gnome-volume-manager doesn't launch.
I'm beginning to think a fresh install is due, but I'm sick of that (my 3rd install since Dapper).

---


---
title: "No Sound on HP Pavilion dv6629ca"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by JosephtheGreat on 2008-03-12
Hi... I installed Kubuntu 7.10 on an HP Pavilion dv6629ca laptop. Everything has been great except the sound, which I've been trying to fix for days. I followed all the instructions in the Comprehensive Sound Guide, including installing the latest ALSA drivers, to no avail. 

My soundcard is an Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) and the codec is Realtek ID 268.  

I installed the linux-backports-modules, since someone suggested that could fix it, but it didn't work for me. My laptop has quickplay buttons at the top including a mute button that is supposed to be blue when the sound is on and orange when it's muted. So far when in Kubuntu it has stayed orange, even though KMix and Alsamixer show that the sound is on and at full volume. 

I hope someone can come up with something. I love Kubuntu, but really want the sound working!

---

### Post by 3.14frequency on 2008-03-12
> **JosephtheGreat said:**
> Hi... I installed Kubuntu 7.10 on an HP Pavilion dv6629ca laptop. Everything has been great except the sound, which I've been trying to fix for days. I followed all the instructions in the Comprehensive Sound Guide, including installing the latest ALSA drivers, to no avail. 

My soundcard is an Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) and the codec is Realtek ID 268.  

I installed the linux-backports-modules, since someone suggested that could fix it, but it didn't work for me. My laptop has quickplay buttons at the top including a mute button that is supposed to be blue when the sound is on and orange when it's muted. So far when in Kubuntu it has stayed orange, even though KMix and Alsamixer show that the sound is on and at full volume. 

I hope someone can come up with something. I love Kubuntu, but really want the sound working!

i've had the same problem since installing ubuntu 7.10. i have an acer 5920. realtek alc888
my headphone jack works but my speak s fail. my quickplay buttons stay lit even when they're not in use.

---

### Post by JosephtheGreat on 2008-03-12
It seems like a lot of people are getting this bug. It's really a shame. I hope a fix will come out soon.

---

### Post by zdarova on 2008-03-26
till now the fix is to start the laptop with battery for first time from xp or vista, after that you can use it with AC adapter. This method works with my hp dv2008ea.
I think is something with QuickPlay feature and the ACPI system. I am not an expert to fix that. try it and let me know. :popcorn:

---


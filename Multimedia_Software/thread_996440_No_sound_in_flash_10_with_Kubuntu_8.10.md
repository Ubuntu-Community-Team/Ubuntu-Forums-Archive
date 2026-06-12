---
title: "No sound in flash 10 with Kubuntu 8.10"
date: 2008-11-28
forum: Multimedia Software
---

### Post by Misocainea on 2008-11-28
I'm not getting sound in any flash applications. It works fine in Amarok.  Installing flashplugin-nonfree-extrasound doesn't help. 

Originally when opened in console I would get a message about libasound_module_pcm_oss.so being missing.  I installed libasound2-plugins, and now I get "ALSA lib pcm_oss.c:396:(_snd_pcm_oss_open) Cannot open device Live" in console in any browser (Firefox and Opera). Live is my SBLive 5.1 sound card. Anyone have any ideas on how to fix this?

---

### Post by Misocainea on 2008-11-29
bump

---

### Post by tamman2000 on 2008-11-29
Have you tried installing flash from synaptic?

I was having flash audio problems with Ubuntu 8.10 and tried that after reading this ([http://ubuntuforums.org/showthread.php?t=964165](http://ubuntuforums.org/showthread.php?t=964165)) thread...  Works now!

---

### Post by Misocainea on 2008-11-29
Thanks for the reply.  Unfortunatly installing through synaptic didn't change the issue at all for me.

EDIT: Fixed it! I ran apt-get install pulseaudio and then pulseaudio -D and I now have sound working in flash.

---

### Post by volodymyr on 2010-06-26
This solution helped me: [http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

---

### Post by FQ`9 on 2011-05-22
i had such issue on with 10.04, (i fixed it with a driver install: Realtek HD Audio)

---


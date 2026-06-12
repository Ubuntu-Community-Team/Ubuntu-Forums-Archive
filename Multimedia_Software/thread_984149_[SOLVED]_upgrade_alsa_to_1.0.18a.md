---
title: "[SOLVED] upgrade alsa to 1.0.18a?"
date: 2008-11-16
forum: Multimedia Software
---

### Post by Morkhaar on 2008-11-16
I ve had some problems making my headphones and mic to work.

I am using Hardy on a Vaio laptop. 
alsa recognises my sound card, in alsamixer I have master, PCM and digital all to max. (and changing to OSS or other options in sound preferences only limits the choices) 

I am trying to make volume control show the switches tab and external amplifier option based on several threads, but when I try to modify the /etc/modprobe.d/alsa-base there is none and gedit opens an empty file so I have nothing to modify... 

according to alsamixer I have v1.0.15. Should upgrading to 1.0.18a help anything in this case? 
I am asking because I wouldn't want to mess up anything, and according to the thread it is mainly for driver support, so I am a little confused on whether it's worth it since sound works ok

---

### Post by binbash on 2008-11-16
'
I am trying to make volume control show the switches tab and external amplifier option based on several threads, but when I try to modify the /etc/modprobe.d/alsa-base there is none and gedit opens an empty file so I have nothing to modify...
'

You can create it.That is what i did at hardy.REad all of this page : 

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by Morkhaar on 2008-11-16
finally..... thanks a lot binbash !!! problem solved!

---

### Post by binbash on 2008-11-16
You are welcome : )

---


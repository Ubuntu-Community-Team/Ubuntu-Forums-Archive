---
title: "Xubuntu 14.04 sound switch help"
date: 2014-05-14
forum: Multimedia Software
---

### Post by frank18 on 2014-05-14
Hi guys; my desktop system is A Lenovo Intel core(tm) I5 2400 CPU  3.10ghz  ,3.8Gib Mem
It has Intel integrated HD 2000 but i've got and run  an ATI AMD 6450 Video Card with fglrx video drivers

I've been using Ubuntu 14.04 but due to video flash player in Firefox  i have changed to Xubuntu14.04 and find it hard to change sound from HDMI to integrated speaker in Xubuntu, 
in Ubuntu14.04 it was easier to change the audio output but in Xubuntu 14.04 it seems to be harder to change from hdmi to built in speaker, i would rather have the 2 outputs activated at same time if that's possible,
can you please tell me an easy way to do it,thanks

---

### Post by frank18 on 2014-05-14
Update on sound situation,i was able to figure it out,

---

### Post by slickymaster on 2014-05-14
You could share with the forum the solution you found to fix it, so other people searching the forums with a similar problem know that there is a working solution for it.

---

### Post by frank18 on 2014-05-14
> **slickymaster said:**
> You could share with the forum the solution you found to fix it, so other people searching the forums with a similar problem know that there is a working solution for it.

Well i did not do anything in particular, i just could not switch back and forth between Hdmi and analog speaker, which is right there in the sound settings,i could not make hdmi and integrated speakers  work at the same time since i don't know how,but i'm ok with switching back and forth.I know that there are ways of doing both outputs to work at same times,but i can't figurer it out.  

Some people say that they can do it with these commands,well i did not try it yet,i don't want to mess up the sound,if you know that this works, let me know!

 type in terminal ```
nano ~/.asoundrc
```
then paste this code:
```
pcm.dsp {
type plug
slave.pcm "dmix"
}
```

---

### Post by slickymaster on 2014-05-14
Thanks for sharing frank18.

I edit your post, adding code tags, just for readability sake

---

### Post by Yellow Pasque on 2014-05-14
dmix is not what you want. Though this is from Archwiki, it should work for Ubuntu as well: [https://wiki.archlinux.org/index.php/PulseAudio/Examples#Simultaneous_HDMI_and_analog_output](https://wiki.archlinux.org/index.php/PulseAudio/Examples#Simultaneous_HDMI_and_analog_output)

---


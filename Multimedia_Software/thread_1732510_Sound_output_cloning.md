---
title: "Sound output cloning"
date: 2011-04-18
forum: Multimedia Software
---

### Post by Kolbason on 2011-04-18
Hello
I have the following with Maverick (10.10):
1) I use 2 monitors (hdmi-connected panel and usual lcd monitor) and 2 sound outputs (hdmi to the panel and analog to usual speakers) in my system
2) If i switch the GUI sound manager to HDMI, sound is only heard from the panel, if I choose analog - only from the speakers
3) hdmi sound introduces a buzz discussed [here.]("http://ubuntuforums.org/showthread.php?t=1544262")

The problem is
1) The solution provided in the link above doesn't do anything. I see no virtual device in ubuntu sound manager, I can't play sound through it
2) I tried to do sound cloning (to hear the sound from both the speakers and panel at the same time) in asound.conf with statement like
pcm.everywhere { 
 slave {hmdi3...} 
 slave {analog...}
}
didn't help either.
Looks like Ubuntu is overriding whatever is in asound.conf

How do I clone the output in Pulseaudio? How do I fix the resampling for HDMI buzz?

Thanks

---

### Post by Kolbason on 2011-04-18
Alright, I think I found the way around the buzz bit, (my sound card has an IEC958 output, which also goes to HDMI as it turs out), however, cloning is still wanted.
I found a tool "paprefs" that allows to create a virtual device, but that device doesn't seem to work.
Anyone ever successful with playing sound to everywhere?

---

### Post by Kolbason on 2011-04-26
So, noone ever succeeded in cloning/broadcasting the sound to many outputs?

---

### Post by lidex on 2011-04-27
Have a look here:
[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---


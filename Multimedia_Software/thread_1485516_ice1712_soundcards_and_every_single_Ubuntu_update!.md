---
title: "ice1712 soundcards and every single Ubuntu update!!!"
date: 2010-05-16
forum: Multimedia Software
---

### Post by JR_Moneybags on 2010-05-16
It's always a nightmare - upgrade Ubuntu, and spend the next 3 days trying to get your ice1712 sound card working, and it seems to have only gotten worse sine PulseAudio became the default audio manager.

I'm using Delta 1010LT on an AMD 64-bit system and upgrading to Lucid from Jaunty.

I have Envy24control installed. There is NO signal showing in Envy24control, all channels are active (not muted), sliders are all up to 0db (or there abouts), same in alsamixer.

PulseAudio Volume Controller does show that Banshee is producing a signal when I play music - but this does not transpire into audio from my speakers.

I have looked at the forums and tried a few suggestions, still to no avail.

If there's anyone out there with some knowledge on this please help me out with any next steps.

---

### Post by jmaasing on 2010-08-31
Pulseaudio gives ubuntu users nothing but grief. I do not know who to blame for that failure, pulseaudio or ubuntu but it has been trouble for years.

This might help you: [http://ubuntuforums.org/showthread.php?p=9765511](http://ubuntuforums.org/showthread.php?p=9765511)
The trick for me was the channel-mapping. Seems pulseaudio gets confused about the channels and that there is no master-volume control.

But since pulseaudio gives nothing of value I usually remove it and stick to plain Alsa.

---


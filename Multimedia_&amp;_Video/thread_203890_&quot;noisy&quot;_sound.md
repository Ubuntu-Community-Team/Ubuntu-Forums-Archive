---
title: "&quot;noisy&quot; sound"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by vladu on 2006-06-26
i am experiencing a very poor quality sound. it's noisy as if i turned the volume up beyond the speakers' capacity.

i am running a fresh ubuntu 6.06 install with all the packages from the default repositories upgraded.
i have an onboard sound card - typing "cat /proc/asound/cards" produces:
0 [CK8            ]: NFORCE - NVidia CK8
                     NVidia CK8 with ALC655 at 0xe6101000, irq 193

if there's need for additional information, please also tell me how to get it. i'm new with linux. thanq you

---

### Post by woedend on 2006-06-26
if you run alsamixer, and turn pcm down and master volume up, does it get any better?

---

### Post by vladu on 2006-06-26
Yes, it seems that the PCM slider is the noise source. But here's another problem: when i move de PCM slider down to its minimum, the sound volume gets extremely low - at least when i'm playing mp3's in xmms or Rhythmbox. So it's practically impossible to cut out all the noise using this method.

in xmms, the volume slider is linked to the PCM slider in Alsa mixer. it says somewhere in help that the PCM slider controlls wave files.

nevertheless, turning the PCM down means a huge improvement. thanks for the advice woedend. if anyone knows a better workaround, i'm open to suggestions. it's not that i can't live with it, but in windows music sounds better at the same volume.

---

### Post by Jolly Roger on 2006-07-11
To change what mixer the volume slider in xmms will change do this:

Go to Options->Preferences and select the Configure button under Output Plugin. A box comes up and in it you should select the Mixer Device box and choose the Master volume setting. 

Now the volume slider in xmms changes your master volume setting instead of PCM. But PCM will still lower the volume of mp3s in xmms. Hopefully someone else will be able to help with another solution. :-k

---


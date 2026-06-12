---
title: "No Sound Input"
date: 2010-12-21
forum: Multimedia Software
---

### Post by Hondros on 2010-12-21
I first noticed this problem when trying to record in audacity. I brought it up, hit record, and started playing guitar [My amp is plugged directly into the microphone jack on the front]. Nothing was recorded. So I figured something was wrong with the cord, grabbed the mic, and mic'ed my amp. Still, no sound. So I was a bit confused. Unplugged the mic, and tried to use the internal mic to record my voice. Still no sound.
So I clicked on the volume icon, went to sound preferences. Found out that under "hardware", this is listed:
```

Internal Audio
1 Output 
Analog Stereo Output

```
Now, this is strange, because I used to have 2 inputs, and 2 outputs. 
The only thing that I have newly installed was the pulseaudio-equalizer. So, I un-installed that with hopes of fixing it. 
It didn't. Next, I re-installed the alsa sound package like in the stickied thread, nothing changed.
Can anyone help?

---

### Post by Hondros on 2010-12-30
*bump*
Can anyone help with this?

---

### Post by Hondros on 2010-12-30
Fixed it, found out somethign was wrong with my preferences. So, I did a rm -rf of ~/.pulse, then copied .pulse from another user of mine. So it's working now.

---


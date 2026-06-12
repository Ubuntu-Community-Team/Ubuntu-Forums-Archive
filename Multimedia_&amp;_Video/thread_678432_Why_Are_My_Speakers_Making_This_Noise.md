---
title: "Why Are My Speakers Making This Noise?"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by adn258 on 2008-01-25
Okay so like when I turn my volume up to the highest I hear a slight so to speak noise it's real low but it's like something is running it makes a sssshhhhh noise so to speak like if you were to take your radio in your car and tune it so it wasn't on a station at all that's the kind of noise it makes.  Is this okay for it to make that on it's highest volume?

---

### Post by yabbadabbadont on 2008-01-25
Yes.

---

### Post by arsenic23 on 2008-01-25
Try turning down your PCM volume either with the volume control, or by typing 'alsamixer' into your terminal.

---

### Post by tgalati4 on 2008-01-25
That's normal noise for cheaper or on-board sound cards.  To get quieter performance or louder volumes, you need to go to a semi-pro card such as M-Audio.  As a rule of thumb, keep your levels at 75% and avoid 100% because that will surely get you noise.

---

### Post by yabbadabbadont on 2008-01-25
> **tgalati4 said:**
> and avoid 100% because that will surely get you noise.

And possibly evicted...  :lol:

---

### Post by Goombie on 2008-01-25
I'm having a similar problem to this, only it is with a pair of headphones I bought today. The headphones work fine in my stereo, so I don't think it's them. Turning down my PCM doesn't help, though. Any other suggestions?

---

### Post by tgalati4 on 2008-01-30
What is the impedance of the headphones?  Are they 16 Ohm, 25 Ohm, 32 Ohm?  Try measuring with a meter.  If you have lower impedance headphones (16 Ohm) then they can put a higher load on the output circuitry on the sound chip.  This could result in noise.

The other possibility, these headphones have better high-frequency response, so you detect the noise, but the stereo has a filter so you can't hear it.

Most computer sound cards are fine for system beeps and game effects, but they are not high-fidelity.

---

### Post by linuxferret on 2008-01-30
i had the same issue; a lot of hissing and squeaking through the headphones (i too have an onboard soundcard).  i have managed to fix this completely now, and the sound - through the headphones at least - is just as good as I get in Vista.

For me it was a simple fix in GNOME Alsa Mixer, but i don't anticipate it will be this easy for  everyone.

Simply open Alsa Mixer and ensure the 'headphones' check box is 'on'; adjust the volume through your headphones to the desired level using 'surround', and theN mute anything that relates to 'microphone' - front mic, mic, mic boost etc.  this solved the problem for me.

---

### Post by dasunst3r on 2008-01-30
If you have an on-board sound card, this is because there is not enough shielding to protect the D/A converter from the noise originating from other components.

---

### Post by adn258 on 2008-01-30
> **dasunst3r said:**
> If you have an on-board sound card, this is because there is not enough shielding to protect the D/A converter from the noise originating from other components.

Is this a bad thing will it mess anything up?

---

### Post by linuxferret on 2008-01-30
> **adn258 said:**
> Is this a bad thing will it mess anything up?

well i´ve not noticed any deterioration in sound quality in my switch from vista.  i did encounter the hissing sound you described (through headphones), but that was easily remedied as described above.

---


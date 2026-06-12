---
title: "Problems with JACK and Audacity (on Ubuntustudio)"
date: 2007-05-21
forum: Multimedia Production
---

### Post by Janusz11 on 2007-05-21
Hello!

I use the onboard sound of my nForce 2 motherboard and the ALSA driver (intel8x0). Now, when I change the input and output device within JACK settings to anything other but default, JACK often complains and fails to start. 

Audacity also complains about a wrong audio device or sample rate ("Error opening sound device. Please check the input device settings and the Project Sample Rate") when I change the input/output device within JACK. But I receive the same error message when I don't run JACK and set the audio device in Audacity's settings. 

The problem is that I use the optical S/PDIF for audio output and I can't hear anything when I play or record stuff in Audacity. Sound in general (system sounds, XMMS) work, btw..

Once again, any help appreciated and thanks in advance.

---

### Post by kayosiii on 2007-05-24
I used to have a similar mainboard and the best advice i can give is to get a soundcard for it. The intel 0x80 does not support hardware mixing. which means that when Jack runs on the soundcard it takes over completely.

There are some parts of Alsa that work around this but I was never able to get them to work (you could look into those I think one was called dmix).

Other than that hopefully there will be a version of Audacity with jack support soon enough.

---


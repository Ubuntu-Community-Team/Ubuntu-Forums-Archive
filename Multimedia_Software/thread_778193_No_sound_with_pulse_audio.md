---
title: "No sound with pulse audio"
date: 2008-05-01
forum: Multimedia Software
---

### Post by bouchmil on 2008-05-01
I got the sound working for every application except the ones that work with gstreamer (Rythmbox and Totem) even if I have the package gstreamer0.10-pulseaudio. I'm on hardy 64. I can get the sound working properly with the alsa drivers. I have selected pulse audio in the gstreamer-proprieties. I dont know where is the problem...

---

### Post by Zorael on 2008-05-02
If you have ALSA set up to use pulse as its default device, you should get Pulse to manage the sound anyway. Basically you want to set ALSA to use pulse as its default output device, alternatively set your individual media apps to.

What does your /etc/asound.conf look like?
```
zorael@sunspire:/etc$ cat asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by presston on 2008-05-02
did you added yourself to pulse group?

---

### Post by bouchmil on 2008-05-02
> **Zorael said:**
> 
What does your /etc/asound.conf look like?
```
zorael@sunspire:/etc$ cat asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

My asound.conf is the same. And i'm added to the pulse group. In fact, i have followed many guides about the pefect pulse setup, but none of them make it work. I dont know why i have sound for all games but not for gstreamer apps... At least, i can still listen to the marvelous frozenbubble theme song...

---

### Post by Zorael on 2008-05-02
I curse my failing memory for not being able to remember precisely what I did to get mine working. At present, if I start something with ALSA output, it properly shows up in the pulseaudio volume control.

I doggedly followed the guides and hints over at [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup), as well as random google results, most of which were posts here on these forums.

---

### Post by bouchmil on 2008-05-02
I've found the problem!! In pulse audio device chooser, in the section volume control, i changed the default output device from ALSA PCM in front:1 (VIA 8237) to ALSA PCM on front:0 (ADC Capture/Standard PCM Playback)... I don't know what it means, but now i got sound comming out from my front  speaker. I just need to set up my 6 other speakers...

It's weird because in System/Prefrences/Sound my defaut mixer track was my Creative audigy and not the VIA 8237 wich is the module for my motherboard sound card... Well thank you all for your help!

---


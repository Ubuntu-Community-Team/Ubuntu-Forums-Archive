---
title: "Pass through digital input to speakers"
date: 2008-11-26
forum: Multimedia Software
---

### Post by rudie on 2008-11-26
I have an AC'97 sound card (82801DB/DBL/DBM ICH4/ICH4-L/ICH4-M), with speakers connected to the analogue output. The card has a digital ( IEC958 ) input connected to my TV, and I would like to pass this source through to my speakers. I have tried to enable various things through alsamixer, and although I can record from this source, I haven't found a way to make it 'mix' with my main sound output.  I have done something like this on another computer before with just alsamixer, but that was with line-in instead of digital in and with a Soundblaster card, so the mixer looked different.

Doing something like 'arecord -t wav -f cd | aplay' kind of works, but there is too much latency and also it doesn't feel like the correct solution.

Does anyone know how to do this properly? Any help would be appreciated.

---

### Post by markbuntu on 2008-11-26
Is there an IEC958 Capture or IEC958 In Monitor or IEC958 In Select switch in your sound mixer?
These switches will probably not be seen in the panel volume control unless you have them selected in the preferences. You may have to fool around with them a little to get it working.

---

### Post by rudie on 2008-11-28
> **markbuntu said:**
> Is there an IEC958 Capture or IEC958 In Monitor or IEC958 In Select switch in your sound mixer?
These switches will probably not be seen in the panel volume control unless you have them selected in the preferences. You may have to fool around with them a little to get it working.

I have the following in alsamixer (which in fact also reveals that it is a Realtek ALC650E, in case that's relevant):
Playback
IEC958 Playback AC97-SPSA (with four settings, set to zero)
IEC958 (switch on/off, set on)
Capture
IEC958 (switch capture/off, set to capture)
IEC958 Playback AC97-SPSA (with four settings, set to zero)

I think the Playback setting should be set to zero to do the right thing, based on some googling (e.g. [http://alsa.opensrc.org/index.php/Realtek_ALC650](http://alsa.opensrc.org/index.php/Realtek_ALC650)).

---

### Post by rudie on 2008-12-01
bump

---

### Post by markbuntu on 2008-12-01
All you can do is try them and see which ones work for you. Be sure to take notes so you can remember what you tried.

---

### Post by rudie on 2008-12-02
> **markbuntu said:**
> All you can do is try them and see which ones work for you. Be sure to take notes so you can remember what you tried.

Thanks but I have tried all combinations I can think of. I suppose I'll have to continue my googling. Could someone at least let me know what this concept is called (i.e. automatically pass through sound from an input to an output)? And is this something that all cards should be able to do?

---

### Post by markbuntu on 2008-12-02
For some cards, the digital input is output as a pcm stream. Since you can record the stream that seems to be working. If you are using pulseaudio you should be able to use one of the monitor streams to get it to your speakers.

---


---
title: "Skype Crashes during calls"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Klemts on 2008-11-04
Skype Version 2.0.0.72 generally crashes a few minutes into a call. 
This problem started under 8.04, and continues post-upgrade. 

Here is a print out of the terminal after the crash:
```
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
Floating point exception
```

The skype forums aren't helpful; as far as I can tell.
Thanks folks,
-Chris.

---

### Post by titoshauri on 2010-05-31
I had similar problem before, what i did is to install PulseAudio  restart machine and here sound and video working.  but later skype stop making call i try to make a test call  i get Call failed. :confused:

---


---
title: "usb headset getting audio as speaker 1 from exaile only"
date: 2009-02-22
forum: Multimedia Software
---

### Post by swiftor on 2009-02-22
i have been working on getting my usb headset to play audio. its an AZ7 headset from ABS tec. the only app that i get audio from is Exaile music player. no system sounds, nor sounds from anything on firefox. using my old headset with a 3.5 mm jack i get all audio 

when i open the volume control my device is "usb advanced audio device (alsa mixer) when i mute speaker 1, audio stops from exaile. muting or turning the volume down on the speaker one slider dosnt do anything

all the audio devices in prefrences -> sound say cmedia usb advanced audio decvice (oss) and when i test them i hear the tone. when i set it to cmedia usb advanced audio device (alsa) and try to test it i get this error "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application." even with exaile and firefox closed. 

i can see it in my aplay -l and after that i am lost @.@ i have tried to folow the sticky but i dont think it pertains to me because i get some audio, just not all. i think i need to switch speaker 1 to just speaker, but i dont know how to do that. 

any ideas?

---


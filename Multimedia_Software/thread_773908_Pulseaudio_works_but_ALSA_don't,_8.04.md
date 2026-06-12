---
title: "Pulseaudio works but ALSA don't, 8.04"
date: 2008-04-29
forum: Multimedia Software
---

### Post by Roig on 2008-04-29
(Sorry for my poor english)

Hello.

First of all, i am very disappointed about this pulseaudio thing. It messed up all my system, my wine apps, my games, some of my favourite apps like VLC, Skype.. etc. Yeah, i don't know why ubuntu 8.04 have pulseaudio, it's a regresion not a progress in any way. Of course i think that when pulseaudio will be stable and compatible 100% with apps it will be very good but now?! NO, THANKS.

Now.. the problem (Yesterday i updated 7.10 -> 8.04), Sound Worked in 7.10 and i can open multiple instances of VLC for example and the sound of all worked very well, wine apps sounds worked, skype too but now in 8.04 -> ...

---- Switch in my System->Preferences->Sound to ALSA and i click the TEST button it pops this error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.
```


---- in Skype:

```
dani@dani-habitacio:~$ skype
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:813:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dsnoop.c:504:(snd_pcm_dsnoop_open) The dsnoop plugin supports only capture stream

```

---- in Wine (when i switch the sound tab it pops this in console)

```
dani@dani-habitacio:~$ wine winecfg
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_dsnoop.c:565:(snd_pcm_dsnoop_open) unable to open slave

```


---- Openttd (transport Tycoon) a game hat worked fine with sound in 7.10. Now it boots but without music/sound

```
dani@dani-habitacio:~$ openttd
ALSA lib pcm_hw.c:1272:(_snd_pcm_hw_open) Unknown field mmap_emulation
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```

Someone can give me a solution? Why ALSA can't open the audio device? If you need more info about my system, i will give you of course.

Thanks!
And again sorry for my english :P.

---

### Post by Roig on 2008-04-29
Okay, i surrender. 

Please, how i can uninstall this shitty pulseaudio and only go with ALSA like 7.10? 

Using Synaptic? or i will have to do something more?

Thank you.

---


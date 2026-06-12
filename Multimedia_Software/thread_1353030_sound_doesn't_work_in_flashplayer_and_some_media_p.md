---
title: "sound doesn't work in flashplayer and some media players"
date: 2009-12-12
forum: Multimedia Software
---

### Post by neuplnost on 2009-12-12
Hello world:),
i am new to this forum but not to ubuntu (continually since breeze badger). Now I have to ask on forums for first time...

My current OS is kubuntu 9.10. Problem is sound. In flashplayer and some media players (vlc, kmplayer) doesn't work. In other media players (dragon, amarok) and in system sound works well. In multimedia settings i see 3 devices:

NVIDIA CK804
1. alsa: x-phonom:CARD=1,DEV=0
2. alsa: plughw:CARD=1,DEV=0
3. oss: /dev/dsp1
4. oss: /dev/audio1)

PULSEAUDIO
xine

HDA ATI HDMI
1. alsa: hdmi:CARD=HDMI


Primary output is nvidia. When i use "sudo killall pulseaudio", it tells me that no process found. When i use "sudo alsa force-reload", it tells me this:

Unloading ALSA sound driver modules: snd-hda-codec-atihdmi snd-intel8x0 snd-ac97-codec snd-seq-dummy snd-seq-oss snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-atihdmi snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-atihdmi snd-intel8x0 snd-ac97-codec snd-seq-dummy snd-seq-oss snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

After this sound either begin to work everywhere, or nothing change except that KDE gives me this:

KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Capture: NVidia CK804 with ALC655 (NVidia CK804)
Output: HDA ATI HDMI, ATI HDMI (HDMI Audio Output)
Output: NVidia CK804 with ALC655 (NVidia CK804)


After system restart it won't work again anyway.

I think it might be something with that hdmi output. I wanted to remove that device, but couldn't find out how.

If somedoby has an idea what to do, please advise:?:.

Thanks.

---

### Post by adamsojc on 2010-01-03
Sorry if this is late but try opening your mixer and adjusting the PCM volume all the way up.

Do that by right clicking the speaker icon is system tray and show mixer.  Then configure it to show the PCM channel if it is not already showing.  Move the slider all the way up.

Hope that helps.

---


---
title: "[SOLVED] PulseAudio 2-bit sound problem"
date: 2008-12-06
forum: Multimedia Software
---

### Post by sj01 on 2008-12-06
When I upgraded from Ubuntu Hardy to Intrepid (was Alpha 5), PulseAudio ceased to function properly, and the only audible sound while using PulseAudio became a seemingly random clicking noise. To use sound, I have change my sound settings to use OSS instead of PulseAudio (because Alsa was configured to run through PulseAudio). I also have to run `pulseaudio -k` on each startup. Playing an audio file through mplayer in the terminal provides the only useful output towards identifying the problem:

```
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (**[COLOR="Red"]2 bytes[/COLOR]** per sample)
```

The same problem exists through all programs, such as 'audacity', 'rhythmbox', and the Firefox flash 10 plug in. Does anybody know how I would reconfigure ALSA and/or PulseAudio to provide full sound once more? I had filed a bug on Launchpad, but it was dismissed as informational, so I hope somebody here can help me.

---

### Post by 2hot6ft2 on 2008-12-06
Start here for more info [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and it will lead you here for how to deal with it [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

UUE 2.0 is 8.10 on steroids and TheeMahn is just that.

---

### Post by sj01 on 2008-12-07
Is there any way to fix PulseAudio without disabling it? In previous versions of Ubuntu, I had found PulseAudio to be much more reliable than ALSA (surprisingly), as it worked correctly with apps that can only use OSS rather than ALSA, as well as ALSA programs themselves. Running OSS through ALSA caused plenty of problems, especially with audio capture.

---

### Post by sj01 on 2008-12-15
My problem still exists, and I would still like to use PulseAudio or ALSA. Disabling PulseAudio through the steps mentioned previously simply results in ALSA providing the same clicking sounds instead of audio. Is there any way to revert the audio configuration to that of the 8.10 LiveCD? Audio works perfectly on the LiveCD with both PA and ALSA.

I have tried to look for configuration files on the LiveCD, but there does not seem to be any at all. I tried to replicate that on my system, and by deleting the configuration files for both ALSA and Pulse solves no problems, but causes no others. Is there a GConf setting that I'm missing?

Edit: Wow, I feel stupid. Something just muted the PCM audio track. I didn't figure this out sooner because I didn't have the regular volume control program running, only the PulseAudio one.

---


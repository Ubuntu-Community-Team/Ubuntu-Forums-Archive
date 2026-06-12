---
title: "No sound from computer"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by newlinux on 2006-12-06
Hello,

I just have done a fresh install of edgy, enabled codecs and a few other things as I prepare to turn this machine into a mythbox. However I get no sound. Here are the errors I get with VLC and mplayer:
```
:~$ vlc sample.mp3 
VLC media player 0.8.6 Janus
[00000288] oss audio output error: cannot open audio device (/dev/dsp)
[00000288] main audio output error: couldn't find a filter for the conversion
[00000288] main audio output error: couldn't create audio output pipeline

```
 and from mplayer:

```
alsa-init: using device default
alsa-lib: pcm_hw.c:1246:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: No such file or directory
alsa-init: playback open error: No such file or directory
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Invalid argument
alsa-init: using device default
alsa-lib: pcm_hw.c:1246:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: No such file or directory
alsa-init: playback open error: No such file or directory
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
[AO ESD] esd_open_sound failed: Connection reset by peer
ao_nas: init(): Can't open nas audio server -> nosound
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
alsa-lib: pcm_hw.c:1246:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: No such file or directory
[AO SDL] Unable to open audio: No available audio device
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```

But play after the errors, but with no sound, as apparently they can't open my sound device. I have an ASUS a8ne mobo, and I'm using the integrated sound. Any help is appreciated!

BTW, /dev/dsp exists
```
:/dev$ ls -l d*
crw-rw---- 1 root audio 14, 25 2006-12-06 08:53 dmmidi1
crw-rw---- 1 root audio 14,  3 2006-12-06 08:53 dsp
crw-rw---- 1 root audio 14, 35 2006-12-06 08:53 dsp2
crw-rw---- 1 root audio 14, 51 2006-12-06 08:53 dsp3

```

Maybe I have something hooked up wrong in the motherboard? Didn't think I really needed to do anything with onboard sound...

---

### Post by newlinux on 2006-12-06
I should note that I am using the line out and I know the speakers I have plugged into them work, and nothing is muted that I know of.

---

### Post by firfin on 2006-12-06
Hi there,

I don't know maybe you already tried this, but have you seen:
[comprehensive guide]("http://ubuntuforums.org/showthread.php?t=205449")

in it is a bit about the rights to /dev/dsp maybe that solves your problem?

Also where do you get the error messages from? I dont get any at all and everything seems fine (all players work) but i can't get any sound to coem from my soundcard either.
see my [post]("http://ubuntuforums.org/showthread.php?t=313184") for things i tried so far

Good luck

---

### Post by newlinux on 2006-12-09
I checked my audio group in /etc/groups and I am in there, so that seems okay. I used to get the errors whenever using VLC or mplayer. I have two tv capture cards and they have sound out, so i thought maybe they were causing a problem (I have a /dev/dsp2 and /dev/dsp3) so I went into System->Preferences-Sound and changed my default sound card and I no longer get the errors, but still no sound. I tried the comprehensive guide, but still no luck. maybe I'll try reinstalling as you did...

---

### Post by newlinux on 2006-12-10
Reinstalling didn't help (and set back a bunch of configs I had already done, but sound is kind of important for an HTPC :). I know that it is recognizing my onboard sound and that it is enabled in the BIOS. I can't see anything that is muted from the volume control panel. I'm out of ideas at this point and any help is appreciated... HELP!!

---

### Post by newlinux on 2006-12-12
okay - I went through a lot of headaches for nothing. It turned out to be a hardware problem -- I bought my mobo used and the previous owner used a front panel audio connector, and I don't. However, when a front panel audio connector is not in use two jumper caps have to be put back on some of the audio pins on the mobo for sound to work... The manual doesn't even say this - it was just a guess from looking at the pictures of the mobo in the manual - so this is resoved for me - thanks for the help.

Off to turning this into a mythbox!!!!!

---


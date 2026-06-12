---
title: "Unable to make pulseaudio to manage digital surround output"
date: 2010-05-12
forum: Multimedia Software
---

### Post by mteira on 2010-05-12
Hello.
pulseaudio doesn't  provide a digital (iec958) surround profile in my system (nVidia MCP73 HDA ALC889A), only stereo profiles on the digital output are available (surround profiles are available for the analog output though).

Running pulseaudio with debug, leads to the fact that a pcm a52 device is expected for those profiles to work:

```

D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory

```So, I took a look to /usr/share/doc/libasound2-plugins/a52.txt and /usr/share/doc/libasound2-plugins/examples/a52.conf_pulse and followed those examples to get to the point where alsa is complaining about a missing plugin:

```

rudiger@colossus:~$ LANG=C aplay -D a52:0 Norrlanda.wav 
ALSA lib pcm.c:2171:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_a52.so
aplay: main:608: audio open error: No such file or directory

```This led me to recompile the libasound2-plugin package, after installing all the build dependencias and libavcodec-dev to provide the a52 support

After this, I purged my user .pulse and restarted pulseaudio. Now, it's able to detect the digital surround outputs. Unfortunately, trying to use it, leads to a segmentation fault in pulseaudio.

So, I stopped further investigations, suspecting that perhaps I'm not following the right path to achieve digital surround sound in Ubuntu 10.04. I've also read some threads about lack of a52 support in Ubuntu due to patent issues, but most of them are one year (and more) old.

So, please, If you were so kind to direct me to some guide or resource to be able to fix this issue, or to share some knowledge about it, i will be very pleased.

BTW, I'm able to get surround audio just executing:
aplay -D iec958 Norrlanda.wav

The home cinema box is receiving the 6 channels in that wav file.

Regards.

---


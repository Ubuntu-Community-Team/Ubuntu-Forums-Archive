---
title: "Using alsa a52 encoder  causes all pcms to produce no sound"
date: 2008-07-03
forum: Multimedia Software
---

### Post by velk on 2008-07-03
Basically, I have my ubuntu 8.04 box hooked up to a surround receiver over coaxial digital. Normal sound works, and AC3 passthrough works from mplayer, using ao alsa:device=hw0 

I'd like to use a52 encode to encode the sound output of other programs into DD5.1, however when I run speaker-test through the a52 encode pcm it not only produces no sound, it also prevents all the other pcms from producing sound until I issue an 'alsactl restore' command.

E.g.
  'speaker-test -c2'
Will produce the expected per channel white noise. If I then try
  'speaker-test -Da52encode -c6'
It will appear to run normally and produce no errors, but there will be no sound output. Also after trying this if I
  'speaker-test -c2'
again, then it will also produce no sound, neither will 'speaker-test -Dfront -c2' and 'speaker-test -Dhw:0 -c2' until I issue 'alsactl restore', at which point they will start working again.

I've done a couple of hours of searching and fiddling without much success, there doesn't seem to be a lot of info on troubleshooting a52encode, I can't even find any errors or error output - was hoping someone here had some suggestions

----------

/etc/asound.conf is configured as :

pcm.!default {
  type hw
  card 0
}

pcm.a52encode {
  type a52
}
--------

aplay -l :
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-----------

aplay -L:
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

-------

ls -la /usr/lib/alsa-lib/libasound_module_pcm_a52*
-rw-r--r-- 1 root root   964 2008-07-03 00:22 /usr/lib/alsa-lib/libasound_module_pcm_a52.la
-rwxr-xr-x 1 root root 50629 2008-07-03 00:22 /usr/lib/alsa-lib/libasound_module_pcm_a52.so

These two files are manually compiled from the alsa-plugins_1.0.15 package source.

---

### Post by cioccolato on 2008-08-09
I have exacltly the same configuration... and I can only make work 2 channels + 2 rear (copied).

---

### Post by theophile on 2009-01-24
I'm also trying to get a52encode to work. I am not using pulse audio. I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=714712](http://ubuntuforums.org/showthread.php?t=714712)

To build and install the alsa libs. However, when I do

mplayer foo.avi -ao alsa:device=a52encode

I get this error:
```
[AO_ALSA] alsa-lib: pcm_a52.c:683:(_snd_pcm_a52_open) Cannot find codec engine
[AO_ALSA] Playback open error: Invalid argument
Failed to initialize audio driver 'alsa:device=a52encode'
Could not open/initialize audio device -> no sound.
Audio: no sound
```

Here is my asound.conf

```
pcm.a52encode {
	type a52
}


pcm.!spdif {
             type hw
             card 0
             device 1
}

pcm.!default {
            type plug
            slave {
                  pcm "spdif"
            }
}
```

Can anyone help?

---

### Post by danwood76 on 2009-02-04
I think you may have a couple of issues.

For one I dont think you have installed the a52 encoder properly, you might want to double check what you did.

Secondly your asound.conf is wrong, you need to setup the encoder aswell as initialising it. Also I think your default is also wrong.
Your asound.conf should look like this:
```

pcm.!default {
	type plug:surroundaudio
}

ctl.!default {
	type plug:surroundaudio
}

pcm.a52encode {
	type a52
	format S16_LE
	channels 6
	rate 48000
	bitrate 448
}

pcm.surroundaudio a52encode

ctl.surroundaudio {
	type hw
	card 0
}

```

I would try editing your asound.conf first then restarting alsa.
Then use ```
speaker-test -Dsurroundaudio -c 6
```
to test the output.

regards,
Danny

---


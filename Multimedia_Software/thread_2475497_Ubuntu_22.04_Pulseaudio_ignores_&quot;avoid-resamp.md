---
title: "Ubuntu 22.04 Pulseaudio ignores &quot;avoid-resampling&quot;"
date: 2022-05-29
forum: Multimedia Software
---

### Post by Leechpool on 2022-05-29
Hi Everyone,
I use "avoid-resampling=yes" in /etc/pulse/daemon.conf to cause the system to leave the sample rate of streams unchanged when they are playing on hardware that can support the stream rate. With this setting in 18.04 and 20.04, I can play sample audio at say 96kHz and system plays the stream to my usb DAC (Cambridge Audio CXA81) at 96kHz, so there is no resampling. The trouble I have is that in 22.04, whatever I do the sample rate seems to stay at 44100Hz (unless I set the "default-sample-rate" in daemon.conf to say 192kHz, in which case everything then stays locked at that sample rate).

I've done a lot of experimenting with 20.04 and 22.04 live disc to try to identify the differences.

With 20.04 live disc, leaving all settings at default, 44100Hz will play at 44100Hz, and 48000Hz will play at 48000Hz, as you would expect as these are the default and alternative samples rates. When I say "play at", I look at the sample rate setting in "pacmd list-sinks" and "cat /proc/asound/card1/pcm0p/sub0/hw_params", and I check the source sample rate using "pacmd list-sink-inputs". Like this, if I try to play say 96kHz it will get resampled to 44100 or 48000Hz, again this is as you would expect because the default is "avoid-resampling = no".  Now if I change "avoid-resampling = true" and restart pulse, 44100 and 48000Hz sources behave as before, but 96kHz sources will play at 96kHz etc. GREAT... this is what I want for HD audio.

Trouble is with 22.04, again using a live disc, whatever I do it plays all sample rates at 44100Hz.

Ultimately, I will use "resample-method = soxr-vhq" and "default-sample-format = float32le" in daemon.conf as recommended in many places, but I can't get the resampling to be avoided in 22.04.

Can anyone shed any light on this please. I'm stuck....

:P

---

### Post by #&amp;thj^% on 2022-05-29
> **Leechpool said:**
>  but I can't get the resampling to be avoided in 22.04.

Can anyone shed any light on this please. I'm stuck....

:P
Things have changed:
```
inxi -A
Audio:
  Device-1: Intel 82801I HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.17.0-1003-oem running: yes
  Sound Server-2: PipeWire v: 0.3.48 running: yes

```
Notice No pulse-audio.
PipeWire uses its own resampling algorithm called Spa. Like with SoX's sox, Speex's speexenc, PipeWire includes its standalone version: spa-resample. Usage:
```
 spa-resample -q 15 -f s24 -r 48000 input16bit44100orAnythingElse.wav output24bit48000hz.wav
```
More found here: [https://gitlab.freedesktop.org/pipewire/pipewire/-/tree/master/spa/plugins/audioconvert](https://gitlab.freedesktop.org/pipewire/pipewire/-/tree/master/spa/plugins/audioconvert)

---

### Post by Leechpool on 2022-05-29
Wow, thanks 1fallen, no wonder I was getting nowhere; there was a whole dimension I was missing.

I need to go way and try to figure out how to set up PipeWire for HD audio :)

---

### Post by #&amp;thj^% on 2022-05-29
Another fun look is:
```
**wpctl status**
PipeWire 'pipewire-0' [0.3.51, me@arch-me, cookie<snip>]
 &#9492;&#9472; Clients:
        32. xfce4-pulseaudio-plugin             [0.3.51, me@arch-me, pid:917]
        33. pipewire-pulse                      [0.3.51, me@arch-me, pid:949]
        34. WirePlumber                         [0.3.51, me@arch-me, pid:947]
        35. WirePlumber [export]                [0.3.51, me@arch-me, pid:947]
        63. xdg-desktop-portal                  [0.3.51, me@arch-me, pid:55163]
        64. Firefox                             [0.3.51, me@arch-me, pid:2]
        65. virt-manager                        [0.3.51, me@arch-me, pid:149364]
        66. virt-manager                        [0.3.51, me@arch-me, pid:149364]
        67. wpctl                               [0.3.51, me@arch-me, pid:955355]

Audio
 &#9500;&#9472; Devices:
 &#9474;      45. UOEOS Laptop Dock                   [alsa]
 &#9474;      48. HDA NVidia                          [alsa]
 &#9474;      61. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      41. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *   56. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      46. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *   55. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      43. Integrated Camera                   [v4l2]
 &#9474;      49. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   59. Integrated Camera                  
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.pci-0000_04_00.6.analog-stereo
         1. Audio/Source  alsa_input.pci-0000_04_00.6.analog-stereo

```

---


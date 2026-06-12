---
title: "No sound in Karmic"
date: 2010-07-08
forum: Multimedia Software
---

### Post by session13 on 2010-07-08
Hello,

Although I'm using Linux from almost a year, I still doesn't have the knowledge to solve my problem. 

From time to time, system booted with no sound and I had to restart system to have it on again. Now I have no sound all the time and no idea where lies the problem. I would like to ask for help in making a diagnose of what could be the cause that there is no sound in my system.

Here is some data that I could gather:

Alsa mixer configuration:
Master, PCM, Front: 100%
Other option: 0%

There is no error message while booting system. No explicit sound driver. Sound isn't muted. Sound works when using Ubuntu Live.

Sound card: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)

Any help would be appreciated.

---

### Post by venturax on 2010-07-08
> **session13 said:**
> 
Any help would be appreciated.

Take a look here: [http://ubuntuforums.org/showthread.php?t=1323348](http://ubuntuforums.org/showthread.php?t=1323348)
I had lots of problems and many kind people replied. There are links to subthreads, which could help also.

---

### Post by lidex on 2010-07-08
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by session13 on 2010-07-09
@venturax, thanks for you advise. I made some research and below is what I did to make my sound back.

$amixer
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 53 [83%] [-11.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [on]
  Front Right: Playback 0 [0%] [-64.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-64.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-13.50dB] [on]
  Front Right: Capture 0 [0%] [-13.50dB] [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

```$cat /proc/asound/cards
```
 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
HDA VIA VT82xx at 0xfebfc000 irq 17
```$cat /proc/asound/devices
```
2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
```I did this without success:

```
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
```Last command output *(alsa force-reload)*:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zero3/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zero3/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
```Next changed: ```
/etc/modprobe.d/alsa-base-conf
```by commenting out:
```
# options snd-hda-intel power_save=10 power_save_controller=N
```and adding:
```
options snd-hda-intel model=auto
```Finally I've used script from [http://h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it](http://h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it). It found two cards:

[LIST=1]
[*]hda-intel                        VIA Technologies, Inc. VT1708/A
[*]legacy                           Probe legacy ISA (non-PnP) chips
[/LIST]
I've choosed 1. and the script finished successfully, but no sound whatsoever. 

But, in *Sound Preferences -> Hardware *there are profiles for sound card settings. Default was *Digita Stereo Duplex (IEC95). *The are many others that works but with crackling sound. The one that gives quite good sound is *Analog Stereo Duplex. *I don't know that this gaves me the best sound quality and does this profile was used whole the time when sound worked before. If so, then the only problem was that something changed the profile by itself.

@lidex, I haven't tried you commands yet and I thing that there is no need now.

Thank for your help. Because I have sound, I think that the topic can be marked as [Solved].

---

### Post by lidex on 2010-07-09
Good news. Any more problems arise, let us know.

---

### Post by session13 on 2010-12-20
The same problem again after upgrade to Ubuntu 10.04 LTS. This time it was a bug reported in [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/570984") thread. I have added there my solution.

---


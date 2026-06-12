---
title: "Pulseaudio won't recognize my onboard audio device (VIAVT1705)"
date: 2014-06-15
forum: Multimedia Software
---

### Post by Joao_Paulo on 2014-06-15
Hey!

After installing the xubuntu-desktop package, it came with PulseAudio. The problem is that PA took over as the default main output device over ALSA and it doesn't recognize my mobo's onboard audio card!

If I try to uninstall PA (purging), ALSA won't be set as the main device. How do I work around that?

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1705 Analog [VT1705 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: VT1705 Digital [VT1705 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: VT1705 Alt Analog [VT1705 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> aplay -D plughw:0,2 /usr/share/sounds/alsa/Front_Center.wavaplay: main:722: audio open error: Device or resource busy
~$ aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:722: audio open error: Device or resource busy
~$ aplay -D plughw:0,1 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono


But I still hear no sound!

My alsa info: [http://pastebin.com/E5WuqXP3](http://pastebin.com/E5WuqXP3)

---

### Post by Joao_Paulo on 2014-06-15
Was able to get sound back after some commands, but it's still not fixed.

I uninstalled pulseaudio completely since it was bugging with my onboard sound card, but now I got another problem. Sound doesn't work on startup and it gets back when I force all the alsa modules to reload. It appears to be because my Intel drivers starts off too low on priority, then it raises to it's natural position after I reload those modules.

[SIZE=6]THIS IS BEFORE RESTARTING
[/SIZE]
```
snd_hda_codec_hdmi     46207  4 
snd_hda_codec_via      27860  1 
snd_hda_intel          52355  4 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
```

[SIZE=5]Then I execute sudo alsa force-reload
[/SIZE]
Terminating processes: 1163.
Unloading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.

```
lsmod|grep snd
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hda_codec_hdmi     46207  4 
snd_hda_codec_via      27860  1 
[SIZE=3]**snd_hda_intel          52355  2 **[/SIZE]
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  15 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
```

Notice how snd_hda_intel suddenly changed it's index on the list.

My problem is exactly this one [https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Random_lack_of_sound_on_startup](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Random_lack_of_sound_on_startup)

But the workarounds on that didn't work for me. I tried adding those lines:

options snd-hda-intel index=0
options snd-hda-intel model=auto
options snd-hda-codec-via index=1

to /etc/modprobe.d/alsa-base.conf

But it didn't work. Tried turning the speech dispatcher OFF and it didn't work.

Sounds works fine after the reload thing, but it's a pain in the ass to do and other non-admin users also have access to this pc. Looking forward to a permanent fix.

---

### Post by Yellow Pasque on 2014-06-15
[http://ubuntuforums.org/showthread.php?t=2186531](http://ubuntuforums.org/showthread.php?t=2186531)

---

### Post by Joao_Paulo on 2014-06-15
Can't believe it was it -_-

Thanks for your help. I really appreciate your patience to help on this forum, I'll looking forward to aid you in the future as I get more experience at Unix enviroments!

**What I did to fix:**

1 - Run Synaptics Package Manager
2- Searched by "roar"
3- Search brought up 5 packages installed. I selected to purge those 5 and get rid of it's dependencies
4- Rebooted and the sound is okay now!

Thanks!

[SIZE=6]SOLUTION IS TO REMOVE THE RoarAudio AND IT'S LIBRARIES

[SIZE=1]Solved[/SIZE][/SIZE]

---


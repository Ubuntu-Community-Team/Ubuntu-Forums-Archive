---
title: "Sound Corruption with Sound Blaster X-Fi Extreme Audio"
date: 2009-01-31
forum: Multimedia Software
---

### Post by stderr on 2009-01-31
Hi 

[Ibex, onboard sound disabled in BIOS]

I'm having some trouble with my Sound Blaster X-Fi Extreme Audio soundcard and ALSA - used to work fine, not sure when the problems began. Perhaps with the Hardy -> Ibex upgrade, perhaps not.

Basically, when the volume is turned up high, I get audio corruption. Sometimes. I haven't managed to narrow the conditions down yet. If I use alsamixergui to turn all other inputs/outputs aside from the main output to minimum, then the situation improves a little. 

If I turn the main output down in alsamixergui, and increase volume on the speakers, quality improves (i.e. the audio is being corrupted by ALSA/something).

I have all settings set to ALSA following some problems with Pulseaudio. 

```
ace@ace1:~$ ps aux | grep pulse
ace       6583  0.0  0.0   3124   444 ?        S    Jan08   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
```

```
ace@ace1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
ace@ace1:~$ lsmod | grep snd
snd_ca0106             40480  6 
snd_ac97_codec        111652  1 snd_ca0106
snd_pcm_oss            46848  0 
snd_pcm                83204  5 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  4 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  18 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
ac97_bus                9856  1 snd_ac97_codec
snd_page_alloc         16136  2 snd_ca0106,snd_pcm
```

```
ace@ace1:~$ sudo dpkg -l alsa*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  alsa           <none>         (no description available)
ii  alsa-base      1.0.17.dfsg-2u ALSA driver configuration files
un  alsa-headers   <none>         (no description available)
ii  alsa-oss       1.0.15-1       ALSA wrapper for OSS applications
ii  alsa-utils     1.0.17-0ubuntu ALSA utilities
ii  alsamixergui   0.9.0rc2-1-9   graphical soundcard mixer for ALSA soundcard

ace@ace1:~$ sudo dpkg -l pulse*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  pulseaudio                0.9.10-2ubuntu9.3         PulseAudio sound server
ii  pulseaudio-esound-compat  0.9.10-2ubuntu9.3         PulseAudio ESD compatibility layer
ii  pulseaudio-module-gconf   0.9.10-2ubuntu9.3         GConf module for PulseAudio sound server
ii  pulseaudio-module-hal     0.9.10-2ubuntu9.3         HAL device detection module for PulseAudio sound server
un  pulseaudio-module-jack    <none>                    (no description available)
ii  pulseaudio-module-lirc    0.9.10-2ubuntu9.3         lirc module for PulseAudio sound server
ii  pulseaudio-module-x11     0.9.10-2ubuntu9.3         X11 module for PulseAudio sound server
ii  pulseaudio-module-zerocon 0.9.10-2ubuntu9.3         Zeroconf module for PulseAudio sound server
ii  pulseaudio-utils          0.9.10-2ubuntu9.3         Command line tools for the PulseAudio sound server

```

I would emphasize that if I turn the alsamixer main output down to about 50%, then you can't really hear any corruption at all, no matter how loud I turn the speakers up. Raising alsamixer beyond this level = corruption is noticeable. If I raise the level to 100%, and crank up the volume on the speakers, it sounds abysmal (I'm talking about LOUD volumes). I'm testing with FLAC files - so audio file quality isn't the issue here.

I've perused howtos, the sound solution stickies here, etc, with no joy. I'm not sure how to proceed - my knowledge of audio in Linux is a bit flaky, so even some general hints on places to look/things to test would really help.

The only thing I can think of is to compile alsa from source, but I'm not sure that'll help... I'll happily try that if other people think it may.

TIA

---

### Post by stderr on 2009-02-01
I'm probably going to try to compile ALSA from source, and go through all the steps, just so I have a better idea of what's going on.

Given I have the crappy version of the X-Fi series, which I understand is essentially an Audigy SE and is based on ca0106, I'm probably going to largely follow [these]("http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106") instructions.

---

### Post by stderr on 2009-02-02
I haven't tried compiling ALSA yet, but I've just confirmed that following a reboot, there's no audio corruption whatsoever.

At some point, I'm sure the corruption will begin again. I've tried running 2 audio apps at once, but everything's still fine. I'm wondering if there's a specific application which isn't using ALSA like it should, or something along those lines.

edit: Interestingly, whilst I thought Pulseaudio might have been interfering, things are running fine and this is the ps output:

```
ace@ace1:~$ ps aux | grep pulse
ace       6646  0.0  0.0   3124   688 ?        S    22:44   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
ace       6650  1.6  0.1  31016  4352 ?        Ssl  22:44   0:20 /usr/bin/pulseaudio -D --log-target=syslog
ace       6653  0.0  0.0   7528  2552 ?        S    22:44   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
```

---

### Post by stderr on 2009-02-04
Pulseaudio jumped in again, disabling all audio applications from working, with messages such as "device busy" etc. 

Killing the pulseaudio and pulseaudio's gconf helper processes (as listed in previous post) rectifies the issue. Why pulseaudio suddenly starts interfering beats me - it occurred after I'd left the PC for ~1day, no user input.

I haven't managed to get the audio corruption back yet, but I'm sure it won't be long :)

---


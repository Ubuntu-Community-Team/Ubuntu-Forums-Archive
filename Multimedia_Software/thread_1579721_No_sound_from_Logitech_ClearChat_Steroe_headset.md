---
title: "No sound from Logitech ClearChat Steroe headset"
date: 2010-09-22
forum: Multimedia Software
---

### Post by oygle on 2010-09-22
There are 2 jacks at the front of the computer, one for mic, the other for headphones. I plug them in, and I can't hear any sound. Have checked all sorts of documents and settings for pulseaudio and ALSA.

If I play a sound file, the Pulseaudio meters are showing that there is sound, but I cannot hear anything. Have checked the obvious, nothing is on mute.

Here are the results of some commands ..

```
~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
2.6.28-19-generic

```

```
 
~$ dmesg | egrep -i "sound|audio|snd"

```

```
~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xcddf4000 irq 16

```

```
~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

```

```
~$ lsmod | grep snd
snd_hda_intel         436276  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
~$ 
```

There is a message in syslogs ..

> 
Sep 22 21:54:14 pulseaudio[4162]: module-x11-xsmp.c: X11 session manager not running.
Sep 22 21:54:14 pulseaudio[4162]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.


Any clues please ?

Oygle

---

### Post by oygle on 2010-09-22
The onboard sound card is a .............

> 
Intel® High Definition Audio
Realtek® ALC861 8-channel CODEC with Jack-sensing and Universal Audio Jack (UAJ®) technology
S/PDIF out interface support

The motherboard supports 8-channel High Definition Audio through the onboard ALC861 CODEC with 24-bit DAC, a stereo 16-bit ADC, and an AC97 2.3 compatible multi-channel audio designed for PC multimedia systems. It also provides a Jack-Sensing function, S/PDIF out support, interrupt capability and includes the Realtek® proprietary UAJ® (Universal Audio Jack) technology.

The motherboard supports the S/PDIF Out function through the S/PDIF interfaces on the rear panel and at midboard. The S/PDIF technology turns your computer into a high-end entertainment system with digital connectivity to powerful audio and speaker systems.


---

### Post by RubeSam on 2010-09-22
Just a thought: The new monitor may  have speakers and changed your default when you set it up. Try going to  your speaker icon lower right and right click on it and left click on  playback and a window will come up and should show the different  playback devices. Make sure the one that shows speakers and not a  monitor is checked and if not, point at the speakers one and right click  and select it as default.  Hope that helps! and wow nice speakers!

---

### Post by oygle on 2010-09-22
I have looked in GNOME ALSA mixer, Pulseaudio applet, and the system settings, and the options look fine. That is, no monitor selected.

I used the headset on another computer, running the latest Ubuntu, and although it took some fiddling to work out which channels were required, I was able to hear sound, and test the mic and sound playback with the sound recorder.

Possibly the best option is to upgrade this version of Ubuntu; I have been putting it off for ages, probably the sound problems will be fixed in a leter release.

Don't know if I need ALSA and Pulseaudio either, but the computer that it 'worked' on, just had all the defaults.

Thanks for your help,

Oygle

---

### Post by oygle on 2010-09-26
Found out after booting into XP on this same computer, that the front jacks were problematic. After putting the headphone and mic leads into the same jacks at the back of the computer, we had sound and could talk over with the mic.

---


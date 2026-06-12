---
title: "Really Weird Sound problem in Lucid"
date: 2010-05-01
forum: Multimedia Software
---

### Post by adam-red on 2010-05-01
I downloaded 10.04 64bit on the day of release and I only get sound on the occasional boot - Maybe 40% of the time. My soundcard and microphone aren't being detected the rest. Totally intermittent though.

```
cat /proc/asound/cards
```

gives me

```
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22
 1 [VX5000         ]: USB-Audio - Microsoft LifeCam VX-5000
                      Microsoft Microsoft LifeCam VX-5000 at usb-0000:00:02.1-1, high speed
```

The really weird thing is that the times that it doesn't pick them up (in the sound panel at least) it won't let me shutdown or reboot. Either option just logs me out, and the shutdown and restart button at the bottom of the login screen don't do anything then so I'm forced to cold boot it and cross my fingers.

Any ideas?

Thanks
Adam

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by adam-red on 2010-05-02
Thanks for the response. Here's the output in the order requested.

uname -a
```
Linux adam-red-linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

head -n 1 /proc/asound/card*/codec#*
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

Computer isn't exactly a make/model but consists of following:
```
AMD Athlon(tm) 64 X2 Dual Core Processor 6000
2Gb RAM
GeForce 8600 GTS
nvidia CK807 AC97 Audio Controller
Microsoft LifeCam VX-5000
2x500Gb SATA HD
```

---

### Post by lidex on 2010-05-02
What is output of:
```
lsmod | grep snd
```
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by adam-red on 2010-05-02
Output of lsmod | grep snd is:
```
snd_usb_audio          92747  1 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_intel8x0           31155  3 
snd_ac97_codec        125394  1 snd_intel8x0
ac97_bus                1450  1 snd_ac97_codec
snd_pcm                87850  5 snd_usb_audio,snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_usb_lib            18978  1 snd_usb_audio
snd_hwdep               6924  1 snd_usb_audio
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  19 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_intel8x0,snd_pcm
```
I'll reboot a few more times to test it properly.

---


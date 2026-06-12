---
title: "&quot;82801BA/BAM AC'97 Audio Controller&quot; Driver Problems on Ubuntu Server 9.04"
date: 2009-07-23
forum: Multimedia Software
---

### Post by KJKJava on 2009-07-23
Greetings!  I am running Ubuntu Server 9.04 w/ no GUI.  The server is an ol' Dell OptiPlex GX240 mini tower with on-board audio.  Unfortunately, I can't seem to get the audio working!

I got excited when I found the "Comprehensive Sound Problem Solutions Guide" sticky here ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) but it didn't fix the issue.

Here is some relevant output:

```

% aplay -l
aplay: device_list:217: no soundcards found...

```

   ===

```

% aplay
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: audio open error: No such file or directory

```

   ===

```

% lspci -v [relevant output pasted]
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
        Subsystem: Dell Device 010e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

```

   ===

```

% lsmod | grep snd
snd_intel8x0           37532  0
snd_ac97_codec        111012  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46208  0
snd_mixer_oss          22528  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14208  0
snd_rawmidi            29568  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_intel8x0,snd_pcm

```

   ===

```

% alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

   ===

```

% lshw [relevant output pasted]
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

   ===

```

% sudo modprobe snd-ac97-codec
%

```

(does no output signify a failure or a success?)


========


I got a bit lost when it came to step three (in the guide), referencing the link [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/).  I got a directory listing, rather than a dropdown.

I have also tried booting with the "irqpoll" option, as I read elsewhere.  It didn't seem to change anything.

Thanks for any ideas.

---

### Post by megamih on 2009-08-23
try to add Your user to the following groups:

**audio**
pulse
pulse-access
pulse-rt

i.e.

# sudo usermod -a -G audio,pulse,pulse-access,pulse-rt **your_user_name**

It worked for me :)

---

### Post by MgFrobozz on 2009-11-10
Hi, KJKJava ...

Did the final suggestion work for you? I just updated to 9.10, and lost my audio (but I lose audio after every upgrade ...). It's the same symptoms: 'aplay -l' shows no sound card, tho 'lspci' shows I have an intel ac'97 controller; 'lsmod' shows that the intel driver is running; stopping and restarting the kernel module (via "sudo modprobe snd_intel8x0") has no effect; there are no errors shown from dmesg (except for the lines indicating the module has started).

Ps ... I've applied the suggested purgative ...
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

---


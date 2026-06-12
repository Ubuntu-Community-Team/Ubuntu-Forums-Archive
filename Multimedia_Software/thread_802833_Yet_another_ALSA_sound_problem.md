---
title: "Yet another ALSA sound problem"
date: 2008-05-21
forum: Multimedia Software
---

### Post by TomB19 on 2008-05-21
I'm having miserable difficulties with ALSA.

I've read everything I can, including the Comprehensive Guide at the top of this forum.  I apologize if I've missed something.  I've sifted through these forums for hours and hours so I believe I've tried everything.

Motherboard: Soltek K8TPro
Chipset: Via K8T800 Pro


# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0





# lspci -v
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Unknown device 1919:200a
        Flags: medium devsel, IRQ 22
        I/O ports at dc00 [size=256]
        Capabilities: [c0] Power Management version 2




# lsmod | grep snd
snd_via82xx            33192  0
gameport               18704  1 snd_via82xx
snd_ac97_codec        122200  1 snd_via82xx
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         12560  2 snd_via82xx,snd_pcm
snd_mpu401_uart        11008  1 snd_via82xx
snd_seq_dummy           5380  0
snd_seq_oss            36864  0
snd_seq_midi           11008  0
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd



When I go into kmix and select mixer, it shows no mixers exist.

When I go into the KDE system settings and restart the audio, it restarts without error.  It also restarts from the command line.


# ./alsa-utils restart
 * Shutting down ALSA...                                                                                                                           [ OK ]
 * Setting up ALSA...                                                                                                                              [ OK ]


Upon restarting ALSA, there are no relevant messages at the end of /var/log/syslog or /var/log/messages.

I'm stumped.

---

### Post by TomB19 on 2008-05-22
I apologize for the bump.

Does anyone with a K8T800 Pro chipset have ALSA running?

---

### Post by Yellow Pasque on 2008-05-22
There's always OSS4...
(see sig)

---

### Post by TomB19 on 2008-05-22
I did not mention in my first post that I have had it working with OSS.  I'm not sure what version.  It was whatever version apt-get streamed in.

The issue I had with OSS is the lack of a mixer or volume adjustment (perhaps I should study this) and I couldn't get some video players like flash and mplayer to provide sound.  System sound worked fine and so did XMMS.

I appreciate the link.  I'm leaving town for a week but will study the link while I'm gone and try it as soon as I return.

Thank you very much for the suggestion and the guide.

---


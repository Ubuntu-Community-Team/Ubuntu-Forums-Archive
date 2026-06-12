---
title: "Diamond XS 7.1DDL - SPDIF"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by ephonk on 2007-06-20
Installed Kubuntu on existing hardware and most everything works well - one exception. The Diamond XS 7.1DDL sound card is silent on the SPDIF out. Analog outs work fine, but I'd rather be optical...

Is this just a case of "non-supported hardware"?

--edit--

Some more detailed info...
```

$ lspci -v | grep -i audio
00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device

$ uname -a
Linux monkeybrain 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

$ lsmod |grep snd
snd_rtctimer            4384  0
snd_cmipci             37024  2
gameport               16520  1 snd_cmipci
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_opl3_lib           11520  1 snd_cmipci
snd_hwdep               9988  1 snd_opl3_lib
snd_mpu401_uart         9472  1 snd_cmipci
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_rtctimer,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9100  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  16 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd

$ dpkg --list | grep alsa
ii  alsa-base                                  1.0.13-3ubuntu1                        ALSA driver configuration files
ii  alsa-utils                                 1.0.13-1ubuntu5                        ALSA utilities
ii  libesd-alsa0                               0.2.36-3ubuntu4                        Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debian-alsa                       1.2.11-7ubuntu1                        Simple DirectMedia Layer (with X11 and ALSA

$ uname -r
2.6.20-16-generic

$ lsb_release -c
Codename:       feisty

$ find /lib/modules/`uname -r` -name snd-cmipci.ko
/lib/modules/2.6.20-16-generic/kernel/sound/pci/snd-cmipci.ko
```

thx...

---

### Post by Silent Warrior on 2007-06-21
I don't know that it's 'unsupported' hardware... You get sound out of it, don't you? :p Bet you anything it's a case of 'partial support', rather.
I happen to have an X-Fi XtremeMusic that does absolutely nothing in Ubuntu, and that's unsupported hardware for sure. Now, since I had some spare stuff left over after upgrading to this system, I glued together another computer and stuck Linux in it as well. I have a Live! Platinum 5.1 in it, and the card seems to work fine. I can use the headphone-connection on the Live!Drive without problem, but none of the more exotic connections seem to work. As I understand it, ALSA claims to support it.

*Surge of savvy* Have you looked through the ALSA-mixer to see if there's anything muted? Or if the digital out is deactivated?

---


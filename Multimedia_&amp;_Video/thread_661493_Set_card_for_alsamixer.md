---
title: "Set card for alsamixer"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by mararual on 2008-01-08
Hi all,

I'm having problems with sound on my ubuntu desktop. The problem is alsa. Sometimes it works fine, sometimes it doesn't (between restarts). When it does NOT work, Alsamixer shows card SiS SI7012 with chip Realtek ALC655 rev 0. On the other side, when it works, Alsamixer shows card C-Media PCI CMI8738-MC6 with chip CMedia PCI. Also, in the control center > sound panel, I can see both Sis and CMedia. When choosing CMedia and clicking test, it works fine. So how can set alsa to use only and always Cmedia? 

Thanks in advance. Let me know what other info you need. :)

---

### Post by heimo on 2008-01-08
Hi!

Couple things that could help us to help you. You could give us output from:
```

lspci |grep -i audio
```And then also:
```
lsmod | grep -i snd
```I'd probably try to put a name of the kernel module ("driver") that's used by your non-working sound chip to a file /etc/modprobe.d/blacklist or maybe editing /etc/modprobe.d/alsa-base could do it. Sorry, no specific advice right now. :-(

EDIT: Or you could try disabling onboard audio in BIOS settings.

---

### Post by mararual on 2008-01-08
Hi heimo,

thanks for the quick reply.

**lspci |grep -i audio**

output:

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
.

**lsmod | grep -i snd**
Output:

snd_cmipci             37024  1 
gameport               16776  1 snd_cmipci
snd_pcm_oss            44672  0 
snd_intel8x0           34972  0 
snd_ac97_codec        100644  1 snd_intel8x0
snd_mixer_oss          17664  1 snd_pcm_oss
ac97_bus                3200  1 snd_ac97_codec
snd_pcm                80388  4 snd_cmipci,snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_opl3_lib           11520  1 snd_cmipci
snd_seq_dummy           4740  0 
snd_hwdep              10244  1 snd_opl3_lib
snd_mpu401_uart         9600  1 snd_cmipci
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9228  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  16 snd_cmipci,snd_pcm_oss,snd_intel8x0,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm



/***********************************/

Disabling the onboard audio it's a good idea. I'll try that. If you found a better advice please let me know, thanks. :)

---


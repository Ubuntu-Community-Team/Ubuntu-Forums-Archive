---
title: "Sound problems on Feisty"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by elnerdo on 2007-05-12
Alright, I've seen a bunch of other posts while trying to solve this problem, so I'll try not to repeat their errors.  I'll be as descriptive as possible.  

I just purchased a laptop, and installed Ubuntu Feisty on it.  This is my FIRST experience with Ubuntu, I'm completely clueless on how everything works, but I'm trying to learn it as fast as possible.  The sound chip I'm using is listed as an ATI SB450.  

As of right now, everything works except for my sound. Ten minutes ago, my problem was that no sound came out of the speakers, even though Ubuntu definitely thought there was sound.  I tried a variety of "solutions" for people that had the EXACT problem and configuration as me, but nothing worked.  

I said 'ten minutes ago' for a reason.  The latest solution that I attempted was,

> 
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

if that makes it work then put : 

options snd-hda-intel probe_mask=8 model=auto

at the end of this file using:

sudo gedit /etc/modprobe.d/alsa-base


First, I couldn't figure out how to do this, as the first command turned up an error because snd-hda-intel was in use.  (To fix this, I closed the volume control).  Then I finally did it. I was excited when the commands actually didn't bring up errors, and then went to turn my volume back up only to find that now Ubuntu says that no volume control Gstreamer plugins and/or devies were found.  I really have no idea what to do.  I've been working on this for an entire day now, and I'm very frustrated.  

Thanks in advance, and I'll go get all the information you need as soon as possible.  

I can't post my lsmod and lspci yet, because I'm not on my laptop right now, but I'll reply to myself and do that as soon as I can.

---

### Post by elnerdo on 2007-05-12
lsmod | grep snd
```

snd_hda_intel          22552  0 
snd_hda_codec         213376  1 snd_hda_intel
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35072  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56324  11 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

```

lspci
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

```

Let me know if there are any other things I'm supposed to post.

EDIT: Here's the results of "cat /proc/asound/oss/sndstat"

```

Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc3 emulation code)
Kernel: Linux gabe-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG

```

lspci | grep audio returns nothing

---

### Post by raydar on 2007-05-23
Your very last code quote there looks exactly like mine except the top line happens to read "ALSA v1.0.14rc1 emulation code" instead of "ALSA v1.0.14rc3 emulation code."  I'm running Feisty (Kubuntu) on an old Dell Latitude cpi d300xt (PII300, 192MB RAM).  

I checked in my BIOS to make sure I hadn't disabled sound for some reason, and I did find that it was set to half duplex instead of full, so I changed it to full.  But that didn't change the fact I have no sound, and although I haven't done all the shell-command checking you have, it seems that like in your case, the OS thinks sound is otherwise set up and enabled--it doesn't hand me any error messages or anything.  

Did you/anyone find a solution?

---

### Post by TSE on 2007-05-23
hi
i also had a sound problem, searched around a lot and this 
> sudo /etc/init.d/alsa-utils reset

helped :D

PS if yuo are a newbie as i am ...just open a shell (terminal) an type the above in, thats it ;)

---

### Post by conxorxa on 2007-05-23
I have the same sound card as you (I'm running Feisty Kubuntu on an Acer Aspire 5050) and I got sound to work by specifying only the model=auto option, i.e.,

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel model=auto

In order to get the rmmod to work I had to first quit all sound programs (mixer, cdplayer, etc) then stop and restart the alsa-utils daemon:

sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsa-utils start 

and then wait a few seconds.

I also added:
options snd-hda-intel model=auto

at the end of /etc/modprobe.d/alsa-base,

so I hope it still works when I reboot.

---


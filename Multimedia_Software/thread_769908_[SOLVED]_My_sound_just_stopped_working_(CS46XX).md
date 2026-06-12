---
title: "[SOLVED] My sound just stopped working (CS46XX)"
date: 2008-04-27
forum: Multimedia Software
---

### Post by GuruCesc on 2008-04-27
Hello,
  When I first installed Ubuntu a year or so ago, the sound (and most of the system) worked out of the box. A week or so ago, I noticed that the sound had just stopped working. I have gone through all the information that I find in the posts with no luck.

  The VERY first think that I tried when I noticed the issue was checking if any device was muted.

  Here is the output that I get:

lspci -v
```

00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM Unknown device 0153
        Flags: bus master, slow devsel, latency 64, IRQ 9
        Memory at e8100000 (32-bit, non-prefetchable) [size=4K]
        Memory at e8000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

```
What I did notice is that I have other devices using the same IRQ 9, but I don't seem to be having issues with the other devices

cat /proc/interrupts
```

           CPU0       
  0:     852014          XT-PIC  timer
  1:       4223          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          2          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:      45412          XT-PIC  yenta, CS46XX, eth0, ndiswrapper
 11:      55778          XT-PIC  uhci_hcd:usb1, yenta
 12:       3077          XT-PIC  i8042
 14:      10570          XT-PIC  ide0
 15:      30108          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```

lsmod | grep snd
```

snd_cs46xx             89448  0 
gameport               17160  2 snd_cs46xx
snd_rawmidi            27264  1 snd_cs46xx
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  1 snd_cs46xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 cs46xx,snd
snd_page_alloc         11400  2 snd_cs46xx,snd_pcm

```

I tried reinstalling the alsa drivers from the repository...
no luck either

See as well the results of a couple other commands:
cat /proc/asound/cards
```

 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xe8100000/0xe8000000, irq 9

```

aplay -l
```

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: CS46xx [Sound Fusion CS46xx], dispositivo 0: CS46xx [CS46xx]
  Subdispositivos: 31/31
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
tarjeta 0: CS46xx [Sound Fusion CS46xx], dispositivo 1: CS46xx - Rear [CS46xx - Rear]
  Subdispositivos: 31/31
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
tarjeta 0: CS46xx [Sound Fusion CS46xx], dispositivo 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

aplay -vv whatever.wav 
```

Sonando WAVE 'whatever.wav' : Unsigned 8 bit, Ratio 8000 Hz, Mono
Plug PCM: Hardware PCM card 0 'Sound Fusion CS46xx' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 8
  buffer_size  : 4000
  period_size  : 1024
  period_time  : 128000
  tick_time    : 4000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 3072
  stop_threshold   : 4000
  silence_threshold: 0
  silence_size : 0
  boundary     : 2097152000
########################################## +      | 87%%

```

  Help me have this fixed before I'm asked to install windows back!!!!!

---

### Post by GuruCesc on 2008-04-29
Anyone can help??? Please!!!

---

### Post by GuruCesc on 2008-07-07
Hello All!!
  After trying so many things that I can't even remember, I decided to burn a DVD to backup my information, I got my parents XP CD and did a fresh install on the laptop.

  NO sound in Windows either. I tried changing the drivers there with no luck either.

  I had decided to make the sound work in Linux even if I had to code anything myself, I just wanted to make sure that the sound chip actually worked!

  That was it then, I'm installing Ubuntu 8.04 back over the week!!

  Thanks to all of you that took the time to read my post!

Regards,
Cesar

---

### Post by GuruCesc on 2008-07-10
Hello All,
  Now I have solved the problem. It was not Linux related!!!!

  I read on a Linux forum somewhere that some of the components on the lap have conflicts with the sound. Since I didn't have sound in either Windows or Linux, I gave it a try.

  Since I didn't find a way to enable / disable the sound card on the BIOS, I disabled ALL those things I don't need: Serial Ports, IR, Parallel port, Wake on LAN, etc. And I made sure that the laptop volume buttons were enabled.

  I hit the "Volume Up" (several times) and hit right arrow (which is not a valid option) and the laptop "beeped". I restarted the laptop and even though the OS didn't have any sound, pushing the "Volume Up" key enabled it.

  Enabling it once in Linux and restarting was enough for keeping it enabled. In Windows I needed to enable it every time I restarted (I'm sure reinstalling the drivers or something will fix the issue there, yet it's out of the scope of this post / forum)

Regards,
Cesar

---


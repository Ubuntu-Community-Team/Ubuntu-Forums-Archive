---
title: "M-Audio 66, not working."
date: 2010-08-22
forum: Multimedia Software
---

### Post by dchurch24 on 2010-08-22
Hi all,

I had (until a few hours ago) 9.10 64 bit RT running on my machine; as usual I had no sound from my M-Audio 66 when I booted up, so fiddled around with the normal things - outputs mysteriously changing to S-PDIF on their own, all the cables (the amp emits sound when I touch the connectors to the soundcard) etc... but after 3 hours, I gave up - I usually give myself 1 or 2 hours to get the sound working when I want to record anything and if I can't get it working in that time, then I generally give up.

Today, however, I had an idea for a song so persevered for a few more hours to get sound, but alas, failed miserably - sometimes I win, sometimes I don't (it's starting to put me off trying to record anything lately, the creativity giving way to the impending frustration and high-blood pressure gained by getting it working before I can start).

I installed the 32 bit 10.04 in the hope that perhaps the ALSA/M-AUDIO etc... stuff had been updated and worked better in a later version or 32 bit version.
I seem to have managed to get the card recognised at last, by adding:

options snd-ice1712 model=delta66

into the alsa-base.conf file - then I can run the envy24control program, although if I reboot then I get the all too familiar: "No ICE cards found".

When it does see the card however, I open Envy24 and apart from their being no sound from anything, all the H/W Out options are missing in the Patchbay tab, as well as almost anything to do with any inputs.

...as can be seen here:

[[IMG]http://thumbnails33.imagebam.com/9423/bc5fdd94224095.jpg[/IMG]](http://www.imagebam.com/image/bc5fdd94224095) [[IMG]http://thumbnails26.imagebam.com/9423/96c17d94224098.jpg[/IMG]](http://www.imagebam.com/image/96c17d94224098) 

Jack starts fine, and in the Setup I can see "IceEnsemble ICE1712" and "ICE1712 multi" to select from.

A dmesg returns this:

```

[   85.038473] ICE1712 0000:03:00.0: PCI INT A -> Link[LNEC] -> GSI 17 (level, low) -> IRQ 17
[   85.038515] ice1712: No matching model found for ID 0x0

```

Which implies that it's found the card but no driver for the card. I also tried changing the cards name from:

options snd-ice1712 model=delta66

to

options snd-ice1712 model=delta1010LT

as this has helped in the past on an old OS, but sadly the result is the same.

cat /proc/asound/cards

produces:

```

 0 [ICE1712        ]: ICE1712 - ICEnsemble ICE1712
                      ICEnsemble ICE1712 at 0xbc00, irq 17

```

"lsmod |grep ice"  returns:


```

snd_ice1712            55129  4 
snd_ice17xx_ak4xxx      2547  1 snd_ice1712
snd_ak4xxx_adda         7364  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              6522  1 snd_ice1712
snd_ac97_codec        100646  1 snd_ice1712
snd_pcm                70662  4 snd_ice1712,snd_ac97_codec
snd_i2c                 4398  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         5617  1 snd_ice1712
snd_seq_device          5700  1 snd_rawmidi
snd                    54148  16 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device

```

Also, when I start Jackctl I get the message "Could not open ALSA sequencer as a client"

if I do: modprobe snd-seq, then this goes away, until the next time that I reboot.

Anyone have a clue as to what's going on?

---

### Post by dchurch24 on 2010-08-22
Ahh - ok, a quick reboot later, then 

sudo gedit /etc/modprobe.d/alsa-base.conf

changed it from delta66 to delta1010LT (don't know why, the card is definetly a 66), then modprobe snd-ice1712 (without the card name), and now all appears and I have just tested output and input and it's all working.

Thanks to anyone with the patience to read the above ;-)

---


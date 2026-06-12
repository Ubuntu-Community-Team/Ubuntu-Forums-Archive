---
title: "No signal with Pinnacle PCTV Stereo (saa7134), tvtime"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by blairboy362 on 2007-01-29
Hi,

I have been unable to get any kind of signal from my Pinnacle PCTV Stereo card so far.

I have mainly been guided by [http://gentoo-wiki.com/HARDWARE_saa7134]("http://gentoo-wiki.com/HARDWARE_saa7134#tuner")  in setting up the driver options. I have run a modified version of the script to try loading the (saa7134) module with a different tuner each time, by looping from 1 to 69.

I monitored /var/log/kern.log while this was looping to see if anything changed when the module was loaded. Nothing did. Part of the script runs TVTime as the main test. With each iteration of the loop, I scanned all of the channels for a signal (yes, I've been at this a while) just to be exhaustive.

About my system:
Based in the UK.
Dapper Drake (6.06)
kernel 2.6.15-27-386
tvtime v 1.01 - I haven't really changed any settings from the defaults, except for the standard of broadcasting to Europe (PAL).

Am I missing something? I'm confident that the card is set correctly, as the "card" driver option value I have matches the identifier of the card (26), as given in the above page.

Any help will be much appreciated.


The modified script I used is below:

```

#/bin/sh
MAXTUNER=69
i=0

while [ $i -lt $MAXTUNER ];
do
  rmmod saa7134_alsa saa7134
  modprobe saa7134 card=26 tuner=$i
  echo "Actual tuner is:" $i
  sleep 1 # this is to make sure /dev/video is registered when tvtime starts
  tvtime
  i=$(($i+1))
done

```

Below follows the information that I think is relevant from the kernel logs. It is repeated each time the above script loops.

```

saa7130/34: v4l2 driver version 0.2.14 loaded
ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 185
saa7134[0]: found at 0000:00:0a.0, rev: 1, irq: 185, latency: 32, mmio: 0xe6000000
saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
saa7134[0]: board init: gpio is 0
tda9887 0-0043: chip found @ 0x86 (saa7134[0])
saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 50: 0c 22 17 34 02 94 c7 b7 ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
saa7134 ALSA driver for DMA sound loaded
saa7134[0]/alsa: saa7134[0] at 0xe6000000 irq 185 registered as card -1
saa7134[0]/irq[10,780542]: r=0x20 s=0x10 PE
saa7134[0]/irq: looping -- clearing PE (parity error!) enable bit

```

```

$ lsmod | grep saa7134
saa7134_alsa           13408  1 
saa7134               115936  1 saa7134_alsa
snd_pcm                89864  5 saa7134_alsa,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd                    55268  16 saa7134_alsa,snd_seq_oss,snd_seq,snd_mpu401,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
video_buf              22148  2 saa7134_alsa,saa7134
v4l2_common             6016  1 saa7134
v4l1_compat            14468  1 saa7134
ir_kbd_i2c              8460  1 saa7134
i2c_core               21904  6 saa7134,i2c_acpi_ec,tda9887,tuner,i2c_viapro,ir_kbd_i2c
ir_common               9988  2 saa7134,ir_kbd_i2c
videodev                9856  1 saa7134

```

---

### Post by josesanders on 2007-01-31
When you first boot up the machine, what is the result when you type the command:
$ dmesg

Also, I noticed in the script that you keep the same card number, just change the tuner option.  I had some problems with a saa7134 card not being recognized, and I never specified a tuner number, only a card number.  I found that my card actually works with about a third of the card numbers.  Even though 26 should be the right number for your card, I would recommend trying a few different ones, or maybe modifying the script to cycle through card numbers, not specifying the tuner, something like this:


```
#/bin/sh
MAXTUNER=69
i=0

while [ $i -lt $MAXTUNER ];
do
  rmmod saa7134_alsa saa7134
  modprobe saa7134 card=$i
  echo "Actual card is:" $i
  sleep 1 # this is to make sure /dev/video is registered when tvtime starts
  tvtime
  i=$(($i+1))
done
```

I should mention, though, that while I did get the card to work with TVTime, I could not get it to work with MythTV, so if that's your ultimate goal, I would recommend you just spend that extra money and get a Hauppauge 150.

---

### Post by Darrarski on 2007-01-31
Try this:
saa7134 card=77 tuner=54
It's working with Pinnacle PCTV 110i

---

### Post by blairboy362 on 2007-01-31
Hi,

thanks for the replies.

josesanders:
I looped through the card values like you suggested, but not really any change. Sometimes, I would get some flickering in the snow when scanning through channels 50-85ish, but I don't think it's anything worth getting excited about.

Darrarski:
I tried those values, but without success. It did, however, render my desktop virtually unresponsive while tvtime was running.


Thanks again. I'll keep trying.

---

### Post by josesanders on 2007-02-01
If you have static, there is a chance that the card is in fact working, and there is something wrong with the frequency settings, or a problem with the tv signal not getting to the tuner.  In my experience, I would either get a black screen, meaning that the card number didn't work, or I would get channels.  I never just got static.  Do you get static for all attempts, or do some give you a black screen, and some others give you static?

It sounds obvious, so I hate to make the suggestion, but have you tried hooking up the cable that you have going to your computer straight to a TV to make sure that it actually has a signal?

---

### Post by blairboy362 on 2007-02-01
Some card numbers gave me a black screen, others gave me static. I tested different tuner values with all the card numbers that gave me static, with no joy.

I'll test my aerial with a TV over the weekend to make sure it's working.

---

### Post by blairboy362 on 2007-02-04
Hi,

I've tested the aerial, and it's working perfectly, so it's not the aerial causing the problems.

---


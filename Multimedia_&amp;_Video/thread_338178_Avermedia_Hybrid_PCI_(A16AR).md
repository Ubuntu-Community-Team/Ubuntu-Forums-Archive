---
title: "Avermedia Hybrid PCI (A16AR)"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by voltagex on 2007-01-14
Hi,
I'm trying to get an Avermedia Hybrid PCI DVB card to work. Google tells me other people have had mixed success. The SAA7134 chip it uses should be well supported... does anyone know how to get this troublesome card to work? I've followed about 3 different tutorials.

Thanks in advance.

---

### Post by pseudonym on 2007-01-14
I don't own that card but I had a discussion with someone about a card which uses the same chip, in [this]("http://www.ubuntuforums.org/showthread.php?t=328140&highlight=peeper+saa7134") thread. Basically, you need to make sure the module 'saa7134-dvb' gets loaded (sudo modprobe saa-7134).

HTH

---

### Post by voltagex on 2007-01-14
Yes, saa7134-dvb does get loaded, still no dice :(

---

### Post by Dovad on 2007-01-16
I have a problem similar to yours also 6.10. The card above is detected properly:

dmesg dump

```

[17179606.928000] saa7134[0]: found at 0000:05:09.0, rev: 1, irq: 66, latency: 160, mmio: 0xfcb01000
[17179606.928000] saa7134[0]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
[17179606.928000] saa7134[0]: board init: gpio is 10000
[17179606.928000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input3
[17179607.064000] saa7134[0]: i2c eeprom 00: 68 51 01 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179607.064000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[17179607.064000] saa7134[0]: i2c eeprom 20: 01 40 01 02 03 ff 01 03 08 ff 01 08 ff ff ff ff
[17179607.064000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179607.064000] saa7134[0]: i2c eeprom 40: ff 1b 00 c0 ff 10 01 01 ff ff ff ff ff ff ff ff
[17179607.064000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179607.064000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179607.064000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179607.064000] saa7134[0]: registered device video0 [v4l2]
[17179607.064000] saa7134[0]: registered device vbi0
[17179607.136000] saa7134 ALSA driver for DMA sound loaded
[17179607.136000] saa7134[0]/alsa: saa7134[0] at 0xfcb01000 irq 66 registered as card -1
...
...
[17179607.732000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[17179607.756000] lp0: using parport0 (interrupt-driven).

```

I have in my /etc/modules

```

saa7134-dvb

```

My "lsmod | grep saa" shows:

```

saa7134_dvb            15108  0 
mt352                   7940  1 saa7134_dvb
video_buf_dvb           7684  1 saa7134_dvb
nxt200x                15364  1 saa7134_dvb
dvb_pll                13700  2 saa7134_dvb,nxt200x
tda1004x               17668  1 saa7134_dvb
saa7134_alsa           15392  0 
snd_pcm                84612  5 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_usb_audio,snd_pcm_oss
saa7134               118496  2 saa7134_dvb,saa7134_alsa
video_buf              27652  5 bttv,saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
v4l2_common            17280  2 bttv,saa7134
v4l1_compat            15108  1 saa7134
ir_kbd_i2c              9872  1 saa7134
compat_ioctl32          2432  3 bttv,usbvideo,saa7134
snd                    58372  15 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_seq_oss,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
ir_common              28548  3 bttv,saa7134,ir_kbd_i2c
videodev               10752  3 bttv,usbvideo,saa7134
i2c_core               23424  11 bttv,i2c_algo_bit,tveeprom,i2c_ec,saa7134_dvb,mt352,nxt200x,tda1004x,saa7134,ir_kbd_i2c,nvidia

```

I have trawled the web, searched linux-tv sites/forums etc. I ran the script on linux-tv to generate the /dev/dvb nodes. I simply cannot get the 'scan' command to detect any channels. I am in the area of uk-mendip transmitter and my init commands are as follows:

```

% scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Mendip 

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Mendip
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754167000 0 2 9 1 0 0 0
>>> tune to: 754167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

I am really scratching my head and as per usual with these types of issues, I feel I am only a hairs breadth from the answer. Any further pointers assistance would be appreciated.

Thanks, David.

---

### Post by styelz on 2007-03-27
> **voltagex said:**
> Hi,
I'm trying to get an Avermedia Hybrid PCI DVB card to work. Google tells me other people have had mixed success. The SAA7134 chip it uses should be well supported... does anyone know how to get this troublesome card to work? I've followed about 3 different tutorials.

Thanks in advance.


I have the Avermedia Hybrid A16AR PCI DVB. To get it to work I had to do the following.

Download and install kernel 2.6.19 or above (see [HERE]("http://www.howtoforge.com/kernel_compilation_ubuntu")), this kernel has support for Avermedia Hybrid. You can find information on each card type under /usr/src/linux-2.6.19/Documentation/video4linux/CARDLIST.saa7134. The one I used was 99. I also used CARDLIST.tuner to get the number for the tuner, 67.

Add the following to file /etc/modprobe.d/saa7134
```

options saa7134 card=99 alsa=1 tuner=67
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-dvb ; /sbin/modprobe tuner ; /sbin/modprobe mt352

```

Reboot into your new kernel, you should see your card configured in dmesg. This allowed me to get Digital TV to work with the Zarlink MT352 DVB-T  but I was unable to get the Analog TV tuner to work (any ideas?)

Good Luck

---

### Post by voltagex on 2007-04-11
Thanks for that, I'll be trying that once Feisty is stable as I have no hard drive space for Ubuntu at the moment :(

---

### Post by voltagex on 2007-04-28
Any word on what has to be done under Feisty to get this card working, at least for DVB-T?

---

### Post by Gruelius on 2007-06-15
I still cant get my card to work, do i need to recompile the kernel or something?

---


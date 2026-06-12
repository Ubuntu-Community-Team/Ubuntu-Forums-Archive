---
title: "SATSC/dvb not working for Pinnacle PCTV HD 800i"
date: 2014-09-26
forum: Multimedia Software
---

### Post by Jacob_Strandlien on 2014-09-26
I'm running a freshly updated Ubuntu 14.04.1 and I just instald a Pinnacle PCTV HD 800i PCI card to replace an old KWorld card that wore out.  It has both analog and digital inputs, but I can't get Ubuntu to properly recognize the digital input.  After doing some research, I'm led to believe that a properly running card will come with a directory at /dev/dvb, but that never appears.  Here's the output of several pertinent commands:

lspci -v
```
04:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: Pinnacle Systems Inc. Device 0051
    Flags: medium devsel, IRQ 21
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>

04:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
    Subsystem: Pinnacle Systems Inc. Device 0051
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio

04:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
    Subsystem: Pinnacle Systems Inc. Device 0051
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88-mpeg driver manager

```

I have come to understand that the card uses modules with names starting with cx88, so
lsmod | grep cx88
```
cx88_vp3054_i2c        12911  0 
cx8802                 18972  0 
cx8800                 37892  0 
cx88_alsa              18359  1 
cx88xx                 88508  3 cx88_alsa,cx8800,cx8802
btcx_risc              13640  4 cx88_alsa,cx8800,cx8802,cx88xx
tveeprom               21216  1 cx88xx
videobuf_dma_sg        19262  4 cx88_alsa,cx8800,cx8802,cx88xx
rc_core                28124  12 lirc_dev,ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,cx88xx,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_pinnacle_pctv_hd
v4l2_common            15681  3 tuner,cx8800,cx88xx
videobuf_core          26023  5 videobuf_dma_sg,videobuf_dvb,cx8800,cx8802,cx88xx
videodev              134688  5 tuner,cx88_alsa,cx8800,cx88xx,v4l2_common
i2c_algo_bit           13413  2 cx88_vp3054_i2c,cx88xx
snd_pcm               102099  4 cx88_alsa,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd                    69322  20 snd_hda_codec_realtek,cx88_alsa,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
```

and most importantly:
dmesg | grep cx88
```
[   98.391858] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[   98.663867] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:14.4/0000:04:07.1/rc/rc0/input17
[   98.663914] rc0: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:14.4/0000:04:07.1/rc/rc0
[   98.672635] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   98.672945] cx88[0]/0: found at 0000:04:07.0, rev: 5, irq: 21, latency: 64, mmio: 0xfd000000
[   98.673742] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input18
[   98.677924] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[  101.728114] cx88[0]/0: registered device video0 [v4l2]
[  101.728176] cx88[0]/0: registered device vbi0
[  101.728238] cx88[0]/2: cx2388x 8802 Driver Manager
[  101.728316] cx88[0]/2: found at 0000:04:07.2, rev: 5, irq: 21, latency: 64, mmio: 0xfb000000
[  101.739815] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[  101.739819] cx88/2: registering cx8802 driver, type: dvb access: shared
[  101.739821] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[  101.739823] cx88[0]/2: cx2388x based DVB/ATSC card
[  101.739824] cx8802_alloc_frontends() allocating 1 frontend(s)
[  101.744839] cx88[0]/2: frontend initialization failed
[  101.744844] cx88[0]/2: dvb_register failed (err = -22)
[  101.744846] cx88[0]/2: cx8802 probe failed, err = -22

```

Through research, I have found the following commands suggested as a fix:
```
rmmod cx8800
rmmod cx88-alsa
rmmod cx8802
rmmod cx88xx
modprobe cx88xx
modprobe cx88-dvb
```

But when I get to rmmod cx88-alsa, I get the following error:
```
ERROR: Module cx88_alsa is in use
```

And that's where I'm stuck, because I can't figure out what's using that module.  Would someone be so kind as to point me in the right direction?

Thanks!

---


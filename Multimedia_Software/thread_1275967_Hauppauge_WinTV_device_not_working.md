---
title: "Hauppauge WinTV device not working"
date: 2009-09-26
forum: Multimedia Software
---

### Post by lucyb on 2009-09-26
I'm trying to get a PCI TV card working under Ubuntu 9.04. When I run Me TV it give the error message - "There are no available DVB tuner devices"

What do I need to do to configure it?

lucy@lotus:~$ lspci | grep -i cx
03:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)

lucy@lotus:~$ ls /dev/video0 -al
crw-rw----+ 1 root video 81, 0 2009-09-25 18:15 /dev/video0

Snip-it from dmesg:
[ 8.625522] Linux video capture interface: v2.00
[ 8.631861] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 8.718354] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[ 8.718702] cx8800 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 8.719377] cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,autodetected], frontend(s): 0
[ 8.719379] cx88[0]: TV tuner type -1, Radio tuner type -1
[ 8.746451] cx2388x alsa driver version 0.0.6 loaded
[ 8.778319] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8.801653] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[ 8.849311] tuner' 1-0061: chip found @ 0xc2 (cx88[0])
[ 8.884485] tveeprom 1-0050: Hauppauge model 34705, rev J198, serial# 2976151
[ 8.884489] tveeprom 1-0050: tuner model is TCL 2002MI_3H (idx 98, type 4)
[ 8.884491] tveeprom 1-0050: TV standards PAL(I) PAL(D/D1/K) (eeprom 0x50)
[ 8.884493] tveeprom 1-0050: audio processor is CX881 (idx 31)
[ 8.884495] tveeprom 1-0050: has radio
[ 8.884497] cx88[0]: warning: unknown hauppauge model #34705
[ 8.884498] cx88[0]: hauppauge eeprom: model=34705
[ 8.884611] input: cx88 IR (Hauppauge WinTV 34xxx as /devices/pci0000:00/0000:00:14.4/0000:03:05.0/input/input5
[ 8.889067] cx88[0]/0: found at 0000:03:05.0, rev: 5, irq: 20, latency: 64, mmio: 0xfc000000
[ 8.889140] cx88[0]/0: registered device video0 [v4l2]
[ 8.889177] cx88[0]/0: registered device vbi0
[ 8.889214] cx88[0]/0: registered device radio0
[ 8.889277] tuner' 1-0061: tuner type not set
[ 8.889358] cx88_audio 0000:03:05.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 8.889383] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards

lucy@lotus:~$ lsmod | grep -i cx
cx8800 38148 0
cx88_alsa 18824 1
snd_pcm 83076 4 snd_hda_intel,cx88_alsa,snd_pcm_oss
cx88xx 79272 2 cx8800,cx88_alsa
ir_common 52228 1 cx88xx
i2c_algo_bit 14084 1 cx88xx
videobuf_dvb 15236 1 cx88xx
snd 62756 21 snd_hda_intel,cx88_alsa,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom 20100 1 cx88xx
videodev 41600 3 cx8800,tuner,cx88xx
compat_ioctl32 9344 1 cx8800
v4l2_common 20992 2 cx8800,tuner
videobuf_dma_sg 20484 3 cx8800,cx88_alsa,cx88xx
videobuf_core 26500 4 cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
btcx_risc 13064 3 cx8800,cx88_alsa,cx88xx

---

### Post by HappyFeet on 2009-09-26
See [this]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)").

---

### Post by lucyb on 2009-09-26
> **HappyFeet said:**
> See [this]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)").

Thanks. I assume that I don't need to recompile the kernel since the cx88xx module is available? That said, the article mentions the cx88-dvb module, which isn't available. Do I need this or has it been renamed?

I've tried reading a linked article about the Hauppage WinTV Go card specifically and it says to try "modprobe cx88xx tuner=56 && modprobe cx8800". However, that still doesn't make it work.

---


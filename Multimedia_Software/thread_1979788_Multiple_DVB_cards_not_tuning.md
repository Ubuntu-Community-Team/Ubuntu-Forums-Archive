---
title: "Multiple DVB cards not tuning"
date: 2012-05-14
forum: Multimedia Software
---

### Post by gregmythtv on 2012-05-14
Hi,
I have recently moved over from Mythdora to Mythbuntu, Ubuntu 11.10 (GNU/Linux 3.0.0-12-generic i686). I have 3 DVB cards, two are the same brand which seem to load correctly but fail to scan.
I have tested the cards with tzap and found only 1 card to work.
Details below, I'm not sure where to look for the problem. Any help would be great.

Regards
Greg.

[EMAIL="masterbackend@mythtvbackend:%7E/.tzap"]masterbackend@mythtvbackend:~/.tzap[/EMAIL]$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 A-LE] (rev a1)
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:02.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:02.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:04.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

[EMAIL="masterbackend@mythtvbackend:%7E/.tzap"]masterbackend@mythtvbackend:~/.tzap[/EMAIL]$ lsmod | grep saa
saa7134_dvb            33358  0
saa7134_alsa           18172  2
videobuf_dvb           13867  2 saa7134_dvb,cx88_dvb
snd_pcm                80468  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,cx88_alsa
saa7134               153846  2 saa7134_dvb,saa7134_alsa
snd                    55902  17 saa7134_alsa,snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rc_core                25797  10 rc_dntv_live_dvbt_pro,saa7134,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
v4l2_common            15793  4 tuner,cx8800,saa7134,cx88xx
videobuf_dma_sg        18786  8 saa7134_dvb,saa7134_alsa,cx88_dvb,cx88_alsa,cx8800,cx8802,saa7134,cx88xx
videodev               85626  5 tuner,cx8800,saa7134,cx88xx,v4l2_common
tveeprom               17009  2 saa7134,cx88xx
videobuf_core          25409  6 videobuf_dvb,cx8800,cx8802,saa7134,cx88xx,videobuf_dma_sg


[EMAIL="masterbackend@mythtvbackend:%7E/.tzap"]masterbackend@mythtvbackend:~/.tzap[/EMAIL]$ dmesg | grep saa
[   16.405800] saa7130/34: v4l2 driver version 0.2.16 loaded
[   16.405898] saa7134 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.405910] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 21, latency: 32, mmio: 0xf0004000
[   16.405922] saa7133[0]: subsystem: 1822:0022, board: Twinhan Hybrid DTV-DVB 3056 PCI [card=131,autodetected]
[   16.405950] saa7133[0]: board init: gpio is 0
[   16.556786] saa7133[0]: i2c eeprom 00: 22 18 22 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   16.556812] saa7133[0]: i2c eeprom 10: 00 01 fb 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[   16.556835] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 10 ff ff ff ff
[   16.556858] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.556882] saa7133[0]: i2c eeprom 40: ff 21 00 c2 84 10 03 32 15 50 ff ff ff ff ff ff
[   16.556905] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.556928] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.556951] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.556973] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.556996] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.557019] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.557043] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.557070] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.557100] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.557128] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.557153] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.216414] saa7133[0]: registered device video0 [v4l2]
[   20.216599] saa7133[0]: registered device vbi0
[   20.216805] saa7133[0]: registered device radio0
[   20.455696] saa7134 0000:02:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.455707] saa7133[1]: found at 0000:02:03.0, rev: 209, irq: 16, latency: 32, mmio: 0xf0005000
[   20.455718] saa7133[1]: subsystem: 1822:0022, board: Twinhan Hybrid DTV-DVB 3056 PCI [card=131,autodetected]
[   20.455742] saa7133[1]: board init: gpio is 0
[   20.608048] saa7133[1]: i2c eeprom 00: 22 18 22 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   20.608075] saa7133[1]: i2c eeprom 10: 00 01 fb 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[   20.608100] saa7133[1]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 10 ff ff ff ff
[   20.608124] saa7133[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608147] saa7133[1]: i2c eeprom 40: ff 21 00 c2 84 10 03 32 15 50 ff ff ff ff ff ff
[   20.608170] saa7133[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608193] saa7133[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608216] saa7133[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608239] saa7133[1]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608261] saa7133[1]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608284] saa7133[1]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608307] saa7133[1]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608329] saa7133[1]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608352] saa7133[1]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608375] saa7133[1]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.608397] saa7133[1]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.164350] saa7133[1]: registered device video2 [v4l2]
[   24.164493] saa7133[1]: registered device vbi2
[   24.164570] saa7133[1]: registered device radio2
[   24.171276] saa7134 ALSA driver for DMA sound loaded
[   24.171339] saa7133[0]/alsa: saa7133[0] at 0xf0004000 irq 21 registered as card -2
[   24.171985] saa7133[1]/alsa: saa7133[1] at 0xf0005000 irq 16 registered as card -1
[   24.192084] DVB: registering new adapter (saa7133[0])
[   29.436047] DVB: registering new adapter (saa7133[1])


[EMAIL="masterbackend@mythtvbackend:%7E/.tzap"]masterbackend@mythtvbackend:~/.tzap[/EMAIL]$ tzap -a 0 abc1
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
reading channels from file '/home/masterbackend/.tzap/channels.conf'
tuning to 226500000 Hz
video pid 0x0200, audio pid 0x028a
status 00 | signal 28af | snr 0000 | ber 00000000 | unc 00000000 |
status 1e | signal 5e2f | snr cccc | ber 00000000 | unc 00000000 | FE_HAS_LOCK

[EMAIL="masterbackend@mythtvbackend:%7E/.tzap"]masterbackend@mythtvbackend:~/.tzap[/EMAIL]$ tzap -a 1 abc1
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
reading channels from file '/home/masterbackend/.tzap/channels.conf'
tuning to 226500000 Hz
video pid 0x0200, audio pid 0x028a
status 00 | signal ffff | snr 9696 | ber 0001fffe | unc 00000000 |
status 00 | signal ffff | snr 8e8e | ber 0001fffe | unc 00000000 |


[EMAIL="masterbackend@mythtvbackend:%7E/.tzap"]masterbackend@mythtvbackend:~/.tzap[/EMAIL]$ tzap -a 2 abc1
using '/dev/dvb/adapter2/frontend0' and '/dev/dvb/adapter2/demux0'
reading channels from file '/home/masterbackend/.tzap/channels.conf'
tuning to 226500000 Hz
video pid 0x0200, audio pid 0x028a
status 00 | signal ffff | snr 0000 | ber 0001fffe | unc 00000000 |
status 00 | signal ffff | snr 0000 | ber 0001fffe | unc 00000000 |

---

### Post by gregmythtv on 2012-05-15
Fixed it!
A more detailed search of the log file showed that the tda1004x firmware was not loading because it is not inlcuded in this version of Mythbuntu.
I found these files on a older system

/lib/firmware/dvb-fe-tda10045.fw  
/lib/firmware/dvb-fe-tda10048-1.0.fw
/lib/firmware/dvb-fe-tda10046.fw  

and copied them into /lib/firmware

All three tuners work now.
Why was something so small and simple left out of the latest Mythbuntu?

---


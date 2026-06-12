---
title: "No Sound from tvtime"
date: 2009-06-04
forum: Multimedia Software
---

### Post by aviator27 on 2009-06-04
Hello,

I am having Ubuntu 9.04 in my system will all available updates. I am having a Pinnacle PCTV card and configured it well using sme online forums and instructions. (tvtime and sound using sox) It was working well till yesterday. Now suddenly even if execute the sox command i used to do, the sound is not coming in TV [IMG]http://theubuntuforums.org/images/smilies/sad.gif[/IMG]. When i execute the sox command and open the tvtime, sound is cming with some disturbance for 2-3 seconds and when the video comes, it goes away!!
Any help is greatly appreciated. Thanks!

Some outputs the might be helpful

dmesg|grep saa
```
[   11.015889] saa7130/34: v4l2 driver version 0.2.14 loaded
[   11.015963] saa7134 0000:05:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.015970] saa7133[0]: found at 0000:05:00.0, rev: 209, irq: 21, latency: 32, mmio: 0x73001000
[   11.015976] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
[   11.016022] saa7133[0]: board init: gpio is 200e000
[   11.172044] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   11.172057] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[   11.172067] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e2 ff 22 00 c2
[   11.172078] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff 15 0e 6c a3 ea 03 b0 8a 2f
[   11.172088] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172098] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172108] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172118] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172128] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172137] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172147] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172157] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172167] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172177] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172187] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.172197] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.264090] tuner' 0-004b: chip found @ 0x96 (saa7133[0])
[   15.316093] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[   15.316310] saa7133[0]: registered device video0 [v4l2]
[   15.316360] saa7133[0]: registered device vbi0
[   15.316406] saa7133[0]: registered device radio0
[   15.394434] saa7134 ALSA driver for DMA sound loaded
[   15.394472] saa7133[0]/alsa: saa7133[0] at 0x73001000 irq 21 registered as card -2
```

lspci
```
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
05:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
```

lsmod|grep snd
```
snd_hda_intel         557364  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  14 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
```

the script i used for making sound available is
```
 sox -q -c 2 -s -r 32000 -v 1 -t ossdsp /dev/dsp1 -t ossdsp -r 32000 /dev/dsp
```

Please help!

Regards
Prasanna Ram

---

### Post by aspartam on 2009-06-05
I having problem with tvtime. I have no sound. Everywhere says i must unmute line-in, but it doesn't solve the problem. Actually it's not the video cards prob. Because before I renew my computer I can see and hear tv in tvtime. I think the problem is in my motherboard.
In windows working.

TV Card: Leadtek Winfast TV2000 XP Expert
[http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=93](http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=93)

Mainboard: MSI K9N Neo V3
[http://www.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=171&prod_no=1244](http://www.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=171&prod_no=1244)

lspci says:
```
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8600GT (rev a1)

```

I think the biggest problem for me that there isn't simple "Multimedia controller: Conexant..."

sorry for my english...

---


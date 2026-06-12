---
title: "MythTV + Edgy = Multiple Video cards keep switching"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by Nelson-Ray on 2006-11-27
Hello,
I have an annoying problem with MythTV and Edgy. I have multiple TV tuner cards (1 Dvico FusionHDTV5 USB Gold, 1 FusionHDTV5 RT Gold, 1 Hauppauge WinTV-PVR-250) and after every reboot, the Hauppauge WinTV-PVR-250 card keeps changing dev id. It fluctuates between /dev/video0 and /dev/video1 on every reboot, so when I launch MythTV the WinTV-PVR-250 does not work. I have to kill mythbackend and re-run mythtv-setup and switch PVR-250 card from /dev/video0 to /dev/video1 and vice versa. Then the card will work fine. The HDTV cards seem fine and do not have this problem. How can I make the WinTV-PVR-250 stay on one setting? Either /dev/video0 or /dev/video1 is fine. Thanks.

---

### Post by superm1 on 2006-11-28
You can try to force the order the modules for the cards are loading by placing each into /etc/modules.  

So if your module for the dvico are lets say dvbMODULE.

then you can place this into /etc/modules
```

ivtv
dvbMODULE
```

Then /dev/video0 should be your hauggpauge and /dev/video1 your dvico.

---

### Post by Nelson-Ray on 2006-11-28
superm1 would you know how I could find out the module name for my dvico cards?

currently this is what is in my /etc/modules 

lp
sbp2
ivtv

---

### Post by superm1 on 2006-11-29
Take a look at lsmod and dmesg.  lsmod will show you all loaded modules, dmesg will hopefully indicate which of those modules is obtaining /dev/video0 and /dev/video0

---

### Post by Nelson-Ray on 2006-11-29
SuperM1 :
The modules for my dvb cards are confusing. Im not sure which ones I should add in /etc/modules. 

The FusionHDTV USB Gold (USB/Bluebird) could be : dvb_usb, dvb_usb_cxusb, dvb_core

The FusionHDTV 5 RT Gold (PCI/Blackbird) could be : cx2388x, cx88_blackbird, cx88_dvb, cx8802

The Hauppauge WinTV PVR-250 could be : ivtv (?)


Could you recommend how the modules should be ordered in /etc/modules? 


Thanks...


Relevant part of DMESG : 

[17179585.668000] usbcore: registered new driver usbhid
[17179585.668000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179585.840000] cx2388x dvb driver version 0.0.5 loaded
[17179585.840000] CORE cx88[0]: subsystem: 18ac:d500, board: DViCO FusionHDTV 5 Gold [card=31,autodetected]
[17179585.840000] TV tuner 64 at 0x1fe, Radio tuner -1 at 0x1fe
[17179585.912000] cx2388x v4l2 driver version 0.0.5 loaded
[17179586.072000] ACPI: PCI Interrupt 0000:02:08.2[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 209
[17179586.072000] cx88[0]/2: found at 0000:02:08.2, rev: 5, irq: 209, latency: 32, mmio: 0xf8000000
[17179586.072000] cx88[0]/2: cx2388x based dvb card
[17179586.380000] DVB: registering new adapter (cx88[0]).
[17179586.380000] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[17179586.380000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 209
[17179586.380000] cx88[0]/0: found at 0000:02:08.0, rev: 5, irq: 209, latency: 32, mmio: 0xf7000000
[17179586.404000] cx2388x alsa driver version 0.0.5 loaded
[17179586.528000] ts: Compaq touchscreen protocol output
[17179586.556000] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[17179586.556000] tuner 2-0061: type set to 64 (LG TDVS-H062F/TUA6034)
[17179586.584000] tuner 2-006f: chip found @ 0xde (cx88[0])
[17179586.616000] tda9887 2-0043: chip found @ 0x86 (cx88[0])
[17179586.620000] cx88[0]/0: registered device video0 [v4l2]
[17179586.620000] cx88[0]/0: registered device vbi0
[17179586.640000] gameport: EMU10K1 is pci0000:02:07.1/gameport0, io 0xde00, speed 1193kHz
[17179586.640000] ACPI: PCI Interrupt 0000:02:08.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 209
[17179586.652000] ivtv:  ==================== START INIT IVTV ====================
[17179586.652000] ivtv:  version 0.7.0 (tagged release) loading
[17179586.652000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179586.652000] ivtv:  In case of problems please include the debug info between
[17179586.652000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179586.652000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179586.680000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179586.760000] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[17179586.764000] ivtv0: Autodetected Hauppauge WinTV PVR-250 card (cx23416 based)
[17179586.764000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179586.764000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 217
[17179586.764000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179586.808000] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179587.004000] tveeprom 3-0050: Hauppauge model 32032, rev B310, serial# 7044969
[17179587.004000] tveeprom 3-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
[17179587.004000] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[17179587.004000] tveeprom 3-0050: audio processor is MSP4448 (idx 27)
[17179587.004000] tveeprom 3-0050: decoder processor is SAA7115 (idx 19)
[17179587.004000] tveeprom 3-0050: has no radio, has IR remote
[17179587.060000] saa7115 3-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179587.200000] msp3400 3-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[17179587.200000] msp3400 3-0040: MSP4448G-A2 supports radio, mode is autodetect and autoselect
[17179587.264000] cx2388x blackbird driver version 0.0.5 loaded
[17179587.336000] wlan: 0.8.4.2 (0.9.2)
[17179587.340000] ath_rate_sample: 1.2 (0.9.2)
[17179587.344000] ath_pci: 0.9.4.5 (0.9.2)
[17179587.476000] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.
[17179587.476000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17179587.508000] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold).
[17179587.508000] DVB: registering frontend 1 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[17179587.508000] input: IR-receiver inside an USB DVB receiver as /class/input/input7
[17179587.508000] dvb-usb: schedule remote query interval to 100 msecs.
[17179587.508000] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.
[17179587.508000] usbcore: registered new driver dvb_usb_cxusb
[17179587.936000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179588.152000] ivtv0: Encoder revision: 0x02050032
[17179588.152000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179588.152000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179588.156000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179588.156000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179588.156000] tuner 3-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17179588.196000] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[17179588.196000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179588.196000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 225
[17179588.204000] ivtv:  ====================  END INIT IVTV  ====================


Relevant part of lsmod : 

dvb_usb_cxusb          18564  1 
dvb_usb                21256  1 dvb_usb_cxusb
cx88_blackbird         21916  0 
ivtv                  199312  0 
tda9887                18448  0 
tuner                  54828  0 
tsdev                   9152  0 
cx88_alsa              15112  1 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_emu10k1,snd_ac97_codec,cx88_alsa,snd_pcm_oss
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
cx8800                 35212  1 cx88_blackbird
v4l2_common            17280  4 cx88_blackbird,msp3400,tuner,cx8800
compat_ioctl32          2432  1 cx8800
v4l1_compat            15108  2 ivtv,cx8800
snd                    58372  16 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_seq_device,snd_hwdep,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
cx88_dvb               14596  0 
cx8802                 13572  2 cx88_blackbird,cx88_dvb
cx88xx                 63908  5 cx88_blackbird,cx88_alsa,cx8800,cx88_dvb,cx8802
ir_common              28548  1 cx88xx
btcx_risc               6280  4 cx88_alsa,cx8800,cx8802,cx88xx
tveeprom               16144  2 ivtv,cx88xx
cx88_vp3054_i2c         5376  1 cx88_dvb
i2c_algo_bit           10376  3 ivtv,cx88xx,cx88_vp3054_i2c
mt352                   7940  2 dvb_usb_cxusb,cx88_dvb
or51132                11396  1 cx88_dvb
video_buf_dvb           7684  1 cx88_dvb
dvb_core               83368  2 dvb_usb,video_buf_dvb
video_buf              27652  7 cx88_blackbird,cx88_alsa,cx8800,cx88_dvb,cx8802,cx88xx,video_buf_dvb
nxt200x                15364  1 cx88_dvb
zl10353                 6532  1 cx88_dvb
cx24123                15112  1 cx88_dvb
lgdt330x                9500  2 dvb_usb_cxusb,cx88_dvb
cx22702                 7812  2 dvb_usb_cxusb,cx88_dvb
dvb_pll                13700  6 dvb_usb_cxusb,dvb_usb,cx88_dvb,or51132,nxt200x,cx22702
videodev               10752  4 cx88_blackbird,ivtv,cx8800,cx88xx
soundcore              11232  1 snd
i2c_nforce2             8192  0 
i2c_core               23424  20 i2c_ec,dvb_usb,msp3400,saa7115,ivtv,tda9887,tuner,cx88_dvb,cx88xx,tveeprom,i2c_algo_bit,mt352,or51132,nxt200x,zl10353,cx24123,lgdt330x,cx22702,nvidia,i2c_nforce2
usbcore               134912  6 dvb_usb_cxusb,dvb_usb,usbhid,ehci_hcd,ohci_hcd

---

### Post by superm1 on 2006-11-30
I'd say from looking at that it looks like it's dvb_usb

---


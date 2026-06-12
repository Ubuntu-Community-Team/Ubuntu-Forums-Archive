---
title: "Sound On One Tuner with Dual Tuner"
date: 2011-11-20
forum: Mythbuntu
---

### Post by downhom on 2011-11-20
I have a dual tuner setup with a Wintv-PVR-150 and a Wintv-Go.  Audio works on the Wintv-PVR-150 but not on the Wintv-Go.  I've been researching this for hours trying different fixes but none work.  Anyone have any ideas?  

Here's my setup:


```
lspci -v 

05:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 150
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at 90000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: ivtv
	Kernel modules: ivtv

05:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at 94001000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: bttv
	Kernel modules: bttv

05:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at 94000000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Bt87x
	Kernel modules: snd-bt87x


dvr@dv4:~$ dmesg | grep ivtv
[   12.480945] ivtv: Start initialization, version 1.4.2
[   12.481056] ivtv0: Initializing card 0
[   12.481063] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   12.486596] ivtv 0000:05:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.486609] ivtv0: Unreasonably low latency timer, setting to 64 (was 0)
[   12.547295] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   12.547299] ivtv0: Reopen i2c bus for IR-blaster support
[   12.579232] cx25840 14-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   12.889653] wm8775 14-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   13.392242] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   13.392428] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   13.392564] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   13.392696] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   13.392702] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   13.399261] ivtv: End initialization
[   14.528416] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   14.744161] ivtv0: Encoder revision: 0x02060039


dvr@dv4:~$ dmesg | grep bttv
[   12.549355] bttv: driver version 0.9.18 loaded
[   12.549361] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.394277] bttv: Bt8xx card found (0).
[   13.394304] bttv 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.394319] bttv 0000:05:01.0: setting latency timer to 64
[   13.394328] bttv0: Bt878 (rev 17) at 0000:05:01.0, irq: 22, latency: 64, mmio: 0x94001000
[   13.394367] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   13.394373] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   13.394408] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   13.396901] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   13.434442] bttv0: Hauppauge eeprom indicates model#44811
[   13.434446] bttv0: tuner type=21
[   13.516813] bttv0: audio absent, no audio device found!
[   13.548414] bttv0: registered device video1
[   13.548505] bttv0: registered device vbi1
[   13.548581] bttv0: registered device radio0
[   13.548606] bttv0: PLL: 28636363 => 35468950 .
[   23.200363] bttv0: PLL can sleep, using XTAL (28636363).



dvr@dv4:~$ lsmod
Module                  Size  Used by
ppdev                  12849  0 
tvaudio                32495  0 
tda7432                13070  0 
msp3400                31543  0 
tuner_simple           18151  2 
tuner_types            18998  1 tuner_simple
snd_hda_codec_realtek   254125  1 
wm8775                 12935  1 
snd_hda_intel          24262  1 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tuner                  26836  2 
snd_seq_midi           13132  0 
usbhid                 41905  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
cx25840                48785  1 
hid                    77367  1 usbhid
snd_bt87x              18727  1 
snd_seq_midi_event     14475  1 snd_seq_midi
bttv                  113026  0 
ir_rc5_decoder         12490  0 
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec,snd_bt87x
ivtv                  143882  0 
videobuf_dma_sg        18786  1 bttv
videobuf_core          25409  2 bttv,videobuf_dma_sg
cx2341x                27739  1 ivtv
ir_nec_decoder         12490  0 
btcx_risc              13400  1 bttv
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,bttv,ir_rc5_decoder,ir_nec_decoder
v4l2_common            15793  9 tvaudio,tda7432,msp3400,wm8775,tuner,cx25840,bttv,ivtv,cx2341x
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               85626  10 tvaudio,tda7432,msp3400,wm8775,tuner,cx25840,ivtv,bttv,cx2341x,v4l2_common
tveeprom               17009  2 bttv,ivtv
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32114  1 
snd                    55902  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_bt87x,snd_pcm,snd_seq,snd_timer,snd_seq_device
i915                  505108  2 
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
drm                   192226  3 i915,drm_kms_helper
snd_page_alloc         14115  3 snd_hda_intel,snd_bt87x,snd_pcm
i2c_algo_bit           13199  3 ivtv,bttv,i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  0 
uas                    17699  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e100                   36289  0 

```

---

### Post by nickrout on 2011-11-20
When you set up the bttv card, which audio device did you specify?

---


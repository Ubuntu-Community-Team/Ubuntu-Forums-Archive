---
title: "Video acquisition problem"
date: 2011-05-17
forum: Multimedia Software
---

### Post by insanegva on 2011-05-17
Hi everyone,
 

 This message because we are trying ton install a telepresence system between Geneva and Montreal for a show called GOD IS A DJ.
 

 As our first experience on a Linux system, we have installed Scenic 0.6.3 on our Ubuntu 11.04 and did all the installation commands in the terminal, as written in the installation guide.
 

 We have bought a video capture card Hauppauge BT878, with 3 composite in and 1 S-video in.
 The module to run the card is bttv, we configured it and it seems to work properly.
 

 Our problem is the following:
 

 The capture signal is perfect in acquisition programs like TVTIME or KINO but is horizontally doubled and stretched in streaming programs like SCENIC, MILHOUSE, GST-LAUNCH and CHEESE.
 The input we use is a composite PAL, 4:3, native 640x480.
 

 Would you have any idea in which direction we have to search to solve this signal distortion problem?
 

 Here you can fin our lspci report:
 

 00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01) 
 00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01) 
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) 
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) 
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) 
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) 
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) 
 00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02) 
 00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02) 
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) 
 00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02) 
 00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02) 
 00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) 
 01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870] 
 01:00.1 Audio device: ATI Technologies Inc HD48x0 audio 
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12) 
 03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) 
 03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) 
 05:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11) 
 05:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11) 
 05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) 
 05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10) 
 

 Here you can fin our lsmod report:
 

 Module                  Size  Used by 
 vivi                   19224  0  
 videobuf_vmalloc       13589  1 vivi 
 binfmt_misc            17565  1  
 parport_pc             36959  0  
 ppdev                  17113  0  
 vesafb                 13761  1  
 snd_hda_codec_hdmi     28103  1  
 snd_hda_codec_analog    98042  1  
 firewire_ohci          40370  0  
 firewire_core          62646  1 firewire_ohci 
 snd_hda_intel          33211  1  
 snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel 
 snd_hwdep              13604  1 snd_hda_codec 
 snd_seq_midi           13324  0  
 snd_rawmidi            30486  1 snd_seq_midi 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
 snd_bt87x              19128  1  
 snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_bt87x 
 usbhid                 46956  0  
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
 ir_lirc_codec          12898  0  
 lirc_dev               19232  1 ir_lirc_codec 
 ir_sony_decoder        12549  0  
 ir_jvc_decoder         12546  0  
 ir_rc6_decoder         12546  0  
 fglrx                2739144  149  
 snd_timer              29602  2 snd_seq,snd_pcm 
 asus_atk0110           17976  0  
 bttv                  128715  0  
 i2c_algo_bit           13400  1 bttv 
 snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_bt87x,snd_seq,snd_pcm,snd_seq_device,snd_timer 
 v4l2_common            17647  2 vivi,bttv 
 videodev               82052  3 vivi,bttv,v4l2_common 
 v4l2_compat_ioctl32    17078  1 videodev 
 videobuf_dma_sg        19307  1 bttv 
 ir_rc5_decoder         12546  0  
 x38_edac               13128  0  
 ir_nec_decoder         12546  0  
 videobuf_core          26135  4 vivi,videobuf_vmalloc,bttv,videobuf_dma_sg 
 serio_raw              13166  0  
 btcx_risc              13640  1 bttv 
 rc_core                26918  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,bttv,ir_rc5_decoder,ir_nec_decoder 
 tveeprom               21249  1 bttv 
 edac_core              53845  2 x38_edac 
 soundcore              12680  1 snd 
 snd_page_alloc         18529  3 snd_hda_intel,snd_bt87x,snd_pcm 
 lp                     17825  0  
 parport                46458  3 parport_pc,ppdev,lp 
 hid                    91020  1 usbhid 
 floppy                 74120  0  
 ahci                   25951  0  
 r8169                  48022  0  
 crc_itu_t              12707  1 firewire_core 
 libahci                26642  1 ahci 
 pata_jmicron           12747  0  
 sky2                   58509  0

---

### Post by insanegva on 2011-05-18
Anyone has a clue? Please save our lives! :)

---


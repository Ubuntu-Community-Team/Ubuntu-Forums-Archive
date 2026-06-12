---
title: "Broadcom BCM4306"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by fiddystorms on 2013-03-24
I never expected to struggle this mightily with Linux, but I'm fairly close to giving up completely.  I am switching from Win7 and I'm fairly proficient with a PC.  I just installed Ubuntu 12.10 & I haven't seen a hint of a wifi network available since.  I just ran several commands found on another post that might help troubleshoot.  please let me know if you can find something.  Nothing has worked and I've been at it for a few hours now.  b43-fwcutter process etc etc. nothing is working.  here's those commands:

   
**lspci -nnk | grep -iA2 net** 

 02:05.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) 
 	Subsystem: Linksys WMP54G v2 802.11g PCI Adapter [1737:0014] 
 	Kernel driver in use: b43-pci-bridge 
 -- 
 02:08.0 Ethernet controller [0200]: Intel Corporation NM10/ICH7 Family LAN Controller [8086:27dc] (rev 01) 
 	Subsystem: Hewlett-Packard Company Device [103c:2a22] 
 	Kernel driver in use: e100 
 

 

 
**lsusb** 

 Bus 001 Device 003: ID 0424:a700 Standard Microsystems Corp. 2 Port Hub 
 Bus 002 Device 002: ID 046d:c248 Logitech, Inc.  
 Bus 003 Device 002: ID 046d:c249 Logitech, Inc.  
 Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 

 
**lsmod** Module                  Size  Used by 
 snd_hda_codec_hdmi     32049  1  
 cx88_blackbird         23475  0  
 cx2341x                28284  1 cx88_blackbird 
 snd_emu10k1_synth      17294  0  
 snd_emux_synth         42804  1 snd_emu10k1_synth 
 snd_seq_virmidi        13421  1 snd_emux_synth 
 snd_seq_midi_emul      13660  1 snd_emux_synth 
 tuner_simple           22369  1  
 tuner_types            24319  1 tuner_simple 
 tda9887                13907  1  
 tda8290                22430  0  
 tea5767                13254  0  
 tuner                  27382  2  
 microcode              22804  0  
 cx8800                 38588  1 cx88_blackbird 
 snd_emu10k1           152374  3 snd_emu10k1_synth 
 b43                   369857  0  
 psmouse                95595  0  
 snd_hda_intel          33492  2  
 snd_ac97_codec        134316  1 snd_emu10k1 
 ac97_bus               12767  1 snd_ac97_codec 
 mac80211              540032  1 b43 
 cx8802                 18962  1 cx88_blackbird 
 cx88xx                 88546  3 cx88_blackbird,cx8800,cx8802 
 snd_hda_codec         134213  2 snd_hda_codec_hdmi,snd_hda_intel 
 serio_raw              13216  0  
 rc_core                22331  1 cx88xx 
 cfg80211              206797  2 b43,mac80211 
 bcma                   35657  1 b43 
 tveeprom               21250  1 cx88xx 
 v4l2_common            16421  5 cx88_blackbird,cx2341x,tuner,cx8800,cx88xx 
 snd_pcm                96668  5 snd_hda_codec_hdmi,snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_hda_codec 
 videodev              120310  6 cx88_blackbird,cx2341x,tuner,cx8800,cx88xx,v4l2_common 
 lpc_ich                17062  0  
 snd_util_mem           14118  2 snd_emux_synth,snd_emu10k1 
 snd_hwdep              17699  3 snd_emux_synth,snd_emu10k1,snd_hda_codec 
 btcx_risc              13641  3 cx8800,cx8802,cx88xx 
 videobuf_dma_sg        19306  4 cx88_blackbird,cx8800,cx8802,cx88xx 
 videobuf_core          26023  5 cx88_blackbird,cx8800,cx8802,cx88xx,videobuf_dma_sg 
 snd_seq_midi           13325  0  
 joydev                 17458  0  
 snd_rawmidi            30513  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi 
 snd_seq_midi_event     14900  2 snd_seq_virmidi,snd_seq_midi 
 snd_seq                61555  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event 
 snd_timer              29426  3 snd_emu10k1,snd_pcm,snd_seq 
 snd_seq_device         14498  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq 
 mac_hid                13206  0  
 rfcomm                 46620  0  
 bnep                   18141  2  
 parport_pc             32689  1  
 ppdev                  17074  0  
 bluetooth             209249  10 rfcomm,bnep 
 lp                     17760  0  
 parport                46346  3 parport_pc,ppdev,lp 
 snd                    78921  21 snd_hda_codec_hdmi,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_hda_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 radeon                895730  3  
 ttm                    83596  1 radeon 
 drm_kms_helper         49113  1 radeon 
 drm                   288721  5 radeon,ttm,drm_kms_helper 
 soundcore              15048  1 snd 
 snd_page_alloc         18485  3 snd_emu10k1,snd_hda_intel,snd_pcm 
 i2c_algo_bit           13414  2 cx88xx,radeon 
 usb_storage            48834  0  
 hid_generic            12541  0  
 usbhid                 46987  0  
 hid                   100411  2 hid_generic,usbhid 
 ssb                    52037  1 b43 
 e100                   40814  0  
 firewire_ohci          40402  0  
 firewire_core          64369  1 firewire_ohci 
 crc_itu_t              12708  1 firewire_core 
 

 
** iwconfig** 

 eth0      no wireless extensions. 
  
 lo        no wireless extensions. 
 
**rfkill list** 

 
**sudo iwlist scan** 

 eth0      Interface doesn't support scanning. 
  
 lo        Interface doesn't support scanning.
 

 
**dmesg | grep rt2**

---

### Post by ahallubuntu on 2013-03-24
~

---

### Post by tenmoi on 2013-03-24
Hi,

I hit the same brick wall as you are doing now until I hit this paper wall.:)
[http://www.devgems.net/?p=318](http://www.devgems.net/?p=318)

Please note: I did a clean install of xubuntu before I applied the instructions on the website. 

Cheers,

---


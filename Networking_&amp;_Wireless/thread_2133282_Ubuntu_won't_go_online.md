---
title: "Ubuntu won't go online"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by ttimmy58 on 2013-04-07
With the exception of me running Windows 7 in the dual boot I am having the [same problem]("http://ubuntuforums.org/showthread.php?t=2133048"). Here is what I get:

uname -r
3.5.0-17-generic

lspci -nnk | grep -1A2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
            Subsystem: Broadcom Corporation Device [14e4:0465]
            Kernel modules: wl, ssb
05:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
            Subsystem Lenovo Device [17aa:2074]
             Kernel driver in use: 8139too

  	 	 	 	lsusb  
Bus 001 Device 002: ID 13fd:0840 Initio Corporation  
 Bus 003 Device 002: ID 046d:c508 Logitech, Inc. Cordless Trackball  

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 

lsmod  
Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 bnep                   17707  2  
 rfcomm                 37276  0  
 bluetooth             183228  10 bnep,rfcomm  
 parport_pc             31968  0  
 ppdev                  12817  0  
 joydev                 17161  0  
 snd_hda_codec_realtek    63356  1  
 coretemp               13168  0  
 pcmcia                 39509  0  
 microcode              18209  0  
 snd_hda_intel          32515  3  
 snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13272  1 snd_hda_codec  
 snd_pcm                80163  2 snd_hda_intel,snd_hda_codec  
 lpc_ich                16925  0  
 r852                   17905  0  
 sm_common              16737  1 r852  
 nand                   49496  2 r852,sm_common  
 psmouse                84843  0  
 nand_ids                8547  1 nand  
 serio_raw              13031  0  
 mtd                    38602  2 sm_common,nand  
 nand_bch               13003  1 nand  
 bch                    17199  1 nand_bch  
 nand_ecc               13070  1 nand  
 r592                   17707  0  
 snd_seq_midi           13132  0  
 memstick               15842  1 r592  
 snd_rawmidi            25382  1 snd_seq_midi  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 yenta_socket           27095  0  
 pcmcia_rsrc            18191  1 yenta_socket  
 snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event  
 pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc  
 snd_timer              24411  2 snd_pcm,snd_seq  
 snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq  
 i915                  457161  3  
 mac_hid                13037  0  
 drm_kms_helper         45271  1 i915  
 drm                   230463  4 i915,drm_kms_helper  
 i2c_algo_bit           13197  1 i915  
 snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 wl                   2442848  0  
 video                  18847  1 i915  
 lib80211               14040  1 wl  
 soundcore              14599  1 snd  
 snd_page_alloc         14036  2 snd_hda_intel,snd_pcm  
 lp                     13299  0  
 parport                40753  3 parport_pc,ppdev,lp  
 hid_generic            12445  0  
 usbhid                 41702  0  
 hid                    82142  2 hid_generic,usbhid  
 mmc_block              26526  2  
 uas                    17556  0  
 usb_storage            39350  2  
 sdhci_pci              18155  0  
 sdhci                  27830  1 sdhci_pci  
 firewire_ohci          35521  0  
 firewire_core          57492  1 firewire_ohci  
 crc_itu_t              12627  1 firewire_core  

 8139too                23071  0  

 8139cp                 26619  0  

 

 iwconfig 

 lo        no wireless extensions.  

 

 eth0      no wireless extensions.

 

 rfkill list

---

### Post by praseodym on 2013-04-07
@ttimmy58:

Deactivate the Broadcom-STA driver, install the package linux-firmware-nonfree via cable connection and reboot.

---

### Post by Iowan on 2013-04-07
To avoid a hijacked thread, I moved your post to a new thread.

---

### Post by ttimmy58 on 2013-04-07
Thanks a bunch for the reply! How do I deactivate Broadcom-sta driver? As I am a newby I will probably need instructions getting and installing the firmware

---

### Post by ttimmy58 on 2013-04-07
Thanks!

---

### Post by wildmanne39 on 2013-04-07
Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
Thanks

---

### Post by ttimmy58 on 2013-04-08
Thanks so much! I think its almost time to ditch MS Windows

---

### Post by wildmanne39 on 2013-04-08
Your welcome!
Enjoy!!!

---


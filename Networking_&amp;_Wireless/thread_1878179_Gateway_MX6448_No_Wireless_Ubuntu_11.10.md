---
title: "Gateway MX6448 No Wireless Ubuntu 11.10"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by NotWindows on 2011-11-09
Hello Everybody!

I need help with a Gateway MX6448 which I believe has a Broadcom or Intel wireless. I am not even getting a wireless indication at the top of the screen and nothing in the settings screen to check.

I didn't know if this was the same problem in the Sticky. I did try to find out what wireless this model had and that is all I could find was either the Broadcom or Intel.

Please Help!
Thanks,
Kevin

---

### Post by wildmanne39 on 2011-11-09
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by NotWindows on 2011-11-09
Sorry somewhat new to Ubuntu and doing external code. What application do I put that into?

The newest versions of Ubuntu are way different user screen wise than what version 10 was.

Thanks,
Kevin

---

### Post by wildmanne39 on 2011-11-09
Hi, yes it is different.

Open the terminal by hitting ctrl+alt+t then copy and paste one line at a time into the terminal and paste the results here following my directions from my previous post.
Thank you

---

### Post by NotWindows on 2011-11-10
This is what I got!

  	 	 	 	 	 	  deedra@deedra-MX6448:~$ cat /etc/lsb-release; uname -a
 DISTRIB_ID=Ubuntu
 DISTRIB_RELEASE=11.10
 DISTRIB_CODENAME=oneiric
 DISTRIB_DESCRIPTION="Ubuntu 11.10"
 Linux deedra-MX6448 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
 deedra@deedra-MX6448:~$ lspci -nnk | grep -iA2 net
 02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
 	Subsystem: Gateway 2000 Device [107b:0367]
 	Kernel driver in use: sky2
 --
 05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 	Subsystem: Broadcom Corporation Device [14e4:0465]
 	Kernel modules: wl, ssb
 deedra@deedra-MX6448:~$ iwconfig
 lo        no wireless extensions.
 

 eth0      no wireless extensions.
 

 deedra@deedra-MX6448:~$ rfkill list all
 deedra@deedra-MX6448:~$ lsmod
 Module                  Size  Used by
 bnep                   17923  2  
 rfcomm                 38408  0  
 bluetooth             148839  10 bnep,rfcomm
 parport_pc             32114  0  
 ppdev                  12849  0  
 binfmt_misc            17292  1  
 joydev                 17393  0  
 snd_hda_codec_si3054    12864  1  
 snd_hda_codec_idt      60049  1  
 snd_hda_intel          24262  2  
 snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel
 snd_hwdep              13276  1 snd_hda_codec
 snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
 pcmcia                 39822  0  
 snd_seq_midi           13132  0  
 wl                   2646601  0  
 snd_rawmidi            25241  1 snd_seq_midi
 snd_seq_midi_event     14475  1 snd_seq_midi
 video                  18908  0  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
 tifm_7xx1              12937  0  
 yenta_socket           27428  0  
 pcmcia_rsrc            18367  1 yenta_socket
 pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
 radeon                925020  3  
 tifm_core              15040  1 tifm_7xx1
 ttm                    65224  1 radeon
 drm_kms_helper         32889  1 radeon
 drm                   192226  5 radeon,ttm,drm_kms_helper
 i2c_algo_bit           13199  1 radeon
 snd_timer              28932  2 snd_pcm,snd_seq
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
 snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 lib80211               14570  1 wl
 psmouse                73673  0  
 soundcore              12600  1 snd
 i2c_piix4              13093  0  
 ati_agp                13242  0  
 serio_raw              12990  0  
 k8temp                 12905  0  
 snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
 shpchp                 32356  0  
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp
 firewire_ohci          35854  0  
 firewire_core          56937  1 firewire_ohci
 crc_itu_t              12627  1 firewire_core
 pata_atiixp            12967  2  
 sky2                   49317  0 



Thanks for the help!
Kevin

---

### Post by wildmanne39 on 2011-11-10
Hi, this should get it working, please run these commands:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
When it is done installing disconnect your wired connection and reboot.
Thank you

---

### Post by NotWindows on 2011-11-10
I put the code in but on the last entry it accessed Ubuntu site I got a message saying not all archives were found.

---

### Post by wildmanne39 on 2011-11-10
Hi, please run the second command again and post all the output here:
Thank you

---


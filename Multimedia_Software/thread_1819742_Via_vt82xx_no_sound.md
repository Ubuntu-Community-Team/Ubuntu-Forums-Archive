---
title: "Via vt82xx no sound"
date: 2011-08-06
forum: Multimedia Software
---

### Post by cfirpo99 on 2011-08-06
Hello I've just installed 11.04 on a gateway mx3210.  I was going crazy trying to install the sound drivers but it looks like all the ALSA packages are already there.  when I run the alsamixer everything looks good, but no sound.  I have checked all setting and preferences to no avail.  please help thanks.

carlos@Gateway:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
carlos@Gateway:~$ 

carlos@Gateway:~$ lsmod
Module                  Size  Used by
drm                   180037  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
lib80211_crypt_tkip    17203  0 
wl                   2642531  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_via82xx            24685  3 
joydev                 17322  0 
gameport               15027  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
snd_via82xx_modem      18305  0 
snd_ac97_codec        105614  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39671  0 
psmouse                73312  0 
tifm_7xx1              12898  0 
video                  18951  0 
yenta_socket           27230  0 
serio_raw              12990  0 
i2c_viapro             12969  0 
tifm_core              15040  1 tifm_7xx1
pcmcia_rsrc            18292  1 yenta_socket
snd_page_alloc         14073  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              12600  1 snd
shpchp                 32345  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
via_rhine              27131  0 
sdhci_pci              13623  0 
pata_via               13368  2 
sdhci                  22720  1 sdhci_pci
carlos@Gateway:~$

---

### Post by cfirpo99 on 2011-08-08
here is some more info.  Alsa mixer reports that I am using Realtek alc250 rev2.  I thought the sound was also part of the VIA chipset.  I will keep trucking through the forums for now.

carlos@Gateway:~$ lsmod | grep snd
snd_via82xx            24685  0 
gameport               15027  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
snd_via82xx_modem      18305  0 
snd_ac97_codec        105614  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  9 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14073  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              12600  1 snd

---

### Post by cfirpo99 on 2011-08-08
Ok so i knew that the sound mods were loaded by running the basic checks in terminal, all I had to do was keep ticking around with the sound preferences.  BUT you need to select the right combination between the hardware tab and the output tab.  In my case the hardware profile is "analog stereo output", then on the output tab, the connector type is "analog output LFE/no amplifier.   

Im happy!

---


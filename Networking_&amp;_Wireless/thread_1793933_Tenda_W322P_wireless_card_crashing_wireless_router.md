---
title: "Tenda W322P wireless card crashing wireless router on connect"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by Dave874y on 2011-06-30
I installed a Tenda W322P wireless card in my dual-boot PC running both Windows XP and Ubuntu 11.04. The card worked straight out of the box on XP, but does not function correctly under Ubuntu. My apologies for any missing/irrelevant information, I am having to post this from the Windows boot so the Ubuntu settings are not directly available at the same time as internet access.

I followed the process detailed here [http://askubuntu.com/questions/24516/how-do-i-install-pci-wi-fi-card-tenda-w322p-rt3062](http://askubuntu.com/questions/24516/how-do-i-install-pci-wi-fi-card-tenda-w322p-rt3062) to install and configure the driver (I believe from reading other sites that this card is the Ralink RT3062 chipset), blacklisted the original RT2860 driver that was in use (couldn't even get the card to scan for wireless networks with the default driver) and restarted the interface.

Since then, sudo iwlist scan can find my wireless router but when I attempt to connect to it, it seems to enter a loop of requesting the WEP key then pausing for a while before re-requesting the key. I know I have the key value correct because it is copied and pasted from the same text file I used to copy and paste into the passkey field on the Windows boot. Attempting to connect to the router using Ubuntu also has the rather unfortunate side-effect of crashing the wireless router, killing off all other device connections until the router has been reset.

```
dave@TUBUL:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6700 XL] (rev a2)
02:00.0 Network controller: Ralink corp. Device 3062
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:05.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem

dave@TUBUL:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr c8:3a:35:c3:2c:c4  
          inet6 addr: fe80::ca3a:35ff:fec3:2cc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104159 (104.1 KB)  TX bytes:0 (0.0 B)
          Interrupt:16 

dave@TUBUL:~$ lsmod
Module                  Size  Used by
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
binfmt_misc            13213  1 
tda1004x               22897  2 
saa7134_dvb            33269  0 
videobuf_dvb           13867  1 saa7134_dvb
dvb_core               90587  1 videobuf_dvb
saa7134_alsa           18130  2 
md4                    12523  0 
nls_utf8               12493  2 
cifs                  247650  4 
tda827x                17827  4 
nvidia               9766978  38 
tda8290                22227  2 
snd_hda_codec_realtek   255820  1 
tuner                  26802  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 saa7134_alsa,snd_hda_intel,snd_hda_codec
ati_remote             13622  0 
snd_seq_midi           13132  0 
saa7134               149236  2 saa7134_dvb,saa7134_alsa
snd_rawmidi            25269  1 snd_seq_midi
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
joydev                 17322  0 
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rc_core                25760  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,saa7134,ir_nec_decoder
ppdev                  12849  0 
v4l2_common            16757  2 tuner,saa7134
rt3562sta             869831  1 
snd_timer              28659  2 snd_pcm,snd_seq
parport_pc             32111  1 
psmouse                73312  0 
videodev               75143  3 tuner,saa7134,v4l2_common
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  18 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        18747  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          25193  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               17009  1 saa7134
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
floppy                 60032  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core

dmesg contains many occurrences of the following set of messages (cut out of the full output for brevity)

[  541.999091] Driver auto reconnect to last OID_802_11_SSID setting - Dennis2860AP, len - 12
[  541.999132] CntlOidSsidProc():CNTL - 0 BSS of 1 BSS match the desire (12)SSID - Dennis2860AP
[  541.999138] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[  541.999233] SCANNING, suspend MSDU transmission ...
[  542.002317] SYNC - BBP R4 to 20MHz.l
[  542.004481] RT35xx: SwitchChannel#1(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF1, K=0x02, R=0x02
[  542.020867] hub 1-3:1.0: unable to enumerate USB device on port 2
[  542.146131] RT35xx: SwitchChannel#2(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF1, K=0x07, R=0x02
[  542.276877] hub 1-3:1.0: unable to enumerate USB device on port 2
[  542.290143] RT35xx: SwitchChannel#3(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF2, K=0x02, R=0x02
[  542.434132] RT35xx: SwitchChannel#4(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF2, K=0x07, R=0x02
[  542.532758] hub 1-3:1.0: unable to enumerate USB device on port 2
[  542.578131] RT35xx: SwitchChannel#5(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF3, K=0x02, R=0x02
[  542.722134] RT35xx: SwitchChannel#6(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF3, K=0x07, R=0x02
[  542.788764] hub 1-3:1.0: unable to enumerate USB device on port 2
[  542.866129] RT35xx: SwitchChannel#7(RF=8, Pwr0=21, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[  543.010135] RT35xx: SwitchChannel#8(RF=8, Pwr0=21, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[  543.044777] hub 1-3:1.0: unable to enumerate USB device on port 2
[  543.154134] RT35xx: SwitchChannel#9(RF=8, Pwr0=21, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[  543.298147] RT35xx: SwitchChannel#10(RF=8, Pwr0=21, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[  543.301282] hub 1-3:1.0: unable to enumerate USB device on port 2
[  543.442135] RT35xx: SwitchChannel#11(RF=8, Pwr0=21, Pwr1=21, 2T), N=0xF6, K=0x02, R=0x02
[  543.556792] hub 1-3:1.0: unable to enumerate USB device on port 2
[  543.586136] RT35xx: SwitchChannel#12(RF=8, Pwr0=21, Pwr1=21, 2T), N=0xF6, K=0x07, R=0x02
[  543.730136] RT35xx: SwitchChannel#13(RF=8, Pwr0=22, Pwr1=19, 2T), N=0xF7, K=0x02, R=0x02
[  543.813041] hub 1-3:1.0: unable to enumerate USB device on port 2
[  543.874148] RT35xx: SwitchChannel#14(RF=8, Pwr0=22, Pwr1=19, 2T), N=0xF8, K=0x04, R=0x02
[  544.018146] RT35xx: SwitchChannel#1(RF=8, Pwr0=21, Pwr1=20, 2T), N=0xF1, K=0x02, R=0x02
[  544.020310] SYNC - End of SCAN, restore to channel 1, Total BSS[01]
[  544.020315] SCAN done, resume MSDU transmission ...

dave@TUBUL:~$ sudo lshw -C network
[sudo] password for dave: 
  *-network:0             
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=rt2860 latency=32 maxlatency=4 mingnt=2
       resources: irq:16 memory:fdee0000-fdeeffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:b2:fd:83
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.100 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:ec00(size=256) memory:fdefe000-fdefe0ff memory:fdd00000-fdd0ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: c8:3a:35:c3:2c:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 multicast=yes wireless=Ralink STA

dave@TUBUL:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:25:69:8D:B1:17
                    Protocol:802.11b/g
                    ESSID:"SKY45334"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-61 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

Finally, the OS release details:
dave@TUBUL:~$ lsb_release -d
Description:	Ubuntu 11.04
dave@TUBUL:~$ uname -mr
2.6.38-8-generic i686
```

---

### Post by Dave874y on 2011-07-18
<Bump>
Sorry for the bump, but it's been almost 3 weeks now with no response, can anyone please help?

Cheers,
David.

---

### Post by Dave874y on 2011-07-22
<Bump>
I have mailed the support team at Tenda to see if they have any suggestions. They suggested I set the wireless router to unsecured and attempt to connect once again.

The connection with no encryption worked first time with no errors.

Any suggestions in the light of this new information?

Thanks,
David.

---


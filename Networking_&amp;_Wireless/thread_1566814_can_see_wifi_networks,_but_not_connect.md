---
title: "can see wifi networks, but not connect"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by Tod Brubacher on 2010-09-02
My symptom is that I see all the wifi networks around, but when I try to   connect it fails instantly or continuously prompts for authentication   (usr/pwd) if the network is secure. I'm at a loss, I've updated the   kernel to the latest stable upstream .deb and updated the whole OS   package to the latest. (it was a mini-cd install so the latest stuff   came in the d-load during install) any thoughts would be wonderful:

oh and please note that this problem occurs with both the internal   wireless card and a pcmcia card I have as well. the readouts below were   run with both active as you can see.

```
csdi@thing-0:~$ lspci -nm
00:00.0 "0600" "8086" "3575" -r04 "" ""
00:01.0 "0604" "8086" "3576" -r04 "" ""
00:1d.0 "0c03" "8086" "2482" -r02 "8086" "4541"
00:1e.0 "0604" "8086" "2448" -r42 "" ""
00:1f.0 "0601" "8086" "248c" -r02 "" ""
00:1f.1 "0101" "8086" "248a" -r02 -p8a "8086" "4541"
00:1f.5 "0401" "8086" "2485" -r02 "1013" "5959"
00:1f.6 "0703" "8086" "2486" -r02 "134d" "4c21"
01:00.0 "0300" "1002" "4c59" "1028" "00e3"
02:00.0 "0200" "10b7" "9200" -r78 "1028" "00e3"
02:01.0 "0607" "104c" "ac51" "1028" "00e3"
02:01.1 "0607" "104c" "ac51" "1028" "00e3"
02:03.0 "0607" "104c" "ac50" -r01 "12a3" "ab01"
``````
csdi@thing-0:~$ lsmod
Module                  Size  Used by
binfmt_misc             6555  1 
michael_mic             1712  8 
orinoco_cs              5082  2 
orinoco                62590  1 orinoco_cs
snd_intel8x0           26521  2 
cfg80211              149609  1 orinoco
snd_ac97_codec         99817  1 snd_intel8x0
radeon                836410  3 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                75159  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4722  0 
pcmcia                 36515  1 orinoco_cs
snd_rawmidi            17635  1 snd_seq_midi
ttm                    55536  1 radeon
drm_kms_helper         30968  1 radeon
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47110  2 snd_seq_midi,snd_seq_midi_event
joydev                  9327  0 
yenta_socket           20525  0 
snd_timer              19728  2 snd_pcm,snd_seq
pcmcia_rsrc            10276  1 yenta_socket
drm                   180325  5 radeon,ttm,drm_kms_helper
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            13897  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit            4910  1 radeon
psmouse                57362  0 
snd                    49853  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,sn  d_seq,snd_timer,snd_seq_device
lp                      7469  0 
intel_agp              25865  1 
ppdev                   5471  0 
serio_raw               4094  0 
parport_pc             27750  1 
video                  20030  0 
soundcore                880  1 snd
shpchp                 25394  0 
output                  1851  1 video
snd_page_alloc          7320  2 snd_intel8x0,snd_pcm
agpgart                32334  3 ttm,drm,intel_agp
dcdbas                  5470  0 
parport                32432  3 ppdev,lp,parport_pc
3c59x                  33860  0 
floppy                 54628  0 
mii                     4169  1 3c59x
``````
csdi@thing-0:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:46:5f:74
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x   duplex=full ip=10.0.1.9 latency=32 link=yes maxlatency=10 mingnt=10   multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=12:cool: memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:01:f4:ee:63:4f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs   driverversion=2.6.36-020636rc3-generic firmware=Lucent/Agere 9.48   link=yes multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: eth2
       serial: 00:02:2d:6b:f5:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs   driverversion=2.6.36-020636rc3-generic firmware=Lucent/Agere 9.48   link=no multicast=yes wireless=IEEE 802.11b
``````
csdi@thing-0:~$  lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 7:cool:
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
```

---


---
title: "AR9287 Wireless Network Adapter (PCI-Express) not working in 11.04"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by rofilio47 on 2011-12-07
Hi, 

I have a Gateway NV55S13u, with the above mentioned wireless card & i can't get the darn thing to work. I've tried downloading drivers & even switched from Network Manager to Wicd, and nothing works. I need help. What should I do?

---

### Post by josephmills on 2011-12-07
> **rofilio47 said:**
> Hi, 

I have a Gateway NV55S13u, with the above mentioned wireless card & i can't get the darn thing to work. I've tried downloading drivers & even switched from Network Manager to Wicd, and nothing works. I need help. What should I do?
allright lets take a deeper look at this could you please open your terminal (ctrl+alt+t) then enter these commands and paste here. (if you do not have ethernet to the box save cd/usb/whatever as a .txt file and move over to woprking box to paste  ) 

```
sudo lshw -c network && lspci -nn && lsmod && lsusb && rfkill list all 
``` 

thanks !

---

### Post by rofilio47 on 2011-12-07
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: b8:70:f4:f0:35:a7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=192.168.0.13 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:f0030000-f003ffff memory:f0040000-f004ffff memory:f0050000-f00507ff
  *-network UNCLAIMED
       description: Network controller
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f010ffff
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1705]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9641]
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1714]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:1709]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Device [1022:170a]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7801]
00:13.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 13)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:14.5 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7809] (rev 11)
00:16.0 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:16.2 USB Controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
01:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
01:00.2 System peripheral [0880]: Broadcom Corporation Device [14e4:16be] (rev 10)
01:00.3 System peripheral [0880]: Broadcom Corporation Device [14e4:16bf] (rev 10)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   255882  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
uvcvideo               66851  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               75143  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ndiswrapper           192828  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13666  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2434640  98 
i2c_piix4              13095  0 
psmouse                59039  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                12951  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
tg3                   131476  0 
sdhci_pci              13623  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1bcf:288a Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by rofilio47 on 2011-12-08
Is there anyone that can help me get this problem solved?

---

### Post by pastalavista on 2011-12-08
Try this code in terminal```
sudo rmmod ndiswrapper && sudo modprobe ath9k
```

---

### Post by rofilio47 on 2011-12-08
Ok that allowed me to see the networks, choose one & attempt to connect. BUT, no connection is made. Is there something going on with the ip address? How do I trouble shoot?

---


---
title: "Remote not working"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by paulngwen on 2007-06-24
have MythTV installed on Fiesty and everything is working except the remote. The card is working properly to record and everything works in MythTV but the remote just gets no response at all. I've searched the ubuntuforums.org and ubuntu help and found several similar problems but none of their fixes have made a dent - still no response from the remote. When using the irw command there is nothing that happens at all on the screen. Any help to point me in the right direction would be greatly appreciated. I've only been working with Ubuntu for about two months now so I am still a newbie. My apologies if this is posted in the wrong place. Thanks for any help anyone can provide. Attached is the IVTV part of the dmesg response.


[   21.080000] ivtv:  ==================== START INIT IVTV ====================
[   21.080000] ivtv:  version 0.10.1 (tagged release) loading
[   21.080000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   21.080000] ivtv:  In case of problems please include the debug info between
[   21.080000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   21.080000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   21.080000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   21.080000] PCI: Enabling device 0000:00:0f.0 (0014 -> 0016)
[   21.080000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   21.200000] parport_pc: VIA parallel port: io=0x3BC, irq=7
[   21.536000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.548000] Linux agpgart interface v0.102 (c) Dave Jones
[   22.136000] input: PC Speaker as /class/input/input2
[   22.204000] logips2pp: Detected unknown logitech mouse model 127
[   22.664000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   23.408000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   23.624000] ivtv0: Encoder revision: 0x02060039
[   23.708000] tveeprom 0-0050: Hauppauge model 32062, rev B185, serial# 2869305
[   23.708000] tveeprom 0-0050: tuner model is TCL 2002N 6A (idx 85, type 50)
[   23.708000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   23.708000] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[   23.708000] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   23.708000] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   23.708000] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   23.756000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   23.856000] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   24.080000] msp3400 0-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #0)
[   24.080000] msp3400 0-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[   24.084000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   24.084000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   24.084000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   24.084000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   24.084000] tuner 0-0061: type set to 50 (TCL 2002N)
[   24.500000] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[   24.500000] ivtv:  ====================  END INIT IVTV  ====================
=====

---

### Post by mjezell on 2007-07-07
I don't have a specific solution to your problem since I'm having the same trouble.  First, looking at your dmesg log there is a comment that you have no IR transmitter.  Have you installed lirc?  Once I had lirc installed I was able to get the remote to respond to the command line using irw.  Still haven't got the remote to respond to MythTv.  Try this link for more info on lirc with fiesty - [https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty")

---


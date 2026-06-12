---
title: "Joybook s53 microphone doesn't work and problem whith sound ubuntu 9.10"
date: 2010-02-16
forum: Multimedia Software
---

### Post by coreoatetosi on 2010-02-16
Hi,
on my Joybook s53, whith last versione of Ubuntu (karmik) and the last version of the alsa modules, i have 2 problem with sound:


 1) the greater one, is that the microphone doesn't work. I've update the alsa driver to the last version, I've check the sound level but nothing...


 2)the output channel are wrong, for example if i use the audio balance, and I set only the right channel, the left channel is not muted, but change the euqualization of the sound.


 Here the the sreenshot of alsamixer
[URL="http://www.allfreeportal.com/imghost/images/74531Schermata.png"]http://www.allfreeportal.com/imghost/images/74531Schermata.png 
[/URL]


You can see that are present the "surround" channel and the "centre cannel", but this audio card is not a sourround card, so this channel should not be exists.
And the microphone has two channel "left" and "right" (i can see it with pulse audio monitor) and one of this channel is relatet to che "sourround" channel because if I increase the level of this channel, also the recognized volume level of the microphone change.


I think that Alsa uses wrong drivers, but I don't know how to solve it.


 Here the results of "lspci" :
 

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


and the result of "sudo lshw -C sound" is:


*-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:b0040800-   b00409ff memory:b0040400-b00404ff






 thanks Alex

---


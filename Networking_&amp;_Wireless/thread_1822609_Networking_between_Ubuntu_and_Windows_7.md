---
title: "Networking between Ubuntu and Windows 7"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by lezzi on 2011-08-10
Hello guys. I am a complete Ubuntu newbie. My old desktop never managed to finish its system recovery properly and so I couldn't even boot it properly. My friend suggested that I try to run Ubuntu on it from a CD. So now I have Ubuntu 11.04 32-bit running on my desktop. It is not running alongside Windows, only the Ubuntu OS is present. Now this is my situation. I have a laptop (Windows 7) that connects wirelessly to the Internet. I want to establish a WIRED connection between my laptop and desktop with an ethernet cable in order to download software from the Ubuntu Software Center and to transfer some large files. I need for someone to explain to me step-by-step everything that I have to do on my laptop and desktop in order to establish this connection. I have tried to manually enter IP/gateway/dns/etc., information but I was unable to establish a connection. I am also not sure if I was entering the correct information. I would really appreciate it if someone could help me through this process. Below I've included information on both machines, as well as some output from the ubuntu terminal.
Laptop: Toshiba Satellite A505 (Windows 7 64-bit)
             Network adapters: Realtek PCIe FE Family Controller
                              Realtek Wireless LAN 802.11 PCI-e
Desktop SPECS: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00196251&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=468379](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00196251&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=468379)

Thanks for your help!

```
anup@Anup-Ubuntu:~$ lspci -nn  
 00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)  
 00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)  
 00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)  
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)  
 00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)  
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)  
 00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)  
 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600] [10de:0141] (rev a2)  
 03:01.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)  
 03:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)  
 03:04.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)  
 anup@Anup-Ubuntu:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17335  1  
 fat                    55505  1 vfat  
 usb_storage            43946  1  
 uas                    17676  0  
 snd_hda_codec_realtek   255820  1  
 snd_hda_intel          24140  2  
 snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13274  1 snd_hda_codec  
 nouveau               621970  2  
 snd_pcm                80244  2 snd_hda_intel,snd_hda_codec  
 binfmt_misc            13213  1  
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 ppdev                  12849  0  
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              28659  2 snd_pcm,snd_seq  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq  
 ttm                    65184  1 nouveau 
 parport_pc             32111  1  
 drm_kms_helper         40745  1 nouveau 
 snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm                   180037  4 nouveau,ttm,drm_kms_helper  
 psmouse                73312  0  
 serio_raw              12990  0  
 i2c_algo_bit           13184  1 nouveau 
 video                  18951  1 nouveau 
 soundcore              12600  1 snd  
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm  
 lp                     13349  0  
 parport                36746  3 ppdev,parport_pc,lp  
 usbhid                 41704  0  
 8139too                23208  0  
 hid                    77084  1 usbhid  
 8139cp                 22497  0  
 firewire_ohci          31504  0  
 firewire_core          56138  1 firewire_ohci  
 crc_itu_t              12627  1 firewire_core  
 anup@Anup-Ubuntu:~$ rfkill list all  
 anup@Anup-Ubuntu:~$ sudo lshw -c network  
 [sudo] password for anup:  
   *-network                
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 2  
        bus info: pci@0000:03:02.0  
        logical name: eth0  
        version: 10  
        serial: 00:13:d4:49:66:73  
        size: 10Mbit/s  
        capacity: 100Mbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s  
        resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff  
 anup@Anup-Ubuntu:~$  

```

---

### Post by spegru on 2011-08-15
I'm not 100% sure about all the steps but I'd suggest that since you want a direct connection between 2 PCs you should manually allocate a fixed ip address to both and then either share the files or FTP them between them

---

### Post by imortalninja161 on 2011-08-15
hay man imma do the best i can to help 
First of all imma need to post some results of 

```

ipconfig /all
```specificallythe Default gateway ip address 

and the ipv4 address for the first adapter you see in the list

i also dont understand some information about the Topology  

is it a USB dongle connected to your laptop
or is it wireless connected to a router thanks.

Thanks 
imortalninja161

---


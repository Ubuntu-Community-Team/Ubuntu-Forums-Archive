---
title: "Wireless Problem"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by derricklongley on 2010-10-13
I'm new to this so here are the results of several different checks. Any help would be great, thanks.

                     
[LIST=1]
[*]Acer 4520 laptop with 10.10 Ubuntu     Netbook
[/LIST]
 



 lspci  
 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)  
 00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)  
 00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)  
 00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)  
 00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)  
 00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)  
 00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)  
 00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)  
 00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)  
 00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)  
 00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)  
 00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)  
 00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)  
 00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)  
 00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)  
 00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)  
 00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)  
 01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)  
 01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)  
 01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)  
 07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
 

 

 

 lsusb  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 006: ID 090c:1000 Feiya Technology Corp. Flash Drive  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

 

 ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:1e:68:13:0a:37   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:42 Base address:0xe000  
 

 eth1      Link encap:Ethernet  HWaddr 00:1f:3a:3f:60:52   
           inet6 addr: fe80::21f:3aff:fe3f:6052/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:19  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:420 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:420 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:37596 (37.5 KB)  TX bytes:37596 (37.5 KB)  
 

 iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 eth1      IEEE 802.11  Access Point: Not-Associated    
           Link Quality:5  Signal level:0  Noise level:0  
           Rx invalid nwid:0  invalid crypt:0  invalid misc:0  
 

 lsmod  
 Module                  Size  Used by  
 nls_iso8859_1           3261  1  
 nls_cp437               4931  1  
 vfat                    9201  1  
 fat                    48240  1 vfat  
 cdc_ether               4052  0  
 usbnet                 17312  1 cdc_ether  
 mii                     4425  1 usbnet  
 nls_utf8                1069  0  
 udf                    79366  0  
 usb_storage            40172  1  
 parport_pc             26058  0  
 ppdev                   5556  0  
 snd_hda_codec_realtek   217980  1  
 binfmt_misc             6599  1  
 nvidia               7088432  27  
 joydev                  8735  0  
 snd_hda_intel          22107  2  
 snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               5040  1 snd_hda_codec  
 snd_pcm                71475  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi            4588  0  
 snd_rawmidi            17783  1 snd_seq_midi  
 snd_seq_midi_event      6047  1 snd_seq_midi  
 snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event  
 lib80211_crypt_tkip     7736  0  
 snd_timer              19067  2 snd_pcm,snd_seq  
 snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq  
 ndiswrapper           184207  0  
 wl                   1959533  0  
 video                  18712  0  
 r852                    9536  0  
 sm_common               3285  1 r852  
 nand                   34905  2 r852,sm_common  
 nand_ids                2903  1 nand  
 nand_ecc                3938  1 nand  
 output                  1883  1 video  
 snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 uvcvideo               55847  0  
 mtd                    18877  2 sm_common,nand  
 lib80211                5058  2 lib80211_crypt_tkip,wl  
 videodev               43098  1 uvcvideo  
 v4l1_compat            13359  2 uvcvideo,videodev  
 agpgart                32011  1 nvidia  
 soundcore                880  1 snd  
 snd_page_alloc          7120  2 snd_hda_intel,snd_pcm  
 k8temp                  3132  0  
 i2c_nforce2             5179  0  
 psmouse                59033  0  
 lp                      7342  0  
 serio_raw               4022  0  
 parport                31492  3 parport_pc,ppdev,lp  
 firewire_ohci          21106  0  
 sdhci_pci               6339  0  
 ahci                   19013  0  
 firewire_core          46643  1 firewire_ohci  
 sdhci                  15890  1 sdhci_pci  
 crc_itu_t               1383  2 udf,firewire_core  
 led_class               2633  1 sdhci  
 libahci                21667  3 ahci  
 forcedeth              49433  0  
 pata_amd                8746  0  
 

 

 

 

 sudo lshw -C network  
 

 *-network                
        description: Ethernet interface  
        product: MCP67 Ethernet  
        vendor: nVidia Corporation  
        physical id: a  
        bus info: pci@0000:00:0a.0  
        logical name: eth0  
        version: a2  
        serial: 00:1e:68:13:0a:37  
        capacity: 1GB/s  
        width: 32 bits  
        clock: 66MHz  
        capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII  
        resources: irq:42 memory:f4488000-f4488fff ioport:30f8(size=8) memory:f4489c00-f4489cff memory:f4489800-f448980f  
   *-network  
        description: Wireless interface  
        product: BCM4311 802.11b/g WLAN  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:07:00.0  
        logical name: eth1  
        version: 01  
        serial: 00:1f:3a:3f:60:52  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg  
        resources: irq:19 memory:f4000000-f4003fff  
 

 

 

 iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 eth1      Interface doesn't support scanning.  
 

 

 

  uname -mr  
 2.6.35-22-generic i686  
 

 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by PaulReaver on 2010-10-13
right so you've got a broadcom BCM4311

two minutes....

---

### Post by PaulReaver on 2010-10-13
if you can somehow get this puter connected to the internet,  cable mobile broadband etc...

using synaptic install broadcom-sta-common
then restart your pc.

wifi 'should' (fingers crossed) now work :D

---

### Post by derricklongley on 2010-10-13
I installed it, but I don't see any changes. I was reading how easy it should be with the Network Manager, but I'm not seeing any networks to connect to at all. I'm trying to connect to a secured network, but I'm not even seeing unsecured networks in my vicinity.

---

### Post by derricklongley on 2010-10-15
still haven't connected and I tried WCID, but it has the same issue where it isn't finding any networks? Anyone have a clue as to what could be the problem?

---

### Post by derricklongley on 2010-10-16
I reinstalled 10.10 and it still didn't work even after making some changes. Then I downloaded and installed 10.4 and went to system>administration> hardware then when it showed the two Braodcom drivers weren't installed I activated them rebooted and  it found my wireless networks.

---

### Post by ArgusVision on 2010-10-16
posted to the other thread by you on the same subject.

[http://ubuntuforums.org/showthread.php?t=1592774&page=4](http://ubuntuforums.org/showthread.php?t=1592774&page=4)

---

### Post by johnnytm on 2010-10-16
10.10 doesn't list the driver under the same hardware tab that 10.04 did. they have changed it to system-->administration-->additional drivers. Lists the same 2 options there that 10.04 had, but you should only use 1 of them. I have always used just the STA driver and have never had problems with wireless working under either 10.10 or 10.04 and the same broadcom wireless card.

---


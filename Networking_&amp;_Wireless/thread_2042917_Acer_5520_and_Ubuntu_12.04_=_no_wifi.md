---
title: "Acer 5520 and Ubuntu 12.04 = no wifi"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by Imabus on 2012-08-15
Hello all, 

I have just taken a dead laptop back into the world of the living, and there may still be some hardware issues so possibly the software is not to blame, but perhaps you can help....

I have had a dead hard drive, totally wiped, instead of buying windows i have opted to leap into the world of Ubuntu, so i am very new at this. But the point to be made is i do not have a windows system to boot and im aware there may be an easy (ish) fix if i could. 

I have an Acer Aspire 5520 and just installed Ubuntu 12.04 and i find my wifi does not work, it seems that it is not even nearly working as i cant even see any wifi networks. i have a button on the keyboard to turn on/off wifi but it does nothing and i have found many posts from other members who have had the same issue but none of the solutions on those threads have solved my problem. 

let me know what other info you need to be able to even begin to help, and hints towards a fix would be fantastic! 

many thanks

---

### Post by praseodym on 2012-08-15
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:

```
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Imabus on 2012-08-15
Hi praseodym

Thanks for the responce, in answer  ... 

lspci -nnk 

imabus@imabus-Aspire-5520:~$ lspci -nnk
00:00.0 RAM memory [0500]: NVIDIA Corporation MCP67 Memory Controller [10de:0547] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP67 SMBus [10de:0542] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP67 Memory Controller [10de:0541] (rev a2)
    Subsystem: NVIDIA Corporation Device [10de:cb84]
00:01.3 Co-processor [0b40]: NVIDIA Corporation MCP67 Co-processor [10de:0543] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: ohci_hcd
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: ehci_hcd
00:04.0 USB controller [0c03]: NVIDIA Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: ohci_hcd
00:04.1 USB controller [0c03]: NVIDIA Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: ehci_hcd
00:06.0 IDE interface [0101]: NVIDIA Corporation MCP67 IDE Controller [10de:0560] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd
00:07.0 Audio device [0403]: NVIDIA Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:08.0 PCI bridge [0604]: NVIDIA Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: NVIDIA Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: ahci
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
00:0c.0 PCI bridge [0604]: NVIDIA Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0d.0 PCI bridge [0604]: NVIDIA Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:12.0 VGA compatible controller [0300]: NVIDIA Corporation C67 [GeForce 7000M / nForce 610M] [10de:0533] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_173, nvidia_current_updates, nouveau, nvidiafb
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:04.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
01:04.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
01:04.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: r592
    Kernel modules: r592
01:04.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: r852
    Kernel modules: r852
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel modules: ssb

imabus@imabus-Aspire-5520:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
imabus@imabus-Aspire-5520:~$ 

imabus@imabus-Aspire-5520:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
snd_hda_codec_realtek   174222  1 
joydev                 17393  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
bnep                   17830  2 
snd_rawmidi            25424  1 snd_seq_midi
parport_pc             32114  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10971098  43 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                72919  0 
r592                   17808  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
serio_raw              13027  0 
memstick               15857  1 r592
nand_ecc               13070  1 nand
k8temp                 12905  0 
i2c_nforce2            12906  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
rc_rc6_mce             12454  0 
ene_ir                 18019  0 
wmi                    18744  1 acer_wmi
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
mac_hid                13077  0 
video                  19068  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci                  28241  1 sdhci_pci
forcedeth              58096  0 
pata_amd               13750  0 
imabus@imabus-Aspire-5520:~$ 

imabus@imabus-Aspire-5520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

imabus@imabus-Aspire-5520:~$ 

imabus@imabus-Aspire-5520:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
imabus@imabus-Aspire-5520:~$ 


Hope that all makes sense to you :)

---

### Post by chili555 on 2012-08-16
Please hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
```Reboot and give us your report.

---

### Post by Imabus on 2012-08-16
Hi Chili555

ran the code and all went well no errors or warnings, 

rebooted and unplugged ethernet and no connections on startup

The wireless symbol in the  toolbar top right is showing no animation or sign of even trying to do anything.

---

### Post by chili555 on 2012-08-16
Let's see what's going on under the hood. Please run and post:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

---

### Post by Imabus on 2012-08-16
> **chili555 said:**
> Let's see what's going on under the hood. Please run and post:```
sudo modprobe b43
dmesg | grep b43
```Thanks.

Hi Chilli 

heres the output ... 

```
 imabus@imabus-Aspire-5520:~$ sudo modprobe b43
[sudo] password for imabus: 
imabus@imabus-Aspire-5520:~$ dmesg | grep b43
[  561.833131] b43-pci-bridge 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[  561.833143] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[  562.075597] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  562.189529] Registered led device: b43-phy0::tx
[  562.189600] Registered led device: b43-phy0::rx
[  562.189678] Registered led device: b43-phy0::radio
[  562.552082] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
imabus@imabus-Aspire-5520:~$ 

```

---

### Post by chili555 on 2012-08-16
Looks perfect! Now is there a wireless interface?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```When you click the Network manager icon, do you see your network? Can you click it and connect?

---

### Post by Imabus on 2012-08-16
There is ... it does .... 

```
 imabus@imabus-Aspire-5520:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

imabus@imabus-Aspire-5520:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 1C:BD:B9:BA:37:B4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Piglet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d3c9d93144
                    Extra: Last beacon: 632ms ago
                    IE: Unknown: 00065069676C6574
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070700000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700103755AF1764269E61031D1CBDB9BA37B410210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 02 - Address: 94:44:52:06:BE:A9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Jeanie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d7413f6183
                    Extra: Last beacon: 628ms ago
                    IE: Unknown: 00064A65616E6965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DDA00050F204104A00011010440001021041000100103B000103104700100000000000000001100094445206BEA91021001242656C6B696E20436F72706F726174696F6E1023000C463544373233342D3420763510240007352E30302E31321042000E31323934333732333433323336301054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084
          Cell 03 - Address: 02:24:17:E4:F9:D7
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ea99ac1fe4
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050402030100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:11:50:FD:B7:13
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"bubble"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c7c4f6541
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 0006627562626C65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD07000C4301000000
          Cell 05 - Address: 74:44:01:5E:FA:6A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6154066"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000590d08a186
                    Extra: Last beacon: 268ms ago
                    IE: Unknown: 001276697267696E6D6564696136313534303636
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001F00000000000000000000000000000000000000
                    IE: Unknown: DD7E0050F204104A0001101044000102103B000103104700100ACD29355CBA4D9CA52A7DA3C6351659102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180205F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 02:24:17:E4:F9:D6
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ea99ac19a0
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050402030100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 07 - Address: F0:7D:68:44:30:08
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"GeorgeHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025f8a5f16b
                    Extra: Last beacon: 840ms ago
                    IE: Unknown: 000A47656F726765486F6D65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010008127A
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 08 - Address: A0:21:B7:CD:AE:2E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Heaven"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024b1d6441a1
                    Extra: Last beacon: 1144ms ago
                    IE: Unknown: 000648656176656E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 09 - Address: 1C:BD:B9:C8:74:1C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"sheragim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master

imabus@imabus-Aspire-5520:~$ 
```

the networks are showing now and i have connected!! 

wow beyond wow .... what was wrong? 

thankyou so much for that fix!

---

### Post by Imabus on 2012-08-16
should i reboot now or do i need to do anything to make the fix permanent? 

also, do you know anything about bluetooth or should i start a new thread? 

Thanks a hundred times again!

---

### Post by chili555 on 2012-08-16
> **Imabus said:**
> should i reboot now or do i need to do anything to make the fix permanent? 

also, do you know anything about bluetooth or should i start a new thread? 

Thanks a hundred times again!You should start a new thread for your bluetooth.

I think you're all set but if, after reboot, it isn't working, post back.

---

### Post by Imabus on 2012-08-17
new thread started for bluetooth....

i rebooted and wifi was off again, but running the two lines of code you first instructed bring it back so not to bad :)

---

### Post by praseodym on 2012-08-17
This means, you just need to force the driver being loaded at boot-up:

```
echo b43 | sudo tee -a /etc/modules
```

---

### Post by Imabus on 2012-08-17
That worked beautifully! Wifi is on even when I reboot now :) thanks all for your help! I'll mark this solved now :)

---

### Post by amrdarwish1975 on 2012-10-04
> **chili555 said:**
> Please hook up the ethernet and do:```
sudo apt-get install linux-firmware-nonfree
```Reboot and give us your report.

It works perfectly for me right after above step .. many thanks :)

---

### Post by amrdarwish1975 on 2012-10-04
wifi is fine just after this step .. many thanks :-)

---


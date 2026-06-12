---
title: "Ubuntu Wireless NetGear Router"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by bcbrown on 2011-09-08
Can someone help me set up Ubuntu 11.04 for wireless connectivity? I am using a NETGEAR wireless router...

---

### Post by praseodym on 2011-09-08
Hello,

please show the following terminal-outputs:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
What kind of computer is that?

---

### Post by bcbrown on 2011-09-08
I am using a Dell Vostro 1500 Intel Core 2 Duo

brandon@ubuntu:~$ lspci -nnk | grep -iA2 net 
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
    Subsystem: Dell Device [1028:0228] 
    Kernel driver in use: b44 
-- 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007] 
    Kernel driver in use: b43-pci-bridge 

brandon@ubuntu:~$ lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

brandon@ubuntu:~$ lsmod 
Module                  Size  Used by 
usbhid                 41704  0  
hid                    77084  1 usbhid 
binfmt_misc            13213  1  
parport_pc             32111  0  
ppdev                  12849  0  
snd_hda_codec_idt      60537  1  
nvidia               7098106  38  
snd_hda_intel          24113  4  
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
b44                    35301  0  
snd_hwdep              13274  1 snd_hda_codec 
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec 
ssb                    45942  1 b44 
snd_seq_midi           13132  0  
snd_rawmidi            25269  1 snd_seq_midi 
joydev                 17322  0  
wl                   2642531  0  
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28659  2 snd_pcm,snd_seq 
r852                   17878  0  
sm_common              16737  1 r852 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
nand                   49822  2 r852,sm_common 
dell_laptop            13515  0  
nand_ids                8547  1 nand 
dell_wmi               12601  0  
nand_ecc               13070  1 nand 
snd                    55295  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
dcdbas                 14054  1 dell_laptop 
psmouse                73312  0  
soundcore              12600  1 snd 
sparse_keymap          13666  1 dell_wmi 
mtd                    26720  2 sm_common,nand 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
serio_raw              12990  0  
lib80211               14570  1 wl 
lp                     13349  0  
video                  18951  0  
parport                36746  3 parport_pc,ppdev,lp 
sdhci_pci              13623  0  
firewire_ohci          31504  0  
firewire_core          56138  1 firewire_ohci 
sdhci                  22720  1 sdhci_pci 
crc_itu_t              12627  1 firewire_core 

brandon@ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 

brandon@ubuntu:~$ rfkill list 
0: dell-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no

---

### Post by praseodym on 2011-09-08
Strange: "lspci" shows the b43 driver, but the Broadcom-STA-driver is loaded. For your card the b43 should work, but the firmware has to be installed. Deactivate the STA-driver in "additional drivers" and install the needed files:

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer modemmanager
```
I added the package modemmanager because its missing per default in Lubuntu. Reboot if neccessary.

---

### Post by bcbrown on 2011-09-08
I have deactivate the STA-driver in "additional drivers" and install the needed files.


   	 	 	 	 	 	  brandon@ubuntu:~$ sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer modemmanager 
 [sudo] password for brandon:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following package was automatically installed and is no longer required: 
   wine1.0-gecko 
 Use 'apt-get autoremove' to remove them. 
 The following NEW packages will be installed: 
   b43-fwcutter firmware-b43-installer 
 0 upgraded, 2 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded. 
 Need to get 258 kB of archives. 
 After this operation, 131 kB of additional disk space will be used. 
 Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main b43-fwcutter i386 1:013-3 [14.6 kB] 
 Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse firmware-b43-installer all 4.150.10.5-5 [3,632 B] 
 Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main modemmanager i386 0.4+git.20110124t203624.00b6cce-2ubuntu1 [240 kB] 
 Fetched 258 kB in 18s (14.0 kB/s)                                               
 Selecting previously deselected package b43-fwcutter. 
 (Reading database ... 205452 files and directories currently installed.) 
 Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ... 
 Selecting previously deselected package firmware-b43-installer. 
 Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ... 
 Preparing to replace modemmanager 0.4+git.20110124t203624.00b6cce-2ubuntu1 (using .../modemmanager_0.4+git.20110124t203624.00b6cce-2ubuntu1_i386.deb) ... 
 Unpacking replacement modemmanager ... 
 Processing triggers for man-db ... 
 Processing triggers for hicolor-icon-theme ... 
 Setting up b43-fwcutter (1:013-3) ... 
 Setting up firmware-b43-installer (4.150.10.5-5) ... 
 --2011-09-08 16:06:44--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
 Resolving mirror2.openwrt.org... 46.4.11.11 
 Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 3888794 (3.7M) [application/x-bzip2] 
 Saving to: `broadcom-wl-4.150.10.5.tar.bz2' 
  
 100%[======================================>] 3,888,794   30.5K/s   in 31s      
  
 2011-09-08 16:07:16 (124 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794] 
  
 This file is recognised as: 
   ID         :  FW13 
   filename   :  wl_apsta_mimo.o 
   version    :  410.2160 
   MD5        :  cb8d70972b885b1f8883b943c0261a3c 
 Extracting b43/pcm5.fw 
 Extracting b43/ucode15.fw 
 Extracting b43/ucode14.fw 
 Extracting b43/ucode13.fw 
 Extracting b43/ucode11.fw 
 Extracting b43/ucode9.fw 
 Extracting b43/ucode5.fw 
 Extracting b43/lp0bsinitvals15.fw 
 Extracting b43/lp0initvals15.fw 
 Extracting b43/lp0bsinitvals14.fw 
 Extracting b43/lp0initvals14.fw 
 Extracting b43/a0g1bsinitvals13.fw 
 Extracting b43/a0g1initvals13.fw 
 Extracting b43/b0g0bsinitvals13.fw 
 Extracting b43/b0g0initvals13.fw 
 Extracting b43/lp0bsinitvals13.fw 
 Extracting b43/lp0initvals13.fw 
 Extracting b43/n0absinitvals11.fw 
 Extracting b43/n0bsinitvals11.fw 
 Extracting b43/n0initvals11.fw 
 Extracting b43/a0g1bsinitvals9.fw 
 Extracting b43/a0g0bsinitvals9.fw 
 Extracting b43/a0g1initvals9.fw 
 Extracting b43/a0g0initvals9.fw 
 Extracting b43/b0g0bsinitvals9.fw 
 Extracting b43/b0g0initvals9.fw 
 Extracting b43/a0g1bsinitvals5.fw 
 Extracting b43/a0g0bsinitvals5.fw 
 Extracting b43/a0g1initvals5.fw 
 Extracting b43/a0g0initvals5.fw 
 Extracting b43/b0g0bsinitvals5.fw 
 Extracting b43/b0g0initvals5.fw 
 Setting up modemmanager (0.4+git.20110124t203624.00b6cce-2ubuntu1) ... 
 brandon@ubuntu:~$

---

### Post by praseodym on 2011-09-08
Ok, reboot and check:

```
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | grep b43
iwlist chan
```

---

### Post by bcbrown on 2011-09-08
brandon@ubuntu:~$ lsmod 
 Module                  Size  Used by 
 binfmt_misc            13213  1  
 parport_pc             32111  0  
 ppdev                  12849  0  
 snd_hda_codec_idt      60537  1  
 snd_hda_intel          24113  2  
 snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
 arc4                   12473  2  
 nvidia               7098106  38  
 snd_hwdep              13274  1 snd_hda_codec 
 snd_pcm                80042  2 snd_hda_intel,snd_hda_codec 
 b43                   296610  0  
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi 
 snd_seq_midi_event     14475  1 snd_seq_midi 
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
 mac80211              257001  1 b43 
 joydev                 17322  0  
 snd_timer              28659  2 snd_pcm,snd_seq 
 r852                   17878  0  
 dell_laptop            13515  0  
 dell_wmi               12601  0  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
 sm_common              16737  1 r852 
 nand                   49822  2 r852,sm_common 
 nand_ids                8547  1 nand 
 cfg80211              156212  2 b43,mac80211 
 sparse_keymap          13666  1 dell_wmi 
 dcdbas                 14054  1 dell_laptop 
 snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 nand_ecc               13070  1 nand 
 psmouse                73312  0  
 mtd                    26720  2 sm_common,nand 
 serio_raw              12990  0  
 soundcore              12600  1 snd 
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
 video                  18951  0  
 lp                     13349  0  
 parport                36746  3 parport_pc,ppdev,lp 
 b44                    35301  0  
 sdhci_pci              13623  0  
 usbhid                 41704  0  
 firewire_ohci          31504  0  
 sdhci                  22720  1 sdhci_pci 
 firewire_core          56138  1 firewire_ohci 
 crc_itu_t              12627  1 firewire_core 
 hid                    77084  1 usbhid 
 ssb                    45942  2 b43,b44 
 brandon@ubuntu:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wlan0     IEEE 802.11bg  ESSID off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thrff   Fragment thrf 
           Power Management off 
            
 brandon@ubuntu:~$ sudo iwlist scan 
 [sudo] password for brandon:  
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 wlan0     Scan completed : 
           Cell 01 - Address: 00:24:B2:E1:3A:ED 
                     Channel:2 
                     Frequency:2.417 GHz (Channel 2) 
                     Quality=59/70  Signal level=-51 dBm   
                     Encryption keyon 
                     ESSID:"ambibambiland" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000000580215f68 
                     Extra: Last beacon: 1040ms ago 
                     IE: Unknown: 000D616D626962616D62696C616E64 
                     IE: Unknown: 010882848B968C129824 
                     IE: Unknown: 030102 
                     IE: Unknown: 0706555320010B1B 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 3204B048606C 
                     IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000 
                     IE: Unknown: 3D16020D0800000000000000000000000000000000000000 
                     IE: Unknown: DD0900037F01010000FF7F 
                     IE: Unknown: DD0A00037F04010002004000 
                     IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000024B2E13AED1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103 
           Cell 02 - Address: 00:24:B2:5D:68:OB 
                     Channel:3 
                     Frequency:2.422 GHz (Channel 3) 
                     Quality=48/70  Signal level=-62 dBm   
                     Encryption key:on 
                     ESSID:"Brandon" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000001264a79d80 
                     Extra: Last beacon: 624ms ago 
                     IE: Unknown: 00074272616E646F6E 
                     IE: Unknown: 010882848B968C129824 
                     IE: Unknown: 030103 
                     IE: Unknown: 0706555320010B1B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 3204B048606C 
                     IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C3403051900000000000000000000000000000000000000 
                     IE: Unknown: 3D1603051900000000000000000000000000000000000000 
                     IE: Unknown: DD0900037F01010000FF7F 
                     IE: Unknown: DD0A00037F04010002004000 
                     IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000024B25D68DB1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103 
                     IE: Unknown: DD050050F20500 
           Cell 03 - Address: 00:23:69:44:60:A4 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=61/70  Signal level=-49 dBm   
                     Encryption key:on 
                     ESSID:"corvette" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000006c36a9616dd 
                     Extra: Last beacon: 644ms ago 
                     IE: Unknown: 0008636F727665747465 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 030106 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2F0104 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: DD09001018020015000000 
           Cell 04 - Address: 40:4A:03:F4:2B:29 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=53/70  Signal level=-57 dBm   
                     Encryption key:on 
                     ESSID:"myqwest1535" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000007c870a684f 
                     Extra: Last beacon: 600ms ago 
                     IE: Unknown: 000B6D79717765737431353335 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 030106 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2F0104 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D1606001300000000000000000000000000000000000000 
                     IE: Unknown: DD780050F204104A00011010440001021041000100103B000103104700103330EFA9160F6A772CBD1F9B878A4EE3102100055A7958454C1023000651313030305A1024000B50383730484E552D35316310420004313233341054000800060050F20400011011000751776573744150100800020088103C000101 
                     IE: Unknown: DD090010180202F0050000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000 
           Cell 05 - Address: 00:22:75:9D:C9:99 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=49/70  Signal level=-61 dBm   
                     Encryption key:on 
                     ESSID:"big bear" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               12 Mb/s; 24 Mb/s; 36 Mb/s 
                     Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000001226650ed9b 
                     Extra: Last beacon: 844ms ago 
                     IE: Unknown: 00086269672062656172 
                     IE: Unknown: 010882848B960C183048 
                     IE: Unknown: 030106 
                     IE: Unknown: 0706555320010B1B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32041224606C 
                     IE: Unknown: DD180050F2020101000003A4000027A4000041435E0061211A01 
           Cell 06 - Address: C0:C1:C0:7A:00:15 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=67/70  Signal level=-43 dBm   
                     Encryption key:on 
                     ESSID:"Mickie91" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000051bbdddd183 
                     Extra: Last beacon: 224ms ago 
                     IE: Unknown: 00084D69636B69653931 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B081100000000000000000000000000000000000000 
                     IE: Unknown: DD700050F204104A00011010440001021041000100103B00010310470010955656D57F52E637E3C6F0C4FE156C3B102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101 
                     IE: Unknown: DD090010180200F0040000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
           Cell 07 - Address: 58:1F:AA:E7:BC:25 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=56/70  Signal level=-54 dBm   
                     Encryption key:on 
                     ESSID:"Fortress of Solitude" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000055995bec177 
                     Extra: Last beacon: 204ms ago 
                     IE: Unknown: 0014466F727472657373206F6620536F6C6974756465 
                     IE: Unknown: 010882848B960C121824 
                     IE: Unknown: 03010B 
                     IE: Unknown: 0706555320010B1E 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32043048606C 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B001100000000000000000000000000000000000000 
                     IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C332C4017FFFF000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000 
                     IE: Unknown: DD07000393016B0120 
                     IE: Unknown: DD070017F203020180 
           Cell 08 - Address: 00:22:3F:7C:7C:3A 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=56/70  Signal level=-54 dBm   
                     Encryption key:on 
                     ESSID:"\x00\x00\x00\x00" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               12 Mb/s; 24 Mb/s; 36 Mb/s 
                     Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000b553a5b181 
                     Extra: Last beacon: 400ms ago 
                     IE: Unknown: 000400000000 
                     IE: Unknown: 010882848B960C183048 
                     IE: Unknown: 03010B 
                     IE: Unknown: 050400010000 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32041224606C 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
           Cell 09 - Address: 00:16:B6:6A:08:84 
                     Channel:4 
                     Frequency:2.427 GHz (Channel 4) 
                     Quality=33/70  Signal level=-77 dBm   
                     Encryption key:on 
                     ESSID:"Lotus_Secure" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                               36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000001ee3d181 
  
 brandon@ubuntu:~$ rfkill list 
 0: dell-wifi: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 1: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 brandon@ubuntu:~$ dmesg | grep b43 
 [    2.640333] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    2.640347] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64 
 [   17.170411] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
 [   17.691962] Registered led device: b43-phy0::tx 
 [   17.692563] Registered led device: b43-phy0::rx 
 [   17.692665] Registered led device: b43-phy0::radio 
 [   20.176198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
 brandon@ubuntu:~$ iwlist chan 
 lo        no frequency information. 
  
 eth0      no frequency information. 
  
 wlan0     14 channels in total; available frequencies : 
           Channel 01 : 2.412 GHz 
           Channel 02 : 2.417 GHz 
           Channel 03 : 2.422 GHz 
           Channel 04 : 2.427 GHz 
           Channel 05 : 2.432 GHz 
           Channel 06 : 2.437 GHz 
           Channel 07 : 2.442 GHz 
           Channel 08 : 2.447 GHz 
           Channel 09 : 2.452 GHz 
           Channel 10 : 2.457 GHz 
           Channel 11 : 2.462 GHz 
           Channel 12 : 2.467 GHz 
           Channel 13 : 2.472 GHz 
           Channel 14 : 2.484 GHz

---

### Post by bcbrown on 2011-09-08
brandon@ubuntu:~$ lsmod 
 Module                  Size  Used by 
 binfmt_misc            13213  1  
 parport_pc             32111  0  
 ppdev                  12849  0  
 snd_hda_codec_idt      60537  1  
 snd_hda_intel          24113  2  
 snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel 
 arc4                   12473  2  
 nvidia               7098106  38  
 snd_hwdep              13274  1 snd_hda_codec 
 snd_pcm                80042  2 snd_hda_intel,snd_hda_codec 
 b43                   296610  0  
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi 
 snd_seq_midi_event     14475  1 snd_seq_midi 
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
 mac80211              257001  1 b43 
 joydev                 17322  0  
 snd_timer              28659  2 snd_pcm,snd_seq 
 r852                   17878  0  
 dell_laptop            13515  0  
 dell_wmi               12601  0  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
 sm_common              16737  1 r852 
 nand                   49822  2 r852,sm_common 
 nand_ids                8547  1 nand 
 cfg80211              156212  2 b43,mac80211 
 sparse_keymap          13666  1 dell_wmi 
 dcdbas                 14054  1 dell_laptop 
 snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 nand_ecc               13070  1 nand 
 psmouse                73312  0  
 mtd                    26720  2 sm_common,nand 
 serio_raw              12990  0  
 soundcore              12600  1 snd 
 snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
 video                  18951  0  
 lp                     13349  0  
 parport                36746  3 parport_pc,ppdev,lp 
 b44                    35301  0  
 sdhci_pci              13623  0  
 usbhid                 41704  0  
 firewire_ohci          31504  0  
 sdhci                  22720  1 sdhci_pci 
 firewire_core          56138  1 firewire_ohci 
 crc_itu_t              12627  1 firewire_core 
 hid                    77084  1 usbhid 
 ssb                    45942  2 b43,b44 
 brandon@ubuntu:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wlan0     IEEE 802.11bg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:off 
            
 brandon@ubuntu:~$ sudo iwlist scan 
 [sudo] password for brandon:  
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 wlan0     Scan completed : 
           Cell 01 - Address: 00:24:B2:E1:3A:ED 
                     Channel:2 
                     Frequency:2.417 GHz (Channel 2) 
                     Quality=59/70  Signal level=-51 dBm   
                     Encryption key:on 
                     ESSID:"ambibambiland" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000000580215f68 
                     Extra: Last beacon: 1040ms ago 
                     IE: Unknown: 000D616D626962616D62696C616E64 
                     IE: Unknown: 010882848B968C129824 
                     IE: Unknown: 030102 
                     IE: Unknown: 0706555320010B1B 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 3204B048606C 
                     IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000 
                     IE: Unknown: 3D16020D0800000000000000000000000000000000000000 
                     IE: Unknown: DD0900037F01010000FF7F 
                     IE: Unknown: DD0A00037F04010002004000 
                     IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000024B2E13AED1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103 
           Cell 02 - Address: 00:24:B2:5D:68:DB 
                     Channel:3 
                     Frequency:2.422 GHz (Channel 3) 
                     Quality=48/70  Signal level=-62 dBm   
                     Encryption key:on 
                     ESSID:"Brandon" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000001264a79d80 
                     Extra: Last beacon: 624ms ago 
                     IE: Unknown: 00074272616E646F6E 
                     IE: Unknown: 010882848B968C129824 
                     IE: Unknown: 030103 
                     IE: Unknown: 0706555320010B1B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 3204B048606C 
                     IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C3403051900000000000000000000000000000000000000 
                     IE: Unknown: 3D1603051900000000000000000000000000000000000000 
                     IE: Unknown: DD0900037F01010000FF7F 
                     IE: Unknown: DD0A00037F04010002004000 
                     IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010000000000000100000000024B25D68DB1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103 
                     IE: Unknown: DD050050F20500 
           Cell 03 - Address: 00:23:69:44:60:A4 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=61/70  Signal level=-49 dBm   
                     Encryption key:on 
                     ESSID:"corvette" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=000006c36a9616dd 
                     Extra: Last beacon: 644ms ago 
                     IE: Unknown: 0008636F727665747465 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 030106 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2F0104 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: DD09001018020015000000 
           Cell 04 - Address: 40:4A:03:F4:2B:29 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=53/70  Signal level=-57 dBm   
                     Encryption key:on 
                     ESSID:"myqwest1535" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000007c870a684f 
                     Extra: Last beacon: 600ms ago 
                     IE: Unknown: 000B6D79717765737431353335 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 030106 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 2F0104 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D1606001300000000000000000000000000000000000000 
                     IE: Unknown: DD780050F204104A00011010440001021041000100103B000103104700103330EFA9160F6A772CBD1F9B878A4EE3102100055A7958454C1023000651313030305A1024000B50383730484E552D35316310420004313233341054000800060050F20400011011000751776573744150100800020088103C000101 
                     IE: Unknown: DD090010180202F0050000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000 
           Cell 05 - Address: 00:22:75:9D:C9:99 
                     Channel:6 
                     Frequency:2.437 GHz (Channel 6) 
                     Quality=49/70  Signal level=-61 dBm   
                     Encryption key:on 
                     ESSID:"big bear" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               12 Mb/s; 24 Mb/s; 36 Mb/s 
                     Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000001226650ed9b 
                     Extra: Last beacon: 844ms ago 
                     IE: Unknown: 00086269672062656172 
                     IE: Unknown: 010882848B960C183048 
                     IE: Unknown: 030106 
                     IE: Unknown: 0706555320010B1B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32041224606C 
                     IE: Unknown: DD180050F2020101000003A4000027A4000041435E0061211A01 
           Cell 06 - Address: C0:C1:C0:7A:00:15 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=67/70  Signal level=-43 dBm   
                     Encryption key:on 
                     ESSID:"Mickie91" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                               24 Mb/s; 36 Mb/s; 54 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000051bbdddd183 
                     Extra: Last beacon: 224ms ago 
                     IE: Unknown: 00084D69636B69653931 
                     IE: Unknown: 010882848B962430486C 
                     IE: Unknown: 03010B 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 2F0100 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 32040C121860 
                     IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B081100000000000000000000000000000000000000 
                     IE: Unknown: DD700050F204104A00011010440001021041000100103B00010310470010955656D57F52E637E3C6F0C4FE156C3B102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101 
                     IE: Unknown: DD090010180200F0040000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (2) : CCMP TKIP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
           Cell 07 - Address: 58:1F:AA:E7:BC:25 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=56/70  Signal level=-54 dBm   
                     Encryption key:on 
                     ESSID:"Fortress of Solitude" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=0000055995bec177 
                     Extra: Last beacon: 204ms ago 
                     IE: Unknown: 0014466F727472657373206F6620536F6C6974756465 
                     IE: Unknown: 010882848B960C121824 
                     IE: Unknown: 03010B 
                     IE: Unknown: 0706555320010B1E 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32043048606C 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : CCMP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D160B001100000000000000000000000000000000000000 
                     IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD1E00904C332C4017FFFF000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000 
                     IE: Unknown: DD07000393016B0120 
                     IE: Unknown: DD070017F203020180 
           Cell 08 - Address: 00:22:3F:7C:7C:3A 
                     Channel:11 
                     Frequency:2.462 GHz (Channel 11) 
                     Quality=56/70  Signal level=-54 dBm   
                     Encryption key:on 
                     ESSID:"\x00\x00\x00\x00" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               12 Mb/s; 24 Mb/s; 36 Mb/s 
                     Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000b553a5b181 
                     Extra: Last beacon: 400ms ago 
                     IE: Unknown: 000400000000 
                     IE: Unknown: 010882848B960C183048 
                     IE: Unknown: 03010B 
                     IE: Unknown: 050400010000 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32041224606C 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
           Cell 09 - Address: 00:16:B6:6A:08:84 
                     Channel:4 
                     Frequency:2.427 GHz (Channel 4) 
                     Quality=33/70  Signal level=-77 dBm   
                     Encryption key:on 
                     ESSID:"Lotus_Secure" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s 
                               36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000001ee3d181 
  
 brandon@ubuntu:~$ rfkill list 
 0: dell-wifi: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 1: phy0: Wireless LAN 
     Soft blocked: no 
     Hard blocked: no 
 brandon@ubuntu:~$ dmesg | grep b43 
 [    2.640333] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    2.640347] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64 
 [   17.170411] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
 [   17.691962] Registered led device: b43-phy0::tx 
 [   17.692563] Registered led device: b43-phy0::rx 
 [   17.692665] Registered led device: b43-phy0::radio 
 [   20.176198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
 brandon@ubuntu:~$ iwlist chan 
 lo        no frequency information. 
  
 eth0      no frequency information. 
  
 wlan0     14 channels in total; available frequencies : 
           Channel 01 : 2.412 GHz 
           Channel 02 : 2.417 GHz 
           Channel 03 : 2.422 GHz 
           Channel 04 : 2.427 GHz 
           Channel 05 : 2.432 GHz 
           Channel 06 : 2.437 GHz 
           Channel 07 : 2.442 GHz 
           Channel 08 : 2.447 GHz 
           Channel 09 : 2.452 GHz 
           Channel 10 : 2.457 GHz 
           Channel 11 : 2.462 GHz 
           Channel 12 : 2.467 GHz 
           Channel 13 : 2.472 GHz 
           Channel 14 : 2.484 GHz

---

### Post by praseodym on 2011-09-08
Ok, now go to the network-manager applet, remove your current wireless profile and set up a new one (changing a current profile may not work).

---

### Post by bcbrown on 2011-09-08
Done. I have successfully connected to my NetGear wireless router. Thanks for your assistance!!!

---

### Post by praseodym on 2011-09-08
:popcorn:

Great. You can mark this thread [SOLVED] by editing the first posting and choosing it from the pull-down-menu.

---


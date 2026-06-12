---
title: "Ubuntu 11.10 wireless not working"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by eipgene on 2011-11-14
This is my first ever post here as I just installed ubutu 11.10 over the weekend. However, the wireless is not working..
I've been trying to solve it myself by following this tutorial: [http://ubuntuforums.org/archive/index.php/t-1476007.html](http://ubuntuforums.org/archive/index.php/t-1476007.html)

I went from the beginning until I couldn't get step 5 to work, the problem is I typed in sudo rmmod rt2860sta, there is an error message saying "ERROR:Module rt2860sta does not exist in /proc/modules"
Someone in that post actually had the same problem and others asked this question of whether you are sure you are using the "Ralink RT2860 WiFi chipset"?  

I bought this wireless card: [http://www.microcenter.com/single_product_results.phtml?product_id=0350102](http://www.microcenter.com/single_product_results.phtml?product_id=0350102) and I have no clue if I'm using the Ralink RT2860 WiFi chipset..

One more note, I'm not connecting to internet through wire either at this moment, could this be the source of the problem?

Can someone help me and tell me what's going on.. I'm a total newbie on ubuntu and this wireless problem is driving me crazy... Thank you guys!

---

### Post by praseodym on 2011-11-14
Hi,

please show the following terminal (CTRL+ALT+T) outputs of:

```
lspci -nnk
lsmod
uname -a
rfkill list
iwconfig
ifconfig -a
cat /etc/network/interfaces
```

---

### Post by eipgene on 2011-11-14
1. lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
    Subsystem: Device [0043:0083]
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
    Subsystem: Device [0043:0083]
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
    Subsystem: Device [0043:0083]
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8375]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.6 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 [8086:3b4e] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.7 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 [8086:3b50] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
    Kernel modules: iTCO_wdt
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
    Kernel modules: i2c-i801
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8383]
    Kernel driver in use: ata_piix
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Cedar PRO [Radeon HD 5450] [1002:68f9]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:2120]
    Kernel driver in use: radeon
    Kernel modules: radeon
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:aa68]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB361 AHCI/IDE [197b:2361] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:824f]
    Kernel driver in use: ahci
    Kernel modules: ahci
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB361 AHCI/IDE [197b:2361] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:824f]
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron
04:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:8413]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
05:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE91A0 SATA 6Gb/s Controller [1b4b:91a0] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8400]
    Kernel driver in use: pata_marvell
    Kernel modules: pata_marvell
08:02.0 Network controller [0280]: Ralink corp. Device [1814:3062]
    Subsystem: Ralink corp. Device [1814:3062]
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

---

### Post by eipgene on 2011-11-14
2. $lsmod
Module                  Size  Used by
fglrx                2642662  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
joydev                 17393  0 
snd_hda_codec_via      61329  1 
arc4                   12473  2 
rt2800pci              18340  0 
asus_atk0110           17742  0 
rt2800lib              48717  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                925020  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
pata_jmicron           12651  0 
libahci                25727  1 ahci
r8169                  43104  0 
xhci_hcd               72915  0 
pata_marvell           12763  2

---

### Post by eipgene on 2011-11-14
3. $ uname -a
Linux localhost 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by eipgene on 2011-11-14
4. $ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by eipgene on 2011-11-14
5. $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by eipgene on 2011-11-14
6. $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 20:cf:30:ee:2e:33  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:feee:2e33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87522127 (87.5 MB)  TX bytes:2815802 (2.8 MB)
          Interrupt:50 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:ca:e2:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by eipgene on 2011-11-14
7. $ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

---

### Post by praseodym on 2011-11-15
Try this driver:
```
sudo apt-get install linux-headers-generic build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Check with:

```
iwconfig
lsmod
dmesg | grep rt2
sudo iwlist scan
```

Dont remove the folder, you need to compile again after a kernel upgrade via:
```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean 
sudo make
sudo make install 
```

---

### Post by eipgene on 2011-11-15
I did all those code.. reboot and now check again:
1. iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: 58:6D:8F:00:A5:58   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-63 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by eipgene on 2011-11-15
2. $ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
rt3562sta             878243  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_via      61329  1 
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2595570  100 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
asus_atk0110           17742  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
xhci_hcd               72915  0 
pata_jmicron           12651  0 
ahci                   21634  0 
libahci                25727  1 ahci
r8169                  43104  0 
pata_marvell           12763  2

---

### Post by eipgene on 2011-11-15
3. $ dmesg |grep rt2
(No output from this command)




4. $ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: C0:C1:C0:84:96:C6
                    Protocol:802.11b/g/n
                    ESSID:"BirdNetRouter"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:37/100  Signal level:-75 dBm  Noise level:-70 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD690050F204104A0001101044000102103B00010310470010E5362E93E2FB5EB826D1218A5E3D8B3E10210005436973636F102300054531353030102400063132333435361042000234321054000800060050F2040001101100054531353030100800020084103C000101
          Cell 02 - Address: 7C:4F:B5:D0:C4:72
                    Protocol:802.11b/g
                    ESSID:"FontbonneU"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-73 dBm  Noise level:-68 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: 64:0F:28:FB:3F:01
                    Protocol:802.11b/g
                    ESSID:"jerk"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-73 dBm  Noise level:-68 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: C0:C1:C0:84:96:C7
                    Protocol:802.11b/g/n
                    ESSID:"BirdNetRouter-guest"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-77 dBm  Noise level:-72 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
          Cell 05 - Address: C0:83:0A:28:CA:99
                    Protocol:802.11b/g
                    ESSID:"2WIRE334"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:100/100  Signal level:-33 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 34:EF:44:E1:63:09
                    Protocol:802.11b/g
                    ESSID:"2WIRE216"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:37/100  Signal level:-75 dBm  Noise level:-70 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:22:A4:25:49:61
                    Protocol:802.11b/g
                    ESSID:"2WIRE672"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-17 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 58:6D:8F:00:A5:58
                    Protocol:802.11b/g/n
                    ESSID:"wakaka"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:68/100  Signal level:-63 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102

---

### Post by eipgene on 2011-11-15
I did the rest of the code after reboot, check and now the wireless card are able to pick up the wireless now! However, there is still no connection... any idea of what's still wrong?

---

### Post by praseodym on 2011-11-15
Which of those networks do you want to connect to? Remove your wireless profile and create a new one because the interface name changed to ra0

---

### Post by eipgene on 2011-11-15
I want to connect to wakaka. How do I remove and creat new profile?

---

### Post by praseodym on 2011-11-15
Right-click on the network-manager applet->Edit connection->wireless

Mark your network and remove it. After that create a new one. I recommend changing the encryption in your router to pure WPA2-AES instead of mixed WPA/WPA2

---

### Post by eipgene on 2011-11-15
OK. I'll try that later when I get back home.. thanks so much for all your help!!

---

### Post by eipgene on 2011-11-15
> **praseodym said:**
> Right-click on the network-manager applet->Edit connection->wireless

Mark your network and remove it. After that create a new one. I recommend changing the encryption in your router to pure WPA2-AES instead of mixed WPA/WPA2

It finally works!!!! THANK YOU SO MUCH!

I  looked at the Wireless Security options but couldn't find WPA2-AES.. There are only the following:
1. WEP 40/128-bit Key (Hex or ASCII)
2. WEP 128-bit Passphrase
3. LEAP
4. Dynamic WEP (802.1x)
5. WPA & WPA2 Personal 
6. WPA & WPA2 Enterprise

---

### Post by praseodym on 2011-11-15
5. WPA & WPA2 Personal 

is the right one

---

### Post by eipgene on 2011-11-15
> **praseodym said:**
> 5. WPA & WPA2 Personal 

is the right one


Thanks!

---

### Post by eipgene on 2011-11-15
> **praseodym said:**
> Try this driver:
```
sudo apt-get install linux-headers-generic build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Check with:

```
iwconfig
lsmod
dmesg | grep rt2
sudo iwlist scan
```

Dont remove the folder, you need to compile again after a kernel upgrade via:
```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean 
sudo make
sudo make install 
```

Can you tell me why I need to install RT3562? How did you find that out? I'd like to learn a bit about it.

---

### Post by eipgene on 2011-11-16
Another question, can I delete the downloaded directory, DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared?

---

### Post by praseodym on 2011-11-16
Dont delete it, you need to compile ahain as described above, if a new kernel comes in.

---

### Post by eipgene on 2011-11-16
> **praseodym said:**
> Dont delete it, you need to compile ahain as described above, if a new kernel comes in.

OK. Can I move it to a different location on my computer? I downloaded it onto the Desktop and want to make my Desktop look cleaner..

---

### Post by eipgene on 2011-11-16
> **praseodym said:**
> Dont delete it, you need to compile ahain as described above, if a new kernel comes in.

A more general question might be:

I have installed many softwares in the past several days while I don't understand how and where they were installed. It seems that they are by default installed in the home directory in root (does this saying sound right?) I now want to organize the folders I downloaded to one central place for all the softwares. Can I move those folders?

---

### Post by praseodym on 2011-11-16
If you copy it e.g. to /home/Downloads/ you need to compile in future via

```
cd ~/Downloads/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean 
sudo make
sudo make install
```
Downloaded packages are saved to /var/cache/apt/archives. These packages are removed via
```
sudo apt-get clean
```
to save disc space. Ubuntu/Linux-systems install the programs to different locations, see here:

[http://proton.pathname.com/fhs/pub/fhs-2.3.pdf](http://proton.pathname.com/fhs/pub/fhs-2.3.pdf)

you shouldnt move them by hand!

---

### Post by eipgene on 2011-11-16
Several questions:
1. can I copy them to a desired location and then removed them from their current location (Desktop)? 

2. If answer is yes to question 1, I need to compile the DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared in the new location using the code you gave?

3. If I remove those packages using sudo apt-get clean, this action won't affect the install softwares because they are in cache?

Thanks!

---

### Post by praseodym on 2011-11-16
1.) Yes

2.) Yes, but use the new absolute path to compile

3.) No, these are only the downloaded .deb-Packages (like e.g. .EXE), you can safely remove them or save them to CD/DVD/whatever if you only have a slow connection with big files. You can make your own Package CD _before_ removing with the app "APTonCD"

---

### Post by northd_tech on 2011-11-16
> **praseodym said:**
> 
3.) No, these are only the downloaded .deb-Packages (like e.g. .EXE), you can safely remove them or save them to CD/DVD/whatever if you only have a slow connection with big files. You can make your own Package CD _before_ removing with the app "APTonCD"
Thank you very much for this APTonCD tip, praseodym.  I've been looking for a Linux/Ubuntu backup tool like this for a LONG time.  (I have my own command line method I've been working on using **nautilus** and **dpkg -i *.deb** but this APTonCD method looks much easier).

My first package .ISO just finished.  BTW it apparently does not support Nero Linux 4.0 (out of the box) to immediately burn the .ISO file, just brasero and k3b, but once the .ISO is generated one could in thoery even burn/modify it from under Windows if so desired.

That's a** keeper **(and I'm thinking of remastering my first LiveDVD and customized Ubuntu distribution in the near future so I likely will incorporate it).

=D>

---

### Post by praseodym on 2011-11-16
Burning ISO _images_ works with "Richt-click" on the ISO and "write on CD/DVD"

---

### Post by northd_tech on 2011-11-16
I'm not ready to burn the .ISO file quite yet (I was just a little surprised that it didn't detect my Nero Linux software)- I might need to dig up some other packages and remaster another .ISO, but this one (APTonCD) it is one of my favorite Linux tools now.

One thing- I did find this curious bit at the APTonCD SourceForge page:

> *This project has no files.*[http://sourceforge.net/projects/aptoncd/files/](http://sourceforge.net/projects/aptoncd/files/)

[http://sourceforge.net/projects/aptoncd/](http://sourceforge.net/projects/aptoncd/)

The SVN looks about 4 years old, and I've never heard of this package before this morning.  Has the project been abandoned already?  I suppose that a PERL script would accomplish everything that I want to do (and that APTonCD does)- in a much less user-friendly and 'attractive' CLI way.  Do you know if the source code for APTonCD is available anywhere?

Edit:  I did find a tarball on the SVN page:

[http://aptoncd.svn.sourceforge.net/viewvc/aptoncd/?view=tar](http://aptoncd.svn.sourceforge.net/viewvc/aptoncd/?view=tar)

[http://aptoncd.svn.sourceforge.net/](http://aptoncd.svn.sourceforge.net/)

The README for /0.2/ is 0 bytes, and I'm not sure the directory structure is complete though.

---

### Post by praseodym on 2011-11-16
Install it via

```
sudo apt-get install synaptic aptoncd
```

it uses the synaptic package manager, which is not installed per default anymore in 11.10

---

### Post by eipgene on 2011-11-17
guys, i have another problem that I don't know how to solve now.. so I used the wired connection to post those replies earlier and got the wireless to work, in about 2-3 meters from the wireless router. Since I got the wireless working now, I moved my desktop back to my room which is more than, say 7 meters away from the router. and guess what.. the wireless connection is really slow now. 

I googled it and found this post: [http://ubuntuforums.org/showthread.php?t=1127371](http://ubuntuforums.org/showthread.php?t=1127371)

I tried this:
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"wakaka"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 58:6D:8F:00:A5:58   
          Bit Rate=39 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=28/100  Signal level:-79 dBm  Noise level:-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Then I tried this code: iwconfig wlan0 rate 6M fixed and it doesn't seem to help at all. 
Output is:

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"wakaka"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 58:6D:8F:00:A5:58   
          Bit Rate=39 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:D1BD-3ECF-A567-2871-62CE-E281-4D42-0983
          Link Quality=44/100  Signal level:-78 dBm  Noise level:-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I don't know how to deal with it now.. any suggestions?

---

### Post by praseodym on 2011-11-17
You want to increase the speed?

```
sudo iwconfig [COLOR="Red"]ra0[/COLOR] rate auto
```
the interface name changed to ra0

---

### Post by eipgene on 2011-11-17
> **praseodym said:**
> You want to increase the speed?

```
sudo iwconfig [COLOR="Red"]ra0[/COLOR] rate auto
```
the interface name changed to ra0

 I actually typed int ra0 in my last reply, sorry for the typo..

I tried your command, it seems to become better, faster but apparently not  as fast/quick to load a webpage as before... it took like 1 second to open this forum before and now it take more than 10 seconds and I can't open gmail..

I don't know if I should call it speed or strength.. the wireless bars were full two days ago and now it fluctuate from almost no connection to half/full bars...

So I'm wondering if this is just because of the nature of the wireless card, the further my computer is physically away from the router, the worse the wireless connection.. or it's something that can be fixed by a command..

what can I try else now?


After I typed in the command you suggested, here is the output

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"wakaka"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 58:6D:8F:00:A5:58   
          Bit Rate=39 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-77 dBm  Noise level:-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by eipgene on 2011-11-19
I had moved this back to a table closer to the wireless router and now the wireless is just fine...  so it's just a limitation of the hardware?

---

### Post by praseodym on 2011-11-20
Maybe a hardware limitation. Tried other channels?

---

### Post by toccovender on 2011-11-25
Hey guys, I'm having a very similar issue with my wireless in Ubuntu 11.10, but I've got a different card, I have the Intel Centrino Advanced-n 6250 + wimax. I've been searching around the Internet for the past week or so since I installed Oneiric (dual booted with win7) trying to figure out how to get this damned wireless card working to no avail. It works just fine on Win7, and it's not hard or soft blocked. I tried doing what praseodym suggested in post #10 and it did not work. 
One thing I found very strange was that the wireless card was working during install and on the live cd.
I've tried installing all sorts of backports and everything but they all appear to be "missing" from the package list. I also downloaded and installed the latest Intel microcode, which also didn't fix it.

Thanks in advance for any help!

(here's the info requested in post #2)

lspci -nnk:
```
$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series] [1002:68e4]
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel modules: radeon
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel modules: snd-hda-intel
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0089] (rev 57)
    Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN [8086:1311]
    Kernel modules: iwlagn
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
    Kernel driver in use: r8169
    Kernel modules: r8169
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:163d]

```
lsmod:
```
$ lsmod
Module                  Size  Used by
arc4                   12529  0 
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
mac80211              462092  2 rt2x00usb,rt2x00lib
i915                  566711  8 
drm_kms_helper         42558  1 i915
parport_pc             36962  0 
rfcomm                 47946  0 
ppdev                  17113  0 
lp                     17799  0 
vesafb                 13809  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
binfmt_misc            17540  1 
sparse_keymap          13890  0 
wimax                  34762  0 
v4l2_compat_ioctl32    17083  0 
serio_raw              13166  0 
intel_ips              18089  0 
soundcore              12680  0 
drm                   236330  4 i915,drm_kms_helper
cfg80211              199587  2 rt2x00lib,mac80211
mei                    41480  0 
snd_page_alloc         18529  0 
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
video                  19412  1 i915
input_polldev          13896  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
hid_a4tech             12678  0 
usbhid                 47198  0 
hid                    95463  2 hid_a4tech,usbhid
ahci                   26002  1 
libahci                26861  1 ahci
r8169                  52788  0 

```
uname -a:
```

$ uname -a
Linux robert-HP-Pavilion-dv7-Notebook-PC 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```
rfkill list:
(didn't return anything in terminal when belkin wireless adapter wasn't plugged in, when plugged in it shows that it's not hard or soft blocked.)
iwconfig:
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
ifconfig -a:
$ ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 98:4b:e1:c1:1e:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39728 (39.7 KB)  TX bytes:39728 (39.7 KB)


```
cat /etc/network/interfaces:
```

cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by rocsco on 2011-12-05
Hi

Hope this is OK to ask here.

I have same problem. HP4730S Probook running Ubuntu 11.10. It has a Ralink Wifi chip requiring the rt2860sta driver which was not installed and is now but I can't make the system recognise it going through all of the usual hoops.

Hope you can help
Ross

Stats out from the system is:

lspci -nnk
lsmod
uname -a
rfkill list
iwconfig
ifconfig -a
cat /etc/network/interfaces
-------------------------------------------
 root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:167d]
        Kernel driver in use: i915
        Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: mei
        Kernel modules: mei
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ahci
        Kernel modules: ahci
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]
        Subsystem: Hewlett-Packard Company Device [103c:167d]
        Kernel driver in use: radeon
        Kernel modules: radeon
24:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci
24:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel modules: sdhci-pci
24:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2393] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: jmb38x_ms
        Kernel modules: jmb38x_ms
25:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
        Subsystem: Hewlett-Packard Company Device [103c:1638]
        Kernel modules: rt2800pci
26:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: r8169
        Kernel modules: r8169
27:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci-hcd
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# lsmod
Module                  Size  Used by
arc4                   12529  2 
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
mac80211              462092  2 rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
bnep                   18436  2 
rfcomm                 47946  12 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
joydev                 17693  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rt2860sta             864748  0 
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
radeon               1016085  0 
i915                  566711  3 
wmi                    19256  1 hp_wmi
xhci_hcd               82772  0 
video                  19412  1 i915
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  2 i915,radeon
drm                   236330  6 i915,radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  2 i915,radeon
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# uname -a
Linux anish-1 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# rfkill list
1: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
6: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Roscommon"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:F2:D7:33:1A   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:49   Missed beacon:0

root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:1f:74:eb:af:9d  
          inet addr:192.168.38.83  Bcast:192.168.38.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:feeb:af9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1090304 (1.0 MB)  TX bytes:728767 (728.7 KB)
          Interrupt:47 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:256912 (256.9 KB)  TX bytes:256912 (256.9 KB)

wlan1     Link encap:Ethernet  HWaddr 00:12:0e:9e:b9:42  
          inet addr:192.168.38.90  Bcast:192.168.38.255  Mask:255.255.255.0
          inet6 addr: fe80::212:eff:fe9e:b942/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28258 (28.2 KB)  TX bytes:42178 (42.1 KB)

root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# cat /etc/network/interfaces
auto lo
iface lo inet loopback
-----------------------------------------------
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:167d]
        Kernel driver in use: i915
        Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: mei
        Kernel modules: mei
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)
        Kernel driver in use: pcieport                                                                                                  
        Kernel modules: shpchp                                                                                                          
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b4)           
        Kernel driver in use: pcieport                                                                                                  
        Kernel modules: shpchp                                                                                                          
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ahci
        Kernel modules: ahci
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]
        Subsystem: Hewlett-Packard Company Device [103c:167d]
        Kernel driver in use: radeon
        Kernel modules: radeon
24:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci
24:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel modules: sdhci-pci
24:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2393] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: jmb38x_ms
        Kernel modules: jmb38x_ms
25:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
        Subsystem: Hewlett-Packard Company Device [103c:1638]
        Kernel modules: rt2800pci
26:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: r8169
        Kernel modules: r8169
27:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci-hcd
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# lsmod
Module                  Size  Used by
arc4                   12529  0 
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
mac80211              462092  2 rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
bnep                   18436  2 
rfcomm                 47946  12 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
joydev                 17693  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rt2860sta             864748  0 
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
radeon               1016085  0 
i915                  566711  3 
wmi                    19256  1 hp_wmi
xhci_hcd               82772  0 
video                  19412  1 i915
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  2 i915,radeon
drm                   236330  6 i915,radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  2 i915,radeon
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# uname -a
Linux anish-1 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# rfkill list
1: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
6: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:1f:74:eb:af:9d  
          inet addr:192.168.38.83  Bcast:192.168.38.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:feeb:af9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1302736 (1.3 MB)  TX bytes:989383 (989.3 KB)
          Interrupt:47 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:260713 (260.7 KB)  TX bytes:260713 (260.7 KB)

root@anish-1:/opt/2010_07_16_RT2860_Linux_STA_v2.4.0.0# cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by praseodym on 2011-12-05
Install the driver according to this thread:

[http://ubuntuforums.org/showthread.php?t=1869278&highlight=1814%3A3592&page=2](http://ubuntuforums.org/showthread.php?t=1869278&highlight=1814%3A3592&page=2)

beginning from #15

---

### Post by pratyay85 on 2012-02-20
I am trying to fix the wireless problem. But could not. Here is the specifications
  Command:~$ lspci -nnk | grep -iA2 net    
  Result:
  24:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]     Subsystem: Hewlett-Packard Company Device [103c:1638]
  **    Kernel driver in use: rt2800pci**

  25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)     Subsystem: Hewlett-Packard Company Device [103c:1680]     Kernel driver in use: r8169
  Command:~$ iwconfig
  Result:
  lo        no wireless extensions.
  eth0      no wireless extensions.
  wlan0     IEEE 802.11abgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:off
  ppp0      no wireless extensions.
  PLease Help.....

---

### Post by praseodym on 2012-02-20
Hi pratyay85.

Add the device ID to the driver. This is one line, you better copy/paste it:

```
echo 'install rt2800pci modprobe --ignore-install rt2800pci ; /bin/echo "1814 3592" > /sys/bus/usb/drivers/rt2800pci/new_id' | sudo tee /etc/modprobe.d/rt2800pci.conf
```
Reload the driver:
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci 
```
Check:

```
lsmod
dmesg | grep rt2
iwconfig
rfkill list
```

---


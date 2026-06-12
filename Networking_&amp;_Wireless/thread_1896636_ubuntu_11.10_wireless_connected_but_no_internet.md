---
title: "ubuntu 11.10 wireless connected but no internet"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by sonna22 on 2011-12-17
hi fellas,
i recently installed ubuntu 11.10 from the cd everything went fine
i'm able to connect to the wireless network and there is internet connection for about 5 - 10 seconds then there is no longer internet access although still connected the problem is the same with both internal wireless card as well as my usb wireless adaptor  which is ALFA RTL8187 
and i'm triple booting together with windows 7 and windows developer preview in both i have internet access with no problem
in ubuntu i reinstalled network manager but still the same 
my laptop is toshiba L300
also i installed compact wireless driver but still the same 
and i don't think it is a driver problem
so any ideas will be appreciated....

---

### Post by sonna22 on 2011-12-17
i'm waiting for your help please

---

### Post by sonna22 on 2011-12-17
please help

---

### Post by praseodym on 2011-12-17
Please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
iwlist chan
cat /etc/resolv.conf
```

---

### Post by sonna22 on 2011-12-18
```
austin316@austin316:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff66]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlagn
austin316@austin316:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
austin316@austin316:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17711  2 
rfcomm                 37292  0 
bluetooth             147371  10 bnep,rfcomm
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
arc4                   12473  4 
rtl8187                56076  0 
eeprom_93cx6           12653  1 rtl8187
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
psmouse                73673  0 
iwlagn                275533  0 
snd_seq_midi           13132  0 
mac80211              271200  2 rtl8187,iwlagn
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              171447  3 rtl8187,iwlagn,mac80211
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13658  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505108  3 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
austin316@austin316:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"Hemn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:1D:67:8C:04:B8   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:132  Invalid misc:341   Missed beacon:0

austin316@austin316:~$ sudo iwlist scan
[sudo] password for austin316: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

wlan1     Scan completed :
          Cell 01 - Address: 1C:1D:67:8C:04:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Hemn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000383664772
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000448656D6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120

austin316@austin316:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

austin316@austin316:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
austin316@austin316:~$
```

---

### Post by praseodym on 2011-12-18
The driver iwlagn is buggy concerning the N-mode in 11.10, deactivate that via:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
Check without stick and cable:
```
iwconfig
route -n
sudo iwlist scan
dmesg | grep iwl
rfkill list
```

---

### Post by sonna22 on 2011-12-18
without stick and cable
```
austin316@austin316:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
austin316@austin316:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
austin316@austin316:~$ sudo iwlist scan
[sudo] password for austin316: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

wlan1     Scan completed :
          Cell 01 - Address: 74:EA:3A:FF:7F:7A
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Ahmad Aziz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f3f26d04
                    Extra: Last beacon: 1580ms ago
                    IE: Unknown: 000A41686D616420417A697A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0A00000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD850050F204104A0001101044000102103B000103104700100000000000001000000074EA3AFF7F7A1021000754502D4C494E4B10230009544C2D57523734304E10240007312E302F322E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523734304E100800020086103C000101
          Cell 02 - Address: 1C:1D:67:8C:04:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Hemn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000436a6c084
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 000448656D6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
          Cell 03 - Address: 00:80:48:65:54:63
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Zanyar ISP - Slemany"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000041b04f1f4
                    Extra: Last beacon: 804ms ago
                    IE: Unknown: 00145A616E79617220495350202D20536C656D616E79
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

austin316@austin316:~$ dmesg | grep iwl
[   20.300825] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.300864] iwlagn 0000:03:00.0: setting latency timer to 64
[   20.315648] iwlagn 0000:03:00.0: pci_resource_len = 0x00002000
[   20.315652] iwlagn 0000:03:00.0: pci_resource_base = f8174000
[   20.315655] iwlagn 0000:03:00.0: HW Revision ID = 0x0
[   20.315925] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[   20.316104] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   20.316248] iwlagn 0000:03:00.0: L1 Enabled; Disabling L0S
[   20.338251] iwlagn 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   20.338254] iwlagn 0000:03:00.0: Device SKU: 0Xf0
[   20.338333] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.558286] iwlagn 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   20.571103] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.019971] iwlagn 0000:03:00.0: L1 Enabled; Disabling L0S
[   21.022968] iwlagn 0000:03:00.0: Radio type=0x1-0x2-0x0
[   21.140906] iwlagn 0000:03:00.0: L1 Enabled; Disabling L0S
[   21.143858] iwlagn 0000:03:00.0: Radio type=0x1-0x2-0x0
austin316@austin316:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
austin316@austin316:~$ 


```

---

### Post by sonna22 on 2011-12-18
when i do 
sudo modprobe -v iwlagn 
the indicator flashes then stops and nothing happens 
buttomline is the problem persists

---

### Post by praseodym on 2011-12-18
Which country do you live?

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE # DE for Germany, change it to yours
```

---

### Post by sonna22 on 2011-12-18
i live in iraq so what the command line should look like?

---

### Post by praseodym on 2011-12-18
It should be

```
sudo iw reg set IQ
```
Check:
```
iwlist chan
sudo iwlist scan
dmesg | grep country
```

---

### Post by sonna22 on 2011-12-19
i'm so sory it took me so long 
```
austin316@austin316:~$ sudo apt-get install iw
[sudo] password for austin316: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
iw is already the newest version.
iw set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 288 not upgraded.
austin316@austin316:~$ iw reg get
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
austin316@austin316:~$ sudo iw reg set IQ
austin316@austin316:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
wlan1     14 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

austin316@austin316:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

wlan1     Scan completed :
          Cell 01 - Address: 1C:1D:67:8C:04:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Hemn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000175a6c9177
                    Extra: Last beacon: 244ms ago
                    IE: Unknown: 000448656D6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
          Cell 02 - Address: 20:2B:C1:DF:F1:CA
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"brwa99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000008ad7d0d2
                    Extra: Last beacon: 1160ms ago
                    IE: Unknown: 0006627277613939
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A8E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000D127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706495120010B10
                    IE: Unknown: DD1E00904C338E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340A000600000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A880202BC1DFF1CA1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101

austin316@austin316:~$ dmesg | grep country
[  883.805918] cfg80211: Calling CRDA for country: IQ
austin316@austin316:~$ 

```
still the same, i appreciate your help anyway.

---

### Post by sonna22 on 2011-12-19
i'm sure there are other people having the same issue with ubuntu 11.10 i'm sure there is a way to get rid of it otherwise ubuntu 11.10 is useless ,no offense , i will be glad to see the final solution.

---

### Post by praseodym on 2011-12-19
> 0 upgraded, 0 newly installed, 0 to remove and [COLOR="Red"]288[/COLOR] not upgraded.
Try to update your system!

---

### Post by dreamquartz on 2011-12-19
Hi sonna22,

How did you create that nice output lay-out?
When I try to copy and paste, it is a mess.

Thx,

Dream

---

### Post by sonna22 on 2011-12-20
> **dreamquartz said:**
> Hi sonna22,

How did you create that nice output lay-out?
When I try to copy and paste, it is a mess.

Thx,

Dream

Hi yourself to copy and paste the output in the thread there are many ways , the simplest one which i did is to select the output then right click to copy then paste it in a new text document  then copy and paste the text in the thread but remeber do it in advanced mode ,after you paste it in the box ,do select all and press the hash {#} button and you'r done , {but if you don't have internet access in ubuntu , then  copy that text document to the windows partition if you'r duel booting, from there open it and do the same }

and you'r wellcome

---

### Post by sonna22 on 2011-12-20
> **praseodym said:**
> Try to update your system!
I've  been trying to do that , but i can't access internet in ubuntu  , so what shall i do?

---

### Post by praseodym on 2011-12-20
What about the stick?

---

### Post by sonna22 on 2011-12-20
ok i somehow managed to update the system ,the update manager now says and i quote "your system is up to date" but the very same problem exists with wireless connection looks like we are out of solution , this reallt pisses me off , i don't know what do now

---

### Post by sonna22 on 2011-12-20
ok i somehow managed to update the system ,the update manager now says and i quote "your system is up to date" but the very same problem exists with wireless connection looks like we are out of solution , this really pisses me off , i don't know what do now

---

### Post by sonna22 on 2011-12-20
sorry about the double post

---

### Post by praseodym on 2011-12-20
Check, if one of the Win systems deactivates the card during shutdown. Check also the BIOS settings if there is "on", "last state", etc. Also try to reset the BIOS to default settings

---

### Post by Neal12 on 2011-12-21
I'm also have trouble getting my wireless to work.  I ran the above and got;neal@neal-desktop:~$ lspci -nnk | grep -iA2 net
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:8139]
    Kernel driver in use: 8139too
neal@neal-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. 
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
neal@neal-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7098131  34 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
floppy                 60310  0 
8139too                23283  0 
8139cp                 22636  0 
neal@neal-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

neal@neal-desktop:~$ sudo iwlist scan
TIA got everything....

---

### Post by praseodym on 2011-12-21
Hi Neal12,

try to add the device ID to the module rt2800usb:

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
```
This is one line, you better copy/paste it! Load the module via:

```
sudo modprobe -v rt2800usb
```
Check:
```
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by Neal12 on 2011-12-21
After running the last 'check' I get
 IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: 00:26:50:9E:42:29
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"2WIRE466"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000240fec0b890
                    Extra: Last beacon: 1052ms ago
                    IE: Unknown: 00083257495245343636
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

---

### Post by Neal12 on 2011-12-21
I have a CD from the company that lists    'Realtek 8187 Linux',  and when I open it I get  '148f:5370  Ralink Technology Corp'

---

### Post by praseodym on 2011-12-21
Please show the complete "checks"

---

### Post by Neal12 on 2011-12-21
Check 1
install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id
Check 2 shows 'can't find'

---

### Post by Neal12 on 2011-12-21
k

---

### Post by praseodym on 2011-12-21
```
modinfo rt2800usb
cat /etc/modprobe.d/rt2800usb.conf
iwconfig
```
please. COPY/PASTE the outputs into a text file

---

### Post by Neal12 on 2011-12-21
~$ modinfo rt2800usb 
 filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
 license:        GPL 
 firmware:       rt2870.bin 
 description:    Ralink RT2800 USB Wireless LAN driver. 
 version:        2.3.0 
 author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) 
 srcversion:     61CFBA7ACB6A210B48AA6CB 
 
 vermagic:       3.0.0-14-generic SMP mod_unload modversions 686  
 parm:           nohwcrypt:Disable hardware encryption. (bool) 
 neal@neal-desktop:~$ cat /etc/modprobe.d/rt2800usb.conf 
 install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id

---

### Post by praseodym on 2011-12-21
So it doesnt work. Remove the file:

```
sudo rm /etc/modprobe.d/rt2800usb.conf
```
and compile the latest driver from the Ralink-homepage:

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

---

### Post by Neal12 on 2011-12-21
OK,  now it shows in my archives....Now how do I compile?  Is that the same as 'install'?

---

### Post by praseodym on 2011-12-21
With wired connection you need to install the compiling tools:

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
Unpack the driver to /home. Then you need to adjust in the file **/os/linux/config.mk** of that folder the following lines to "y":

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```
save, close the editor, and open a terminal:

```
cd [COLOR="Red"]nameoffolder[/COLOR]/
sudo make
sudo make install
```
Reboot and check:
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Neal12 on 2011-12-27
I'm back with you.  Had to take care of those Xmas thingys you know.
Still don't really ubnderstand much of your 'lingo' yet,,,But trying to learn.

---


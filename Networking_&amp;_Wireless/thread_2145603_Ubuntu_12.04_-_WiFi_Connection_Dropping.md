---
title: "Ubuntu 12.04 - WiFi Connection Dropping"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by Panama.Craig on 2013-05-15
Hello Everyone,

   I've come to the Forums, and done a search, but to be honest... It's been so long since I've messed with Linux anything, that I can barely do anything...  I do understand how to run commands in the terminal and etc, so I can post anything that is needed, however... I'm not sure where to start here...

   I know the connection issue isn't actually due to my Router, because my Laptop, which runs on Win7, is currently connected fine and stays connected.  However, my Desktop PC, which I have a clean install of 12.04 on, is basically having an intermittent issue of dropping its wireless connection.  That being said, I also know from what I -have- read, that I may need to turn off the "N" setting and stick it to "G" only.  Which I would prefer -not- to do, but will do if I -have- to.

   Could someone please help me out with this?  I've always loved Linux, and would love to keep Ubuntu on this Machine.

---

### Post by moody_mark on 2013-05-16
Hi, sometimes wireless connection dropping could be interference from other access points on the same channel. Your windows machine will have a different card and a manufacturer's driver, your desktop will have a different hardware and might not be seeing such a strong signal. Im guessing you are using network manager? Do you have more than one access point on your wireless network? (You can have two routers with the same SSID using one as simply an access point and one as the gateway router). Try using a tool like "wicd" or "WiFi Radar" to see what other access points are in the vicinity. Sometimes it will be the interference as I mentioned above sometimes it will be network manager hopping to the strongest signal.

It is worth trying a channel change on your router if you haven't done so already, apparently using channels like 1, 6 or 11 may help. I found channel 11 worked best for me even though there are other 11s close by. Apparently this is to do with there being crossover frequencies among the channels so these ones are more independent of one another. [http://en.wikipedia.org/wiki/IEEE_802.11#Frequencies_and_Channels](http://en.wikipedia.org/wiki/IEEE_802.11#Frequencies_and_Channels)

---

### Post by Panama.Craig on 2013-05-16
Ok...  I had both of PC's right beside each other all the time when they both ran Win7, and they both would work perfectly fine.  Both would stay connected constantly.  This issue only popped up once I installed Ubuntu... It's -never- happened before....  Also, I do not have 2 different wireless signals with the same name.  Only 1 router, 1 modem in the house.  Also, the router is already configured to be on channel 11, because anything between channels 3-7 catch interference from my wireless phone in the house.

---

### Post by praseodym on 2013-05-16
Please show these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by Panama.Craig on 2013-05-16
lspci -nnk | grep -iA2 net
```

04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5786 Gigabit Ethernet PCI Express [14e4:169a] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0dfe]
	Kernel driver in use: tg3

```

lsusb
```

Bus 001 Device 002: ID 1307:0169 Transcend Information, Inc. 
Bus 002 Device 002: ID 1058:0740 Western Digital Technologies, Inc. My Passport 1TB
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 008 Device 002: ID 050d:0200 Belkin Components 
Bus 008 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 005: ID 13b1:0031 Linksys AM10 v1 802.11n [Ralink RT3072]

```

lsmod
```

Module                  Size  Used by
parport_pc             32867  0 
ppdev                  17114  0 
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             211812  10 bnep,rfcomm
binfmt_misc            17541  1 
vesafb                 13846  1 
arc4                   12530  2 
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
joydev                 17694  0 
snd_hda_codec_realtek    79855  1 
hid_generic            12541  0 
mxm_wmi                13022  0 
snd_hda_intel          34063  3 
snd_hda_codec         135141  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
wmi                    19257  1 mxm_wmi
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
rt2800usb              22903  0 
rt2800lib              59396  1 rt2800usb
crc_ccitt              12708  1 rt2800lib
rt2x00usb              20809  1 rt2800usb
rt2x00lib              55575  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              555272  3 rt2800lib,rt2x00usb,rt2x00lib
nvidia              11309216  42 
ses                    17418  0 
enclosure              15313  1 ses
psmouse               102075  0 
cfg80211              208382  2 rt2x00lib,mac80211
serio_raw              13216  0 
snd_timer              29990  2 snd_pcm,snd_seq
mac_hid                13254  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            23910  0 
lpc_ich                17145  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
soundcore              15092  1 snd
edac_core              53053  3 i7core_edac
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
microcode              23030  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
firewire_ohci          41034  0 
firewire_core          64697  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
ahci                   25869  0 
tg3                   156646  0 
libahci                27338  1 ahci
pata_jmicron           12748  0 
usb_storage            49288  1 

```

iwconfig
```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Griffith Family"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 08:86:3B:9F:7D:48   
          Bit Rate=60 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3031  Invalid misc:1704   Missed beacon:0

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:22:68:3f:c3:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:445919 (445.9 KB)  TX bytes:445919 (445.9 KB)


wlan0     Link encap:Ethernet  HWaddr 68:7f:74:73:16:c4  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6a7f:74ff:fe73:16c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103005952 (103.0 MB)  TX bytes:6638124 (6.6 MB)

```

sudo iwlist scan
```

eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:9F:7D:48
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Griffith Family"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b439120a1
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000F47726966666974682046616D696C79
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA50050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F08863B9F7D481021001442656C6B696E20496E7465726E6174696F6E616C102300144E33303020576972656C65737320526F757465721024000746394B313030321042000E32303132303647433130393634371054000800060050F20400011011001B42656C6B696E204E33303020576972656C65737320526F75746572100800020086
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: 5C:57:1A:00:CD:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"HOME-CD62"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010dc77bb57
                    Extra: Last beacon: 1880ms ago
                    IE: Unknown: 0009484F4D452D43443632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503005E127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A8805C571A00CD6010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F75746572100800020084103C000101
          Cell 03 - Address: 00:1D:D4:63:EF:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME-EF62"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000128f36fc1e
                    Extra: Last beacon: 1880ms ago
                    IE: Unknown: 0009484F4D452D45463632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DD463EF60103C000101
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020039127A
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: 20:AA:4B:B8:EE:A3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"kiwigal10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d0eb53c98
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 00096B69776967616C3130
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
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010B074AEE431441FC3BF509BC2369A628610210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 20:AA:4B:B8:EE:A5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"kiwigal10-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d0eb54720
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 000F6B69776967616C31302D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: C8:D7:19:E7:BF:D9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Phase2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d080b82a8
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0006506861736532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD740050F204104A0001101044000102103B00010310470010FF27363D8654AA2DB2DED41AB7976740102100074C696E6B73797310230004453930301024000776312E302E30331042000234321054000800060050F20400011011000445393030100800022688103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

cat /etc/resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search Belkin

```









Also finally note that I've not had the connection issue since I've turned on my PC this morning...  It may have actually been the wireless card from my Laptop interfering with the signal.  Or it may be that it truly is just an intermittent issue.  I will turn on my laptop and run it for a little while to see if the issue starts coming back up.

Thank you for your assistance.

---

### Post by praseodym on 2013-05-16
Deactivate the power management of the card:
```

sudo iwconfig wlan0 power off
```
and change to a fixed channel (e.g. 6) with pure WPA2-AES (CCMP) encryption. Check the router manual for this.

---

### Post by Panama.Craig on 2013-05-16
I've done all 3 of these recommendations... Thank you very much Praseodym, I will come back in a day to announce if there were any further issues, or to announce if the issue seems to be resolved.  As it is right now, the issue seems to be resolved.

---


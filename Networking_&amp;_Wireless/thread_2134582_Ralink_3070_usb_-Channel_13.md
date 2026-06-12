---
title: "Ralink 3070 usb -Channel 13"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by mojekorisnickoime on 2013-04-11
I have a very wierd problem whit my wireless.

I can connect to any wifi normal but if i connect on wifi on channel 13 it gives me IP but i cant ping ruter and heve no internet?
i am using usb ralink 3070 

any help would be nice
> 
kompijuter@NedirajMe:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"sanjam"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: B0:B2:DC:4F:0A:5C   
          Bit Rate=28.9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



kompijuter@NedirajMe:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_codec_via      46198  1 
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
snd_hda_intel          32719  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_nforce2            12906  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2909978  133 
cfg80211              178877  2 rt2x00lib,mac80211
snd                    62218  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
dm_multipath           22747  0 
serio_raw              13027  0 
ppdev                  12849  0 
parport_pc             32114  1 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
k10temp                12990  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638248  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41937  0 
hid                    77428  1 usbhid
floppy                 60184  0 
forcedeth              58096  0 
pata_amd               13750  0 
sata_nv                23360  2 
zram                   18193  1 

kompijuter@NedirajMe:~$ sudo lshw -C network
[sudo] password for kompijuter: 
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 48:02:2a:45:b4:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-40-generic-pae firmware=0.29 ip=192.168.1.6 link=yes multicast=yes wireless=IEEE 802.11

kompijuter@NedirajMe:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: B0:B2:DC:4F:0A:5C
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"sanjam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000054cffd7cc1
                    Extra: Last beacon: 13948ms ago
                    IE: Unknown: 000673616E6A616D
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500010D7A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706414C20010D10
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340D070400000000000000000000000000000000000000
                    IE: Unknown: DD9F0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601B0B2DC4F0A5C1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000B5472656E64436869704150100800020084103C000100
          Cell 02 - Address: 54:E6:FC:DD:FD:74
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Joca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004ea49e181
                    Extra: Last beacon: 14912ms ago
                    IE: Unknown: 00044A6F6361
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F01010008FF7F
                    IE: Unknown: DD1A00037F030100000054E6FCDDFD7456E6FCDDFD7464002C010808
          Cell 03 - Address: F4:EC:38:BC:09:D2
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NikolaS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d1621ed96
                    Extra: Last beacon: 14960ms ago
                    IE: Unknown: 00074E696B6F6C6153
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34080F0800000000000000000000000000000000000000
                    IE: Unknown: 3D16080F0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 04 - Address: 90:F6:52:21:67:2E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"DAVIDOVIC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001decd1d3180
                    Extra: Last beacon: 14320ms ago
                    IE: Unknown: 000944415649444F564943
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B071100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD3F0050F204104A0001101044000102104700100000000000001000000090F652216710103C000101104900140024E26002000101600000020001600100020001
          Cell 05 - Address: 40:4A:03:CF:1E:A3
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Titan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a6dda6186
                    Extra: Last beacon: 14064ms ago
                    IE: Unknown: 0005546974616E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010004
                    IE: Unknown: 0706434820010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C

eth0      Interface doesn't support scanning.

---

### Post by mojekorisnickoime on 2013-04-11
anybody

---

### Post by mojekorisnickoime on 2013-04-12
help

---

### Post by mojekorisnickoime on 2013-04-12
downloaded newes drivers and make install and modprobe and it fixsed now it works

---


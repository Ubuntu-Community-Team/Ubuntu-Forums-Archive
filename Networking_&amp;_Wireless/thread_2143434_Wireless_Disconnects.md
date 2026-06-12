---
title: "Wireless Disconnects"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by ruddi on 2013-05-09
Hello. :)

When I download or "max out" my internet connection the wireless network disconnects, this happens most often when I use a torrent client like deluge or transmission, the only way to reconnect is to disable wifi then enable it.
If I am browsing the web, watching youtube etc. everything works fine

Ubuntu 13.04 64bit
I am using gsky gs-27USB 
Motherboard: Gigabyte Z77X-UD5H  (If that helps?)

Thanks in advance :)

---

### Post by ruddi on 2013-05-11
any help would be greatly appreciated :)

---

### Post by ruddi on 2013-05-20
No one? :)

---

### Post by praseodym on 2013-05-20
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
sudo iwlist scan
```

---

### Post by ruddi on 2013-05-20
Thank you for answering :) 
Here is the output 



ath@ath-pc:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: e1000e
--
06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: atl1c
ath@ath-pc:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 2109:0810  
Bus 004 Device 003: ID 2109:0810  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 004: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 005: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 006: ID 2109:0810  
Bus 001 Device 007: ID 2109:0810  
ath@ath-pc:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
vesafb                 13828  1 
arc4                   12615  2 
coretemp               13355  0 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
hid_generic            12540  0 
aesni_intel            55399  3 
rtl8187                60848  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mac80211              606457  1 rtl8187
cfg80211              510937  2 mac80211,rtl8187
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
eeprom_93cx6           13344  1 rtl8187
mxm_wmi                13021  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
microcode              22881  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
psmouse                95870  0 
serio_raw              13215  0 
lpc_ich                17061  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mei                    41158  0 
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
fglrx                5201161  147 
video                  19390  0 
wmi                    19070  1 mxm_wmi
mac_hid                13205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
amd_iommu_v2           19068  1 fglrx
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
atl1c                  41071  0 
ahci                   25731  2 
libahci                31364  1 ahci
e1000e                198787  0 
ath@ath-pc:~$ iwconfig
eth0      no wireless extensions.


eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"SiminnECADC1"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 58:98:35:EC:AD:C1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0


ath@ath-pc:~$ iwconfig -a
-a        No such device


ath@ath-pc:~$ sudo iwlist scan
[sudo] password for ath: 
eth0      Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: 58:98:35:EC:AD:C1
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"SiminnECADC1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000C53696D696E6E454341444331
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180206000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


ath@ath-pc:~$ clear


ath@ath-pc:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: e1000e
--
06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
	Kernel driver in use: atl1c
ath@ath-pc:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 2109:0810  
Bus 004 Device 003: ID 2109:0810  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 004: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 005: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 006: ID 2109:0810  
Bus 001 Device 007: ID 2109:0810  
ath@ath-pc:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
vesafb                 13828  1 
arc4                   12615  2 
coretemp               13355  0 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
hid_generic            12540  0 
aesni_intel            55399  3 
rtl8187                60848  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mac80211              606457  1 rtl8187
cfg80211              510937  2 mac80211,rtl8187
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
eeprom_93cx6           13344  1 rtl8187
mxm_wmi                13021  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
microcode              22881  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
psmouse                95870  0 
serio_raw              13215  0 
lpc_ich                17061  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mei                    41158  0 
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
fglrx                5201161  147 
video                  19390  0 
wmi                    19070  1 mxm_wmi
mac_hid                13205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
amd_iommu_v2           19068  1 fglrx
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
atl1c                  41071  0 
ahci                   25731  2 
libahci                31364  1 ahci
e1000e                198787  0 
ath@ath-pc:~$ iwconfig
eth0      no wireless extensions.


eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"SiminnECADC1"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 58:98:35:EC:AD:C1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0


ath@ath-pc:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:2b:34:57:9c:3f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 90:2b:34:57:9c:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7f00000-f7f20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37341 (37.3 KB)  TX bytes:37341 (37.3 KB)


wlan0     Link encap:Ethernet  HWaddr 00:e0:4c:9d:ee:3b  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe9d:ee3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3621695 (3.6 MB)  TX bytes:247845 (247.8 KB)


ath@ath-pc:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.

---

### Post by praseodym on 2013-05-20
Router firmware is up-to-date? Try a fixed channel instead of "auto"

---

### Post by wildmanne39 on 2013-05-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ruddi on 2013-05-20
Wild man
Sorry about that, I am new and did not know how to do that 

[COLOR=#000000]praseodym
The router is up-to-date, this only happens on my Ubuntu machine, my laptop is fine and when i dual boot to windows 7 it works fine too.
How do I try a fixed channel? sorry I am noob
Thank you so much for your help :)[/COLOR]

---

### Post by ruddi on 2013-05-21
I changed the channel and now it works fine, thank you :)
But I was wondering why this only happens in ubuntu/mint but not in windows?

---

### Post by ruddi on 2013-05-21
I should have knocked on wood.. it worked for a couple of minutes then it started to disconnect again, I have tried out different channels but that did not change anything.
But if it's a problem with the channel wouldn't it also affect my computer when using windows 7? 
So, any other ideas? :)

---


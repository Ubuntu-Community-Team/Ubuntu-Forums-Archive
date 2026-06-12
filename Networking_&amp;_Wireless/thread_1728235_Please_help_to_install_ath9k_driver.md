---
title: "Please help to install ath9k driver"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by Strolchi on 2011-04-13
Hello all,
just bought a Compaq Presario CQ56, installed Ubuntu 10.10, but the install program did not realize the AR 9286 (Atheros) WLAN chip.
After 3 days of reading I successfully installed linux-backport-modules-compat-wireless-2.6.36-2.6.35-28-generic-pae.
If I look now at sys/module(s) I find a (correct) ath, ath9k, ath9k_common, and a ath_hw directory.

Linux Wireless (originator of ath9k) describes in their installation procedure to install and use a NCURSES user interface in order to install the mac80211 Networking stack and Atheros 802.11 wireless card support.

This all is much over my head. I am begging on my knees for a cooking recipe in order to finish this night mare.

Hopefully one of the GURUS has an understanding for a bloody beginners difficulty.

Best regards
Strolchi

---

### Post by josephmills on 2011-04-13
hi there could you please post ```
lspci
``````
iwconfig
``````
rfkill list
``` thanks

---

### Post by Strolchi on 2011-04-13
Hello Josephmills
thanks for your fast respose.

Please let me tell you the result.

lspci           clearly detects the AR9285 chip



iwconfig     lo        no wireless extensions.

                  eth0      no wireless extensions.

                  wlan0     IEEE 802.11bgn  ESSID:"FRITZ!Box Fon WLAN 7270"  
                                Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
                               Tx-Power=20 dBm   
                               Retry  long limit:7   RTS thr:off   Fragment thr:off
                               Power Management:off

rfkill list                   0: hp-bluetooth: Bluetooth
                              Soft blocked: no
                              Hard blocked: no
                             1: phy0: Wireless LAN
                             Soft blocked: no
                              Hard blocked: no


Sorry it took a while because I had to tranfer from the win to the ubuntu PC.

I hope this helps you.
BR
Strolchi

---

### Post by josephmills on 2011-04-13
is there anyway that you can plug into a router?

---

### Post by Strolchi on 2011-04-13
Yes, I am connected by cable to a router

BR Strolchi

---

### Post by josephmills on 2011-04-13
please go to the link and follow post # 4 [http://ubuntuforums.org/showthread.php?t=1727472](http://ubuntuforums.org/showthread.php?t=1727472)

---

### Post by Strolchi on 2011-04-16
Hello Joseph

first I want to make you a complement, I find it so great that you have the great power to work with people like all the newbies -me. 

I read the conversation with the guy having the same problem with a Dell machine.
 but it doesnt really help me. I mean I dont anderstand the key points.

To my problem, I still cannot use the Internet, although I think I made allmost everything right.

I made a dump of the configuration according the succestions given in Wicki, that should tell enough to give it the last kik.

Please see the below.

gerhard@Presario-CQ56-Notebook-PC:~$[COLOR=Blue] **lsmod**[/COLOR]
Module                  Size  Used by
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22299  2 
binfmt_misc             6599  1 
arc4                    1165  2 
joydev                  8767  0 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
ath9k                  90317  0 
mac80211              235189  1 ath9k
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
ath9k_common            4396  1 ath9k
snd_seq_midi            4588  0 
ath9k_hw              291798  2 ath9k,ath9k_common
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ath                     8053  2 ath9k,ath9k_hw
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
cfg80211              142680  3 ath9k,mac80211,ath
video                  18712  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
videodev               43098  1 uvcvideo
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
v4l1_compat            13359  2 uvcvideo,videodev
output                  1883  1 video
psmouse                59033  0 
led_class               2633  1 ath9k
shpchp                 29982  0 
lp                      7342  0 
hp_wmi                  5223  0 
serio_raw               4022  0 
i2c_piix4               8795  0 
k10temp                 2607  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
ahci                   19198  2 
libahci                21792  1 ahci
r8169                  36777  0 
mii                     4425  1 r8169
gerhard@Presario-CQ56-Notebook-PC:~$ 




gerhard@Presario-CQ56-Notebook-PC:~$[COLOR=Blue] sudo iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:52:79:0B:91
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Mirakel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020a6df4a180
                    Extra: Last beacon: 996ms ago
                    IE: Unknown: 00074D6972616B656C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706415420010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010B0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001100000000000000000000000000000000000000
                    IE: Unknown: DD0700039301690120
                    IE: Unknown: DD070017F203020180
          Cell 02 - Address: 00:24:FE:A5:C0:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000b8ab183
                    Extra: Last beacon: 704ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037323730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: 10110009465249545A21426F78100800020188103C000103





gerhard@Presario-CQ56-Notebook-PC:~$[COLOR=Blue] sudo lshw -c network[/COLOR]
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:35:0f:92
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 98:4b:e1:bf:69:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.26 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:2000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9002ffff
gerhard@Presario-CQ56-Notebook-PC:~$ 




gerhard@Presario-CQ56-Notebook-PC:~$[COLOR=Blue] iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FRITZ!Box Fon WLAN 7270"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
gerhard@Presario-CQ56-Notebook-PC:~$ 




gerhard@Presario-CQ56-Notebook-PC:~$[COLOR=Blue] iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn    
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
gerhard@Presario-CQ56-Notebook-PC:~$ 


I hope this dump will be of some help to you.

The access point is ok, because I have a Win 2000 and a Android Handy connected to it.

Thank you for your time and effort

Gerhard  (Strolchi)

---

### Post by josephmills on 2011-04-16
Hello there again I my self am new to this but if you right click on the network managers icon (see pic) is wireless greyed out?

---

### Post by Strolchi on 2011-04-17
Good morning,
the Network Manager looks exactly the same as yours. Even the white light on the F12 key is on. I have the impression WLAN is O.K. but there is some how no connection to the system. 

Thanks and have a nice Sunday.

BR
Strolchi

---

### Post by Strolchi on 2011-05-09
Big thanks to all of you, the problem doesnt exist anymore
Strochi.

---

### Post by josephmills on 2011-05-09
> **Strolchi said:**
> Big thanks to all of you, the problem doesnt exist anymore
Strochi.

cool glad to see that you got it working please mark as solved ):P

---


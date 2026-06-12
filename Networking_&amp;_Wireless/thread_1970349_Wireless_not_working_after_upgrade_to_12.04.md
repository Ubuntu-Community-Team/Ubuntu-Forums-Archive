---
title: "Wireless not working after upgrade to 12.04"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by gokulsurendiran on 2012-05-01
Hi All,
I'm using Sansung N150 netbook & recently udgraded from 11.10 tp 12.04; everything is fine except by wireless. It searches for network but unable to connect. Please help with this.

lspci -nn | grep 0280
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

lsmod
Module Size Used by
ipt_MASQUERADE 12663 0 
xt_state 12514 0 
ipt_REJECT 12512 0 
xt_tcpudp 12531 0 
iptable_filter 12706 0 
nf_nat_h323 12749 0 
nf_conntrack_h323 52412 1 nf_nat_h323
nf_nat_pptp 12536 0 
nf_conntrack_pptp 13553 1 nf_nat_pptp
nf_conntrack_proto_gre 13395 1 nf_conntrack_pptp
nf_nat_proto_gre 12671 1 nf_nat_pptp
nf_nat_tftp 12420 0 
nf_conntrack_tftp 12817 1 nf_nat_tftp
nf_nat_sip 16921 0 
nf_conntrack_sip 24749 1 nf_nat_sip
nf_nat_irc 12542 0 
nf_conntrack_irc 13138 1 nf_nat_irc
nf_nat_ftp 12595 0 
nf_conntrack_ftp 13183 1 nf_nat_ftp
iptable_nat 13016 0 
nf_nat 24959 9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_prot o_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp ,iptable_nat
nf_conntrack_ipv4 19084 3 iptable_nat,nf_nat
nf_conntrack 73847 18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h 323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_pro to_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf _conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntra ck_ipv4
nf_defrag_ipv4 12649 1 nf_conntrack_ipv4
ip_tables 18106 2 iptable_filter,iptable_nat
x_tables 21974 7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptab le_filter,iptable_nat,ip_tables
easy_slow_down_manager 12985 0 
dm_crypt 22528 0 
joydev 17393 0 
snd_hda_codec_realtek 174055 1 
snd_hda_intel 32765 3 
snd_hda_codec 109562 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13276 1 snd_hda_codec
snd_pcm 80845 2 snd_hda_intel,snd_hda_codec
samsung_backlight 13487 0 
snd_seq_midi 13132 0 
arc4 12473 2 
snd_rawmidi 25424 1 snd_seq_midi
ath9k 117425 0 
uvcvideo 67203 0 
mac80211 436455 1 ath9k
snd_seq_midi_event 14475 1 snd_seq_midi
videodev 86588 1 uvcvideo
ath9k_common 13781 1 ath9k
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
ath9k_hw 391523 2 ath9k,ath9k_common
psmouse 87213 0 
snd_timer 28931 2 snd_pcm,snd_seq
btusb 17912 1 
serio_raw 13027 0 
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
ath 19387 3 ath9k,ath9k_common,ath9k_hw
cfg80211 178679 3 ath9k,mac80211,ath
snd 62064 15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec, snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,sn d_seq_device
soundcore 14635 1 snd
snd_page_alloc 14115 2 snd_hda_intel,snd_pcm
rfcomm 38139 12 
bnep 17830 2 
bluetooth 158438 23 btusb,bnep,rfcomm
parport_pc 32114 0 
ppdev 12849 0 
binfmt_misc 17292 1 
mac_hid 13077 0 
lp 17455 0 
parport 40930 3 parport_pc,ppdev,lp
i915 414568 3 
drm_kms_helper 45466 1 i915
drm 197692 4 i915,drm_kms_helper
sky2 49545 0 
i2c_algo_bit 13199 1 i915
video 19068 1 i915

---

### Post by chili555 on 2012-05-01
So far, everything looks pretty solid. Let's have a look at:```
iwconfig
sudo iwlist wlan0 scan
sudo cat /var/log/syslog | grep -e ath -e etwork | tail -n20
```Thanks.

---

### Post by gokulsurendiran on 2012-05-01
response for iwconfig


lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"daffo"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1A:A9:60:59:40   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by chili555 on 2012-05-01
> It searches for network but unable to connect. However...> wlan0 IEEE 802.11bgn [COLOR="Red"]ESSID:"daffo"[/COLOR]
Mode:Managed Frequency:2.427 GHz [COLOR="Red"]Access Point: 00:1A:A9:60:59:40[/COLOR]
Bit Rate=54 Mb/s Tx-Power=15 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
[COLOR="Red"]Link Quality=70/70[/COLOR] Signal level=-33 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
It looks like you are connected right now! No??

---

### Post by gokulsurendiran on 2012-05-01
response for sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:25:5E:32:65:E8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061b17884c
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 0004686F6D65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:25:5E:32:65:EA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061b178e8e
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: 00:25:5E:32:65:EB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061b17919f
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 04 - Address: 00:21:A4:32:19:8D
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"WI5_Banaswadi SAP3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000021101322
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 00125749355F42616E6173776164692053415033
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 0706494E49010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010026FF7F
          Cell 05 - Address: 08:86:3B:98:6B:E1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"belkin.3be2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000051035e063
                    Extra: Last beacon: 124ms ago
                    IE: Unknown: 000B62656C6B696E2E33626532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0F0000000000000000000000000000000000000000
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100008863B986BE11021001242656C6B696E20436F72706F726174696F6E1023000A4637443133303120763110240007312E30302E32321042000E31323131353047313130323732391054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084

---

### Post by gokulsurendiran on 2012-05-01
continuation......(I don't know where from the smileys came & not able to post!)
          Cell 06 - Address: 00:1A:A9:60:59:40
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"daffo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003717b687a
                    Extra: Last beacon: 464ms ago
                    IE: Unknown: 0005646166666F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030104
                    IE: Unknown: 070A555320010B1E010B1E00
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010910400
          Cell 07 - Address: 00:25:5E:32:65:E9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000061b178b7d
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: 00:E0:4C:00:25:32
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"Ultimate_B_Band3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015fe46b0054
                    Extra: Last beacon: 564ms ago
                    IE: Unknown: 0010556C74696D6174655F425F42616E6433
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 05080001006800C10002
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD0700E04C01020300
          Cell 09 - Address: 80:A1:D7:25:E0:60
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"luckysan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s;
24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018b7155e0c
                    Extra: Last beacon: 11504ms ago
                    IE: Unknown: 00086C75636B7973616E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 10 - Address: 80:A1:D7:25:E0:61
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MGMNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018b715621d
                    Extra: Last beacon: 11504ms ago
                    IE: Unknown: 00054D474D4E54
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

---

### Post by gokulsurendiran on 2012-05-01
> **chili555 said:**
> However...It looks like you are connected right now! No??

it only searches for the network; and it says wireless disconnected - you are offline

---

### Post by gokulsurendiran on 2012-05-01
response for sudo cat /var/log/syslog | grep -e ath -e etwork | tail -n20


May  1 19:16:07 Daffo NetworkManager[644]: <info> Config: added 'ssid' value 'daffo'
May  1 19:16:07 Daffo NetworkManager[644]: <info> Config: added 'scan_ssid' value '1'
May  1 19:16:07 Daffo NetworkManager[644]: <info> Config: added 'key_mgmt' value 'NONE'
May  1 19:16:07 Daffo NetworkManager[644]: <info> Config: added 'wep_key0' value '<omitted>'
May  1 19:16:07 Daffo NetworkManager[644]: <info> Config: added 'wep_tx_keyidx' value '0'
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  1 19:16:07 Daffo NetworkManager[644]: <info> Config: set interface ap_scan to 1
May  1 19:16:07 Daffo NetworkManager[644]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  1 19:16:07 Daffo NetworkManager[644]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  1 19:16:07 Daffo NetworkManager[644]: <info> (wlan0): supplicant interface state: authenticating -> associating
May  1 19:16:07 Daffo NetworkManager[644]: <info> (wlan0): supplicant interface state: associating -> completed
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'daffo'.
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May  1 19:16:07 Daffo NetworkManager[644]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  1 19:16:07 Daffo NetworkManager[644]: <info> dhclient started with pid 32630
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0) Beginning IP6 addrconf.
May  1 19:16:07 Daffo NetworkManager[644]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May  1 19:16:08 Daffo NetworkManager[644]: <info> (wlan0): DHCPv4 state changed nbi -> preinit

---

### Post by chili555 on 2012-05-01
Please try:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```Does it connect now? If so, we can write one file and make it persistent.

---

### Post by gokulsurendiran on 2012-05-01
> **chili555 said:**
> Please try:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```Does it connect now? If so, we can write one file and make it persistent.

no same reaction; "wireless network disconnected"

---

### Post by chili555 on 2012-05-01
Please try one more:```
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
```Is your router set up to do 802.11B, G and *N*? I just solved a case where changing the router to B and G only made it possible to connect. You might try it.

I am just about out of ideas.

---

### Post by gokulsurendiran on 2012-05-01
> **chili555 said:**
> Please try one more:```
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
```Is your router set up to do 802.11B, G and *N*? I just solved a case where changing the router to B and G only made it possible to connect. You might try it.

I am just about out of ideas.

the first part didn't work,

sorry for the trouble...... how do I do the second part changing router to B & G!!!

I'm using ubuntu for close to 2 years & it never gave such a problem!

---


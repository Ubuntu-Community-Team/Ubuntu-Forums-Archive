---
title: "Atheros AR9285 / Ubuntu 11.10 / Toshiba NB305 netbook"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by koleary on 2011-12-22
Wireless worked fine with Ubuntu 11.04 on this netbook.  I also have a desktop (Ubuntu 11.04 & Windows XP dual-boot) and wireless on it works well too.

After doing a clean install of 11.10 I have very slow and erratic wireless performance; most access attempts time out (eventually if not immediately).

After looking at similar posts here is the results of running the commands typically requested:

```

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux netbook 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```

lspci -nnk | grep -iA2 net

07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Accton Technology Corporation Device [1113:e811]
	Kernel driver in use: ath9k
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff30]
	Kernel driver in use: r8169

```

```

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SiPorFavor"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: AC:81:12:85:48:35   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

```

```

rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```

rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```

lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 127538  0 
mac80211              310872  1 ath9k
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13839  1 ath9k
psmouse                73882  0 
ath9k_hw              312866  2 ath9k,ath9k_common
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
ath                    24067  2 ath9k,ath9k_hw
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  3 ath9k,mac80211,ath
i915                  566711  3 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  2 ums_realtek
uas                    18027  0 
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0

```

Thanks in advance for any help you can offer.

Kevin

---

### Post by praseodym on 2011-12-22
Hi,

deactivate the hardware encryption of the driver (software encryption WEP/WPA/WPA2 not affected):

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
This is a kind of bug in 11.10

---

### Post by koleary on 2011-12-22
Hi praseodym,

   I tried the solution that you suggested but my wireless performance did not change.
   Any other ideas?

Kevin

---

### Post by praseodym on 2011-12-22
Which encryption mode do you use I recommend WPA2-AES (CCMP) instead of mixed WPA/WPA2 or even WEP. The network-manager often has problems with that.

---

### Post by koleary on 2011-12-22
I have been using "WPA & WPA2 Personal".

The options listed for Wireless Security on my PC are:
*  WEP 40/128-bet Key
*  WEP 128-bit Passphrase
*  LEAP
*  Dynamic WEP (802.1x)
*  WPA & WPA2 Personal
*  WPA & WPA2 Enterprise

WPA2-AES is not listed as an option.  

Are any of these other choices worth trying?

Kevin

---

### Post by praseodym on 2011-12-22
You need to change the encryption mode in your router interface. Connect via cable (because you change setting for wireless) and type in the IP address of the router into your browser. "WPA&WPA2 Personal" is right then

---

### Post by koleary on 2011-12-22
Hi praseodym,

Thank you for your assistance with this wireless problem.

I am able to access the router successfully using a cable and following your directions.  My settings in the router to begin with are:
*  Authentication = WPA-WPA2-Mixed_PSK
*  Encryption = TKIP

Per your earlier post I made these changes in the router:
*  Authentication = WPA2 PSK
*  Encryption = AES

On my netbook, I kept security set to "WPA & WPA2 Personal".  
After rebooting both my netbook and the router/modem my wireless is still not working.


While I was accessing the router, I noticed that authentication can be changed to "WPA2".  But when this is done, a new configuration block labeled "802.1x Setting" appears.  All the fields in this block are filled with default values with one exception -- the "Radius server".  I have no idea what this should be -- and something needs to be input into this field before this configuration change is accepted (IOW I get an error message when the "Radius server" field is left blank and I try to save the configuration).

I am open to any more suggestions you may have.

Kevin

---

### Post by praseodym on 2011-12-23
Ok, some more info:

```
dmesg | egrep 'ath|country'
iwlist chan
sudo iwlist scan
route -n
cat /etc/resolv.conf
```

---

### Post by koleary on 2011-12-23
Here is the response to your code request.

```

dmesg | egrep 'ath|country'

[    9.989209] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.989241] ath9k 0000:07:00.0: setting latency timer to 64
[   10.042144] ath: EEPROM regdomain: 0x65
[   10.042154] ath: EEPROM indicates we should expect a direct regpair map
[   10.042166] ath: Country alpha2 being used: 00
[   10.042173] ath: Regpair used: 0x65
[   10.076708] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.080482] Registered led device: ath9k-phy0
[   11.081146] type=1400 audit(1324654386.324:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=812 comm="apparmor_parser"
[   11.097728] type=1400 audit(1324654386.340:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=812 comm="apparmor_parser"

```

```

iwlist chan

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

```

```

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:CF:31:BA
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"nope"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d8ce3ea183
                    Extra: Last beacon: 808ms ago
                    IE: Unknown: 00046E6F7065
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B0001031047001062A5DA38EC54A56131E2117D506CDE851021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:23:F8:A6:E3:63
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL_363"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000023b2e3911c6
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 00095A7958454C5F333633
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 03 - Address: 02:2A:8A:DC:2E:DB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"HP-nomodel.9E6E48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000078ce73e3bc
                    Extra: Last beacon: 568ms ago
                    IE: Unknown: 001148502D6E6F6D6F64656C2E394536453438
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: AC:81:12:85:48:35
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SiPorFavor"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bd4c7a426
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000A5369506F724661766F72
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1607000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020008127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706313920010910
          Cell 05 - Address: 68:7F:74:84:B2:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Blessed"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ad023c180
                    Extra: Last beacon: 624ms ago
                    IE: Unknown: 0007426C6573736564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: 00:1A:70:7F:9E:82
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"EVH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003932db8fd0
                    Extra: Last beacon: 432ms ago
                    IE: Unknown: 0003455648
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: C0:C1:C0:06:3E:F0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Cisco"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000af29b94186
                    Extra: Last beacon: 856ms ago
                    IE: Unknown: 0005436973636F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: 00:23:F8:98:6D:FB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL_DFB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000055fc3c9e1b6
                    Extra: Last beacon: 628ms ago
                    IE: Unknown: 00095A7958454C5F444642
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 050C010300180000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 09 - Address: 94:44:52:63:43:C5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Belkin.33C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000025a109d18e
                    Extra: Last beacon: 304ms ago

```

```

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.15.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

```

cat /etc/resolv.conf

# Generated by NetworkManager
nameserver 192.168.15.1

```

Kevin

---

### Post by praseodym on 2011-12-23
Your network on channel 7 is still WPA/WPA2 mixed. Remove your current profile in the network-manager and setup a new one. Which country do you live? I also recommend using another channel instead of 7, a lot of traffic on channel 6 around it.

---

### Post by koleary on 2011-12-23
Hi praseodym,

I accessed the modem and it had "Radio Channel" set to "Auto".  I changed this to "4".  Then I deleted my profile in Network Manager and created a new one as you suggested.

When I tested this new setup my Wireless connection was working.  There was about 100MB of updates (for my new install of Ubuntu 11.10) that I successfully downloaded.  But after these new updates were installed and I rebooted my netbook, the wireless network is not functioning anymore.

I deleted my profile in Network Manager and created a new one -- but this did not help.  I'm not sure what to do next...

Below are the results from running the "iwlist scan" command again.

Kevin


```

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: AC:81:12:85:48:35
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"SiPorFavor"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000010046c636
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000A5369506F724661766F72
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020005127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706313920010910
          Cell 02 - Address: 00:1A:70:7F:9E:82
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"EVH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b1c7ec3f5
                    Extra: Last beacon: 424ms ago
                    IE: Unknown: 0003455648
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:1F:33:CF:31:BA
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"nope"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001dab7e4a183
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 00046E6F7065
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B0001031047001062A5DA38EC54A56131E2117D506CDE851021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:23:F8:A6:E3:63
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL_363"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000023d17da61bb
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 00095A7958454C5F333633
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 05 - Address: 00:25:2E:02:BB:D5
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Cisco0313"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000125da4ff15f
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 0009436973636F30333133
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD07000C4301000000
          Cell 06 - Address: 68:7F:74:84:B2:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Blessed"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cb9c73c20
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 0007426C6573736564
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B0001031047001000000000000000011000687F7484B240102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B3534393432351054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 07 - Address: 00:23:F8:98:6D:FB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL_DFB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000561ad6cd636
                    Extra: Last beacon: 596ms ago
                    IE: Unknown: 00095A7958454C5F444642
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 050C020300180000000000000000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```

---

### Post by koleary on 2011-12-23
Also, I live in the United States.

Kevin

---

### Post by praseodym on 2011-12-23
There is a bug with the country code settings in 11.10:

Reboot into the old kernel (imho there was an update, hold the SHIFT-button during boot-up and choose "previous ubuntu versions" there) and:

```
sudo apt-get install iw
iw reg get
sudo iw reg set US
```
if wireless works there. Or try it with the new kernel via wired connection

---

### Post by koleary on 2011-12-23
I wasn't able to access the Internet after booting into the old kernel.  So I rebooted my netbook and accessed the Internet using my cable (I am in the new kernel now).

I ran the commands you gave me and then tested the wireless after rebooting everything.  Unfortunately my wireless is still not working.

I'm not sure if it is useful but I copied the netbook's response to the commands you just gave me.  I also ran "iwlist scan" again and copied that response too.

Kevin


```

kevin@netbook:~$ sudo apt-get install iw
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libnl1
The following NEW packages will be installed:
  iw libnl1
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 172 kB of archives.
After this operation, 565 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libnl1 amd64 1.1-6ubuntu1 [134 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe iw amd64 0.9.19-1 [37.5 kB]
Fetched 172 kB in 3s (56.9 kB/s)
Selecting previously deselected package libnl1.
(Reading database ... 149518 files and directories currently installed.)
Unpacking libnl1 (from .../libnl1_1.1-6ubuntu1_amd64.deb) ...
Selecting previously deselected package iw.
Unpacking iw (from .../archives/iw_0.9.19-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libnl1 (1.1-6ubuntu1) ...
Setting up iw (0.9.19-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
kevin@netbook:~$ iw reg get
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
kevin@netbook:~$ sudo iw reg set US
kevin@netbook:~$ 

```

```

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:CF:31:BA
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"nope"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001dc7dde5cea
                    Extra: Last beacon: 780ms ago
                    IE: Unknown: 00046E6F7065
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B0001031047001062A5DA38EC54A56131E2117D506CDE851021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: AC:81:12:85:48:35
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-25 dBm  
                    Encryption key:on
                    ESSID:"SiPorFavor"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002ad428d8
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000A5369506F724661766F72
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020009127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706313920010910
          Cell 03 - Address: 00:1A:70:7F:9E:82
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"EVH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ce2779562
                    Extra: Last beacon: 372ms ago
                    IE: Unknown: 0003455648
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

---

### Post by praseodym on 2011-12-23
Can you ping?

```
ping -c 4 192.168.15.1
ping -c 4 www.ubuntuusers.de
ping -c 4 213.95.41.11 # IP of uu.de
```

---

### Post by koleary on 2011-12-23
Here are the results of my ping attempts.

Kevin

```

kevin@netbook:~$ ping -c 4 192.168.15.1
PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.

--- 192.168.15.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3000ms

kevin@netbook:~$ ping -c 4 www.ubuntuusers.de
ping: unknown host www.ubuntuusers.de
kevin@netbook:~$ ping -c 4 213.95.41.11
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.

--- 213.95.41.11 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

```

---

### Post by praseodym on 2011-12-23
You cant even ping your own router but the wireless networks are shown?!

Right-click on the network-manager applet and edit your wireless profile->IPv4 settings. Change there from "Automatic (DHCP)" to "Automatic (DHCP), addresses only" and add the Google Public nameservers

```
8.8.8.8, 8.8.4.4
```
in "DNS-servers". Set "IPv6-settings" to "Ignore". Restart the network.

---

### Post by koleary on 2011-12-23
I made the change to the IPv4 settings that you listed (the IPv6 settings were already set to "Ignore").  After restarting my netbook I had a "poor" connection to the Internet; browsing the web was sometimes successful and sometimes I would time out.

Here are the results from running some of the ping commands again.

Kevin

```

kevin@netbook:~$ ping -c 4 192.168.15.1
PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.
64 bytes from 192.168.15.1: icmp_req=3 ttl=64 time=2.20 ms
64 bytes from 192.168.15.1: icmp_req=4 ttl=64 time=2.34 ms

--- 192.168.15.1 ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3018ms
rtt min/avg/max/mdev = 2.201/2.273/2.345/0.072 ms
kevin@netbook:~$ ping -c 4 www.ubuntuusers.de
ping: unknown host www.ubuntuusers.de
kevin@netbook:~$ ping -c 4 213.95.41.11
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.

--- 213.95.41.11 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

kevin@netbook:~$ ping -c 4 192.168.15.1
PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.
64 bytes from 192.168.15.1: icmp_req=1 ttl=64 time=2.36 ms
64 bytes from 192.168.15.1: icmp_req=2 ttl=64 time=2.18 ms
64 bytes from 192.168.15.1: icmp_req=3 ttl=64 time=97.6 ms
64 bytes from 192.168.15.1: icmp_req=4 ttl=64 time=48.9 ms

--- 192.168.15.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 2.187/37.775/97.635/39.457 ms
kevin@netbook:~$ ping -c 4 213.95.41.11
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.
64 bytes from 213.95.41.11: icmp_req=1 ttl=47 time=234 ms
64 bytes from 213.95.41.11: icmp_req=2 ttl=47 time=238 ms
64 bytes from 213.95.41.11: icmp_req=3 ttl=47 time=251 ms
64 bytes from 213.95.41.11: icmp_req=4 ttl=47 time=265 ms

--- 213.95.41.11 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 234.739/247.585/265.612/12.178 ms

```

---

### Post by praseodym on 2011-12-23
```
                    IE: WPA Version 1
                        Group Cipher : [COLOR="Red"]CCMP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="Red"]CCMP[/COLOR]
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
Did you restart the router after changing to pure WPA2? These settings show mixed mode and strange WPA(1)-settings?! Any strange letters in the key? How many letters does the key have?

---

### Post by koleary on 2011-12-23
Hi praseodym,

My key has 9 characters; it has 5 letters (in the range A-Z) and 4 numbers (in the range 0-9) in it.

At this time I have the router set to "WPA-WPA2-Mixed-PSK".  I cannot set the router to "WPA2" (see message #7 for explanation).  I did try "WPA2-PSK" earlier but, because it didn't seem to help, I changed back to "WPA-WPA2-Mixed-PSK".

I will change the router now to "WPA2-PSK" and see if that helps.

Kevin

---

### Post by praseodym on 2011-12-23
If it doesnt work you can try Wicd instead of the network-manager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```
Choose in Wicd **wlan0** as interface name and **wext** as driver. The Add-on (from one of the developers) installs several encryption templates. Wicd also works much better with mixed encryption.

---

### Post by koleary on 2011-12-24
Hi praseodym,

Switching to Wicd has given me good results.
When I was running Ubuntu 11.04 I tried Wicd and had mixed results; sometimes it worked very well and some days it worked poorly.  But with 11.10 the performance has been consistently good.

At this point I consider my Wireless problem to be solved.

Thank you very much for your help!

Kevin

---

### Post by mutrax on 2012-04-28
> **praseodym said:**
> Hi,

deactivate the hardware encryption of the driver (software encryption WEP/WPA/WPA2 not affected):

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
This is a kind of bug in 11.10

FYI
This fixes wifi timeouts on an upgraded 12.04 (precise pangolin)on a asus k50ij

---

### Post by davidtrounce on 2012-12-29
Thanks. Also upgraded to 12.04 adn got wireless enabled on Toshiba NB 305 with the fix found [here]("http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10?s=7270758b-4c79-421b-ad11-8b0b4250c807#new-answer").

---


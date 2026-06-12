---
title: "Fresh install 11.10 64bit wireless was good until update now SUPER slow"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by frettfreak on 2011-11-18
really wish Ubuntu would just figure out how to work with wireless and no issues... Ok.. i am over it..now...here is my problem

I just reinstalled ubuntu 11.10 64bit (previously had 32bit).  After install and the initial boot into the OS, wireless was working great (after i disabled power management).  ran update manager, did the recommended updates, but when i reboot, my wireless is SUPER SLOW again.  I have had this issue off and on, and googled the living crap out of it, but nothing seems to be working this time.  I have an Atheros AR928X card (wireless N)... and EVERYTHING is working speedy and well on my win7 partition so its NOT the router.

Let me know what other info you need and i will post it right away!  Thanks in advance!!

---

### Post by praseodym on 2011-11-18
Hi,

check which module is loaded:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
```
The Atheros modules **ath5k** and **ath9k** need the hardware encryption to be deactivated. Example for [COLOR="Red"]ath5k[/COLOR]:

```
echo "options [COLOR="Red"]ath5k[/COLOR] nohwcrypt=1" | sudo tee /etc/modprobe.d/[COLOR="Red"]ath5k[/COLOR].conf
sudo modprobe -rfv [COLOR="Red"]ath5k[/COLOR]
sudo modprobe -v [COLOR="Red"]ath5k[/COLOR]
```

---

### Post by frettfreak on 2011-11-18
> **praseodym said:**
> Hi,

check which module is loaded:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
```The Atheros modules **ath5k** and **ath9k** need the hardware encryption to be deactivated. Example for [COLOR=Red]ath5k[/COLOR]:

```
echo "options [COLOR=Red]ath5k[/COLOR] nohwcrypt=1" | sudo tee /etc/modprobe.d/[COLOR=Red]ath5k[/COLOR].conf
sudo modprobe -rfv [COLOR=Red]ath5k[/COLOR]
sudo modprobe -v [COLOR=Red]ath5k[/COLOR]
```

it is the 9k.  I ran the 3 options you gave, but put a 9 where the 5 was.  I dont see any difference at the moment.  Gonna reboot and see if that does anything.

---

### Post by praseodym on 2011-11-18
Check after that:

```
iwconfig
lsmod
dmesg | grep ath
sudo iwlist scan
ifconfig wlan0
cat /etc/resolv.conf
```

---

### Post by frettfreak on 2011-11-18
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MSMK-N"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:4A:3F:4A   
          Bit Rate=117 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:46   Missed beacon:0

```

lsmod:

```
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
nvidia              11713772  40 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
psmouse                73882  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 127538  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57901  0 
uas                    18027  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 
```

dmesg | grep ath

```
[   13.064862] ath9k 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.064875] ath9k 0000:04:00.0: setting latency timer to 64
[   13.494080] ath: EEPROM regdomain: 0x6a
[   13.494083] ath: EEPROM indicates we should expect a direct regpair map
[   13.494087] ath: Country alpha2 being used: 00
[   13.494088] ath: Regpair used: 0x6a
[   13.522808] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.523447] Registered led device: ath9k-phy0
[   14.752799] type=1400 audit(1321654727.729:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=982 comm="apparmor_parser"
```

sudo iwlist scan

```
wlan0     Scan completed :
          Cell 01 - Address: 00:26:62:13:66:04
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"MIKES-WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e8145e551
                    Extra: Last beacon: 4444ms ago
                    IE: Unknown: 000A4D494B45532D574C414E
                    IE: Unknown: 010882848B96A4B0C8EC
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C9298E0
                    IE: Unknown: DD090010180200F0000000
          Cell 02 - Address: 00:25:9C:4A:3F:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"MSMK-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e7027c183
                    Extra: Last beacon: 608ms ago
                    IE: Unknown: 00064D534D4B2D4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B00010310470010B4A088A439115A6C3F64A9BEEE5DE97B102100104C696E6B73797320627920436973636F102300075752543631304E1024000876322E30302E30311042000234321054000800060050F2040001101100075752543631304E100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080400000000000000000000000000000000000000
          Cell 03 - Address: 00:18:01:AA:31:B8
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"DirtyNastyVirus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf7be1aaa4
                    Extra: Last beacon: 4024ms ago
                    IE: Unknown: 000F44697274794E617374795669727573
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

ifconfig wlan0

```
wlan0     Link encap:Ethernet  HWaddr 00:21:00:e1:1f:41  
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fee1:1f41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6676734 (6.6 MB)  TX bytes:576466 (576.4 KB)
```

cat /etc/resolv.conf

```
# Generated by NetworkManager
domain domain_not_set.invalid
search domain_not_set.invalid
nameserver 192.168.1.1
nameserver 68.238.64.12

```

i am not really sure what i am supposed to be looking for, but here are the results.

---

### Post by praseodym on 2011-11-18
The network ESSID:"MSMK-N" uses mixed WPA/WPA2 encryption, this causes problems with the network-manager. Try pure WPA2-AES instead.

---

### Post by frettfreak on 2011-11-18
> **praseodym said:**
> The network ESSID:"MSMK-N" uses mixed WPA/WPA2 encryption, this causes problems with the network-manager. Try pure WPA2-AES instead.

You are awesome!  Everything is working great!!!  THANK YOU VERY VERY MUCH!!!!

---


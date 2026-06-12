---
title: "rt3090 Wireless connection problem in 11.10"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by kpuz on 2012-01-08
Hi, 
I am having connection problems with my wireless configuration with the rt3090 wireless card.  The iwconfig command shows a very high number of 'Tx excessive retries' and 'invalid misc'.

```
kpuz@kpuz-ibm:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"jungle_fish2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:C1:3C:B9   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:48  Invalid misc:54   Missed beacon:0

```

The Bit Rate of 18Mbps is also weird because I am supposed to be getting 54mbps.  When I was running ubuntu 11.04 on a 2.xx kernel the wireless worked well at 54Mbps with the rt2860sta module.  But with the 3.0xx kernel the module that is loading is the rt2800pci.  I was wondering if I can revert back to the old module or if there is a fix for the current module (rt2800pci) that I can apply.  I have searched and have not had any luck.

---

### Post by wildmanne39 on 2012-01-08
Hi, please try what is in post 7 of this thread.
[http://ubuntuforums.org/showthread.php?t=1905330&highlight=rt2800pci](http://ubuntuforums.org/showthread.php?t=1905330&highlight=rt2800pci)
You do not need to do the first command just all the others.
Thanks

---

### Post by kpuz on 2012-01-08
> **wildmanne39 said:**
> Hi, please try what is in post 7 of this thread.
[http://ubuntuforums.org/showthread.php?t=1905330&highlight=rt2800pci](http://ubuntuforums.org/showthread.php?t=1905330&highlight=rt2800pci)
You do not need to do the first command just all the others.
Thanks
Thanks for the quick reply wildmanne39.

I just finished with those commands but the problem persists.  
```
kpuz@kpuz-ibm:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"jungle_fish2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:C1:3C:B9   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:584  Invalid misc:32   Missed beacon:0

```

---

### Post by UltimateCat on 2012-01-08
> **kpuz said:**
> Hi, 
I am having connection problems with my wireless configuration with the rt3090 wireless card.  The iwconfig command shows a very high number of 'Tx excessive retries' and 'invalid misc'.

```
kpuz@kpuz-ibm:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"jungle_fish2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:C1:3C:B9   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:48  Invalid misc:54   Missed beacon:0

```The Bit Rate of 18Mbps is also weird because I am supposed to be getting 54mbps.  When I was running ubuntu 11.04 on a 2.xx kernel the wireless worked well at 54Mbps with the rt2860sta module.  But with the 3.0xx kernel the module that is loading is the rt2800pci.  I was wondering if I can revert back to the old module or if there is a fix for the current module (rt2800pci) that I can apply.  I have searched and have not had any luck.

I had the exact same problem for 6 weeks.  Once I installed the driver for my NIC RT8168....and installed Ndiswrapper I now have an internet connection.
Maybe your internal card needs a driver. Hope this was helpful.
UltimateCat:p

---

### Post by wildmanne39 on 2012-01-08
Hi, please try this:
```
gksudo gedit /etc/modprobe.d/mac80211.conf
```
Add this line:
```
options mac80211 probe_wait_ms=1000
```
Proofread carefully, save and close gedit and reboot.
Thanks

---

### Post by kpuz on 2012-01-09
That didn't work either wildmanne39.

```
wlan0     IEEE 802.11bgn  ESSID:"jungle_fish2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:C1:3C:B9   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:38   Missed beacon:0
```

---

### Post by wildmanne39 on 2012-01-09
Hi, please post the contents of:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
Thanks

---

### Post by kpuz on 2012-01-09
> **wildmanne39 said:**
> Hi, please post the contents of:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
Thanks

options rt2800pci nohwcrypt=1

---

### Post by wildmanne39 on 2012-01-09
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
sudo ifup wlan0
sudo iwlist scan
lsmod | grep rt2
```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by kpuz on 2012-01-09
Here's the output.  



```
kpuz@kpuz-ibm:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux kpuz-ibm 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
kpuz@kpuz-ibm:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lenovo Device [17aa:f101]
	Kernel driver in use: rt2800pci
kpuz@kpuz-ibm:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b272 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 
kpuz@kpuz-ibm:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"jungle_fish2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:C1:3C:B9   
          Bit Rate=12 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12977  Invalid misc:75   Missed beacon:0

kpuz@kpuz-ibm:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
kpuz@kpuz-ibm:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
xt_limit               12711  12 
xt_tcpudp              12603  18 
xt_addrtype            12713  4 
xt_state               12578  14 
snd_hda_codec_conexant    62197  1 
snd_hda_codec_hdmi     32040  1 
sp5100_tco             13791  0 
joydev                 17693  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25890  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           82342  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
rts5139               351143  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_hda_intel          33390  4 
mac80211              462092  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_codec         104802  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              199587  2 rt2x00lib,mac80211
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
k10temp                13166  0 
eeprom_93cx6           12725  1 rt2800pci
i2c_piix4              13301  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
radeon               1016226  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
snd                    68266  18 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   236290  4 radeon,ttm,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
i2c_algo_bit           13423  1 radeon
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
kpuz@kpuz-ibm:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:6F:84:AD

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [jungle_fish2] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        CC:AF:78:53:4F:6A

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MightyDucks:     Infra, 3C:EA:4F:1C:44:D9, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP
    ExtraPulp:       Infra, 00:22:2D:5A:85:E1, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    2mid:            Infra, 00:26:F3:1E:E9:21, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    Kati B's Network:Infra, 00:25:BC:88:75:83, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Rogers01839:     Infra, 38:60:77:3B:3D:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Kati B's Guest Network: Infra, 06:25:BC:88:75:83, Freq 2417 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    *jungle_fish2:   Infra, 78:CD:8E:C1:3C:B9, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA

  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


kpuz@kpuz-ibm:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

kpuz@kpuz-ibm:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 78:CD:8E:C1:3C:B9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"jungle_fish2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bf825c62fd
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000C6A756E676C655F6669736832
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504001F127A
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
          Cell 02 - Address: 78:CD:8E:C1:3C:BA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bf8259584f
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504001F127A
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: 38:60:77:3B:3D:59
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Rogers01839"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d4d626526d
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 000B526F676572733031383339
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 06:25:BC:88:75:83
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Kati B's Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000040f1113180
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 00164B61746920422773204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602080000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016D0208
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F207000101060025BC887584
          Cell 05 - Address: 00:25:BC:88:75:83
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Kati B's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000040f11a9180
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 00104B61746920422773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602080000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016D0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F207000101060025BC887584
          Cell 06 - Address: 00:22:2D:5A:85:E1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ExtraPulp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017cd55c171
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0009457874726150756C70
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001E127A
                    IE: Unknown: DD07000C4304000000
          Cell 07 - Address: 00:22:2D:5A:85:E2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017cd55ca03
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001E127A
                    IE: Unknown: DD07000C4304000000

kpuz@kpuz-ibm:~$ lsmod | grep rt2
rt2800pci              18715  0 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              462092  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
kpuz@kpuz-ibm:~$ sudo cat /var/log/syslog | grep -e rt2 -e firmware -e wpa -e wlan -e etork | tail -n75
Jan  9 18:25:43 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  9 18:25:43 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  9 18:25:43 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  9 18:25:43 kpuz-ibm NetworkManager[1006]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  9 18:25:43 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0/wireless): connection 'jungle_fish2' has security, and secrets exist.  No new secrets needed.
Jan  9 18:25:43 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  9 18:25:44 kpuz-ibm NetworkManager[1006]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan  9 18:25:45 kpuz-ibm wpa_supplicant[1228]: Trying to authenticate with 78:cd:8e:c1:3c:b9 (SSID='jungle_fish2' freq=2412 MHz)
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  9 18:25:45 kpuz-ibm kernel: [   22.669980] wlan0: authenticate with 78:cd:8e:c1:3c:b9 (try 1)
Jan  9 18:25:45 kpuz-ibm kernel: [   22.671720] wlan0: authenticated
Jan  9 18:25:45 kpuz-ibm wpa_supplicant[1228]: Trying to associate with 78:cd:8e:c1:3c:b9 (SSID='jungle_fish2' freq=2412 MHz)
Jan  9 18:25:45 kpuz-ibm kernel: [   22.672541] wlan0: associate with 78:cd:8e:c1:3c:b9 (try 1)
Jan  9 18:25:45 kpuz-ibm kernel: [   22.675363] wlan0: RX AssocResp from 78:cd:8e:c1:3c:b9 (capab=0xc11 status=0 aid=2)
Jan  9 18:25:45 kpuz-ibm kernel: [   22.675372] wlan0: associated
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  9 18:25:45 kpuz-ibm kernel: [   22.677651] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  9 18:25:45 kpuz-ibm wpa_supplicant[1228]: Associated with 78:cd:8e:c1:3c:b9
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): supplicant interface state: associating -> associated
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan  9 18:25:45 kpuz-ibm wpa_supplicant[1228]: WPA: Key negotiation completed with 78:cd:8e:c1:3c:b9 [PTK=TKIP GTK=TKIP]
Jan  9 18:25:45 kpuz-ibm wpa_supplicant[1228]: CTRL-EVENT-CONNECTED - Connection to 78:cd:8e:c1:3c:b9 completed (auth) [id=0 id_str=]
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'jungle_fish2'.
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  9 18:25:45 kpuz-ibm dhclient: Listening on LPF/wlan0/cc:af:78:53:4f:6a
Jan  9 18:25:45 kpuz-ibm dhclient: Sending on   LPF/wlan0/cc:af:78:53:4f:6a
Jan  9 18:25:45 kpuz-ibm dhclient: DHCPREQUEST of 192.168.0.15 on wlan0 to 255.255.255.255 port 67
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan  9 18:25:45 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  9 18:25:45 kpuz-ibm avahi-daemon[1000]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.15.
Jan  9 18:25:45 kpuz-ibm avahi-daemon[1000]: New relevant interface wlan0.IPv4 for mDNS.
Jan  9 18:25:45 kpuz-ibm avahi-daemon[1000]: Registering new address record for 192.168.0.15 on wlan0.IPv4.
Jan  9 18:25:46 kpuz-ibm NetworkManager[1006]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan  9 18:25:46 kpuz-ibm NetworkManager[1006]: <info> Policy set 'jungle_fish2' (wlan0) as default for IPv4 routing and DNS.
Jan  9 18:25:46 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) successful, device activated.
Jan  9 18:25:46 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  9 18:25:46 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  9 18:25:46 kpuz-ibm avahi-daemon[1000]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::ceaf:78ff:fe53:4f6a.
Jan  9 18:25:46 kpuz-ibm avahi-daemon[1000]: New relevant interface wlan0.IPv6 for mDNS.
Jan  9 18:25:46 kpuz-ibm avahi-daemon[1000]: Registering new address record for fe80::ceaf:78ff:fe53:4f6a on wlan0.*.
Jan  9 18:25:47 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Jan  9 18:25:47 kpuz-ibm NetworkManager[1006]: <error> [1326151547.499114] [nm-device.c:1784] dhcp6_start(): (wlan0): failed to add IPv6 multicast route: Object not found
Jan  9 18:25:47 kpuz-ibm NetworkManager[1006]: <info> Activation (wlan0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Jan  9 18:25:47 kpuz-ibm dhclient: Listening on Socket/wlan0
Jan  9 18:25:47 kpuz-ibm dhclient: Sending on   Socket/wlan0
Jan  9 18:25:47 kpuz-ibm NetworkManager[1006]: <info> (wlan0): DHCPv6 state changed nbi -> preinit6
Jan  9 18:25:48 kpuz-ibm dhclient: XMT: Solicit on wlan0, interval 1030ms.
Jan  9 18:25:49 kpuz-ibm dhclient: XMT: Solicit on wlan0, interval 2000ms.
Jan  9 18:25:51 kpuz-ibm dhclient: XMT: Solicit on wlan0, interval 4060ms.
Jan  9 18:25:55 kpuz-ibm dhclient: XMT: Solicit on wlan0, interval 7860ms.
Jan  9 18:26:03 kpuz-ibm dhclient: XMT: Solicit on wlan0, interval 15990ms.
Jan  9 18:26:19 kpuz-ibm dhclient: XMT: Solicit on wlan0, interval 32290ms.
Jan  9 18:26:32 kpuz-ibm NetworkManager[1006]: <warn> (wlan0): DHCPv6 request timed out.
Jan  9 18:26:32 kpuz-ibm NetworkManager[1006]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1544
Jan  9 18:49:21 kpuz-ibm kernel: [ 1438.839402] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:24:81:ba:07:a3:08:00 SRC=192.168.0.13 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=2200 PROTO=2 
Jan  9 19:11:28 kpuz-ibm wpa_supplicant[1228]: WPA: Group rekeying completed with 78:cd:8e:c1:3c:b9 [GTK=TKIP]
Jan  9 20:11:31 kpuz-ibm wpa_supplicant[1228]: WPA: Group rekeying completed with 78:cd:8e:c1:3c:b9 [GTK=TKIP]
Jan  9 20:32:46 kpuz-ibm kernel: [ 7644.106825] [UFW BLOCK] IN=wlan0 OUT= MAC=cc:af:78:53:4f:6a:78:cd:8e:c1:3c:b7:08:00 SRC=72.21.214.36 DST=192.168.0.15 LEN=40 TOS=0x00 PREC=0x00 TTL=245 ID=36772 DF PROTO=TCP SPT=80 DPT=44316 WINDOW=127 RES=0x00 ACK FIN URGP=0 
Jan  9 20:57:20 kpuz-ibm kernel: [ 9117.922104] [UFW BLOCK] IN=wlan0 OUT= MAC=cc:af:78:53:4f:6a:78:cd:8e:c1:3c:b7:08:00 SRC=50.18.172.187 DST=192.168.0.15 LEN=89 TOS=0x00 PREC=0x00 TTL=49 ID=4648 DF PROTO=TCP SPT=443 DPT=43638 WINDOW=31 RES=0x00 ACK PSH URGP=0 
Jan  9 20:57:22 kpuz-ibm kernel: [ 9119.903062] [UFW BLOCK] IN=wlan0 OUT= MAC=cc:af:78:53:4f:6a:78:cd:8e:c1:3c:b7:08:00 SRC=50.18.172.187 DST=192.168.0.15 LEN=89 TOS=0x00 PREC=0x00 TTL=49 ID=4649 DF PROTO=TCP SPT=443 DPT=43638 WINDOW=31 RES=0x00 ACK PSH URGP=0 
Jan  9 20:57:30 kpuz-ibm kernel: [ 9127.654855] [UFW BLOCK] IN=wlan0 OUT= MAC=cc:af:78:53:4f:6a:78:cd:8e:c1:3c:b7:08:00 SRC=50.18.172.187 DST=192.168.0.15 LEN=89 TOS=0x00 PREC=0x00 TTL=49 ID=4652 DF PROTO=TCP SPT=443 DPT=43638 WINDOW=31 RES=0x00 ACK PSH URGP=0 
Jan  9 20:57:40 kpuz-ibm kernel: [ 9137.840237] [UFW BLOCK] IN=wlan0 OUT= MAC=cc:af:78:53:4f:6a:78:cd:8e:c1:3c:b7:08:00 SRC=50.18.172.187 DST=192.168.0.15 LEN=89 TOS=0x00 PREC=0x00 TTL=49 ID=4653 DF PROTO=TCP SPT=443 DPT=43638 WINDOW=31 RES=0x00 ACK PSH URGP=0 
Jan  9 20:58:44 kpuz-ibm kernel: [ 9201.776284] [UFW BLOCK] IN=wlan0 OUT= MAC=cc:af:78:53:4f:6a:78:cd:8e:c1:3c:b7:08:00 SRC=50.18.172.187 DST=192.168.0.15 LEN=89 TOS=0x00 PREC=0x00 TTL=49 ID=4655 DF PROTO=TCP SPT=443 DPT=43638 WINDOW=31 RES=0x00 ACK PSH URGP=0 
Jan  9 21:11:31 kpuz-ibm wpa_supplicant[1228]: WPA: Group rekeying completed with 78:cd:8e:c1:3c:b9 [GTK=TKIP]
Jan  9 22:11:31 kpuz-ibm wpa_supplicant[1228]: WPA: Group rekeying completed with 78:cd:8e:c1:3c:b9 [GTK=TKIP]
Jan  9 23:11:32 kpuz-ibm wpa_supplicant[1228]: WPA: Group rekeying completed with 78:cd:8e:c1:3c:b9 [GTK=TKIP]

```

---

### Post by wildmanne39 on 2012-01-10
Hi, two more things to do, you have more then one issue so we are working on them one at a time.
```
gksudo gedit /etc/pm/power.d/wireless
```
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```
Save, gedit and exit, then make sure your settings ae set like the screenshots I am including except leave yours set to auto connect.
Then reboot

I probably will not be on much today because it is my birthday.
Thanks

---

### Post by kpuz on 2012-01-10
Done.  I'm still getting 
```
kpuz@kpuz-ibm:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"jungle_fish2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:C1:3C:B9   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:36   Missed beacon:0
```

---

### Post by wildmanne39 on 2012-01-10
Hi, besides the messages does your internet perform poorly?
Thanks

---

### Post by kpuz on 2012-01-10
It performs poorly when I am at home where I have a slower internet (7mbps).  In fact, as soon as I log on, the router starts to slow down the connection for everyone that is connected.  At work however, where the internet is fast, I don't have any problem.

---

### Post by wildmanne39 on 2012-01-10
Hi, first 7 mbs is not that fast so you may experience slow down with other computers on your network but you should not be getting the messages, do you have the messages at work?

You should change your network name and see if that helps, take the line out, sometimes special characters causes problems for linux.

Also if you can change your encryption in your router to just wpa2 and not wpa or wep or wpa/wpa2 it works better for linux.
Thanks

---

### Post by kpuz on 2012-02-20
After giving up on this issue I found someone who had compiled the 3090 driver provided by Ralink (which happens to be the same RT2860STA driver that worked so well before the kernel upgrade to 3.0) on post 71 on this thread: [http://ubuntuforums.org/showthread.php?t=1849602&page=8](http://ubuntuforums.org/showthread.php?t=1849602&page=8).  I compiled the Ralink driver and don't get any more Tx excessive retries or Misc Invalids.  There is also no more slowdown of the internet and I'm getting great speeds.  I will update when I am able to test for wireless n speeds on my work router.  Hope this is able to help someone else out.

---


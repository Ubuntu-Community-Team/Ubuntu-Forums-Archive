---
title: "wireless network detected but connection failed"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by shahin_67 on 2011-10-31
hey guys,

I've been using ubuntu 11.10 for few days. first my wireless card wasn't compatible with the os such that I settled the problem [this way]("http://ubuntuforums.org/showpost.php?p=11372158&postcount=4"). (my machine is a dell vostro 1500 laptop) but now wireless networks are detected but I fail to connect them. I tried [this post]("http://ubuntuforums.org/showthread.php?t=571188") and many other semi-command posts (wep section) but they didn't work either. any help is welcome.

thanks ahead,

ps1, my *security* type is *wep 128-bit* key. *wep index* is *1(default)* and *authentication* is *open system*. in *ipv4 settings* tab the *method* is chosen *automatic (dhcp)* and the field of *dhcp client id* is left *blank*. 

ps2, chance of any mistake with password entering or any other configuration to the modem is very low because all these settings go well in windows wireless connection sections.

---

### Post by shahin_67 on 2011-10-31
hey guy,

as it seems my problem is a quirky one, is there any code to return my wireless interface things log? apparently it doesn't have any problem. i type ifconfig, iwconfig and iwlist but everything goes well! by the way, since installation of the firmware i mentioned above --to have my wireless card compatible with the os-- i come across some "full network things didn't get configured fully" message when booting the os. hope someone can help me!

thanks ahead,
ps, i have no problem with wired connection!

---

### Post by shahin_67 on 2011-10-31
hey guys,

i seem to have finally found what i need in [this guide]("http://ubuntuforums.org/showthread.php?t=193350"). unfortunately it's an old post and some commands or versions which were used should have been probably changed since then. someone please take a look at the code scripts and refurbish them in a ubuntu 11.10 applicable fashion. btw, i installed broadcom b43 driver and firmware. so first off i need to remove them too.

thanks ahead,

---

### Post by wildmanne39 on 2011-10-31
Hi, I think you need to wait and post some information so you can get help.

If you manually configured your connection then you need to undo that so network manager can do its job, there is almost no need to manually congfigure these days unless you are setting up a server.

Please post the results of:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by shahin_67 on 2011-10-31
hey wilmanne39,

cat /etc/lsb-release; uname -a:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10

```nm - tool:
```
NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unmanaged
  Default:           no
  HW Address:        00:1C:23:AF:4D:FF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

```lspci -nnk | grep -iA2 net:
```

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

```iwconfig:
```

lo        no wireless extensions.

eth1      no wireless extensions.

ppp0      no wireless extensions.

```rfkill list all:
```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```sudo iwlist scan:
```

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

```lsmod:
```

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
xt_TCPMSS              12619  1 
xt_tcpmss              12453  1 
xt_tcpudp              12531  1 
iptable_mangle         12646  1 
ip_tables              18106  1 iptable_mangle
x_tables               21975  5 xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_mangle,ip_tables
pppoe                  17513  2 
pppox                  13158  1 pppoe
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_idt      60049  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
nouveau               663211  3 
psmouse                73673  0 
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
serio_raw              12990  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
drm                   192226  5 nouveau,ttm,drm_kms_helper
mtd                    35852  2 sm_common,nand
snd_seq_midi           13132  0 
b44                    31443  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ssb                    50682  1 b44
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wl                   2646601  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
wmi                    18744  2 dell_wmi,mxm_wmi
lib80211               14570  1 wl
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 nouveau
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   21634  2 
libahci                25727  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

```as you see I removed b43 driver and firmware. before removing them, I installed sta from additional drivers then deactivated b43 and activated wl(sta) the result was that I wasn't able to see(detect) wireless networks around
```

modprobe -r b43
modprobe wl

```afterwards I activated b43 and deactivated wl(sta). this time networks were detectable but the authentication processes failed. (main problem) 
```

modprobe -r wl
modprobe b43

```I hope these hints help to understand the problem.

thanks ahead,

---

### Post by wildmanne39 on 2011-10-31
Hi, please try this:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
When the install is done unplug wired connection and run:
```
sudo modprobe b43
```
It will work better with wpa2 only encryption.

If it does not work post the results of all those commands again we need to see them with the b43 driver installed because it is the correct driver.
Thank you

---

### Post by shahin_67 on 2011-11-01
hey mate,

my problem didn't get fixed, I did what you recommended though. as you told the firmware b43 would work better with wpa2 I configured my router to wpa2 personal encryption. it started working well in my windows 7 environment so security won't be the case anymore.

cat /etc/lsb-release; uname -a:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

```nm-tool:
```
NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unmanaged
  Default:           no
  HW Address:        00:1C:23:AF:4D:FF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:1D:60:BF:23:6C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Nowin:           Infra, 00:25:68:B9:AB:F0, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    princess:        Infra, 40:4D:8E:CF:E6:57, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Parmida:         Infra, 40:4A:03:DA:6B:C7, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    ASUS:            Infra, 00:23:54:0F:D3:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2
    REZA ZADEH:      Infra, F4:EC:38:F5:BE:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    D72:             Infra, 00:22:6B:EB:43:2F, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA
    Symphony:        Infra, F4:3E:61:05:70:DF, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA

```lspci -nnk | grep -iA2 net:
```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

```iwconfig:
```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

```rfkill list all:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```sudo iwlist scan:
```
o        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:54:0F:D3:6E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000059a2e4e2
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000441535553
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
          Cell 02 - Address: 00:22:6B:EB:43:2F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"D72"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000248f40c300
                    Extra: Last beacon: 6692ms ago
                    IE: Unknown: 0003443732
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 070A465200010D14010D1400
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
          Cell 03 - Address: F4:3E:61:05:70:DF
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Symphony"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000206733e183
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 000853796D70686F6E79
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 40:4D:8E:CF:E6:57
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"princess"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002d9fb16a
                    Extra: Last beacon: 1288ms ago
                    IE: Unknown: 00087072696E63657373
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880404D8ECFE657103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000012127A
                    IE: Unknown: DD1E00904C338E1103FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000

ppp0      Interface doesn't support scanning.

```lsmod:
```
Module                  Size  Used by
xt_TCPMSS              12619  1 
xt_tcpmss              12453  1 
xt_tcpudp              12531  1 
iptable_mangle         12646  1 
ip_tables              18106  1 iptable_mangle
x_tables               21975  5 xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_mangle,ip_tables
pppoe                  17513  2 
pppox                  13158  1 pppoe
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
arc4                   12473  2 
videodev               85626  1 uvcvideo
b43                   318816  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               663211  3 
mac80211              272785  1 b43
r852                   17901  0 
sm_common              16737  1 r852
psmouse                73673  0 
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
serio_raw              12990  0 
mtd                    35852  2 sm_common,nand
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 b43,mac80211
soundcore              12600  1 snd
ttm                    65224  1 nouveau
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 nouveau
drm                   192226  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
binfmt_misc            17292  1 
wmi                    18744  2 dell_wmi,mxm_wmi
video                  18908  1 nouveau
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
b44                    31443  0 
ahci                   21634  2 
libahci                25727  1 ahci
firewire_ohci          35854  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50682  2 b43,b44

```

the problem is still the same. my wirelss nic gets to spot networks around but it fails to connect when I click the network name. i have made appropriate settings i.e., changing security from wep to wpa2 personal with correct passphrase. other settings are still the same i.e., bssid, ssid, mac address. 

thanks ahead,

---

### Post by wildmanne39 on 2011-11-01
Hi, it is scanning for networks.

What is the name of the network you are trying to connect too?

Please post the results of:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etwork | tail -n55
```
Thank you

---

### Post by shahin_67 on 2011-11-02
hi wildmanne39, 

I'm trying to connect to ASUS --Cell 01. 

sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etwork | tail -n55:
```
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]:    Ifupdown: get unmanaged devices count: 2
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver (unknown))
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0/net/wlan0, iface: wlan0)
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/dell-laptop/rfkill/rfkill1) (driver dell-laptop)
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov  2 11:22:25 shahin-Vostro-1500 dbus[521]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Nov  2 11:22:25 shahin-Vostro-1500 dbus[521]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> wpa_supplicant started
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> (wlan0): supplicant interface state: starting -> ready
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 11:22:25 shahin-Vostro-1500 NetworkManager[558]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov  2 11:22:28 shahin-Vostro-1500 NetworkManager[558]: <info> (eth1): carrier now ON (device state 10)
Nov  2 11:22:30 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  2 11:22:30 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov  2 11:22:31 shahin-Vostro-1500 kernel: [   30.192097] type=1400 audit(1320220351.573:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1040 comm="apparmor_parser"
Nov  2 11:22:32 shahin-Vostro-1500 NetworkManager[558]: <warn> bluez error getting default adapter: No such adapter
Nov  2 11:24:22 shahin-Vostro-1500 NetworkManager[558]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 11:24:52  NetworkManager[558]: last message repeated 2 times
Nov  2 11:25:02 shahin-Vostro-1500 NetworkManager[558]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 11:25:23 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:25:23 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:25:23 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:25:53 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:25:53 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:25:54 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:26:22 shahin-Vostro-1500 NetworkManager[558]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 11:26:24 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:26:24 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:26:24 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:26:54 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:26:54 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:26:54 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:27:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:27:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:27:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:27:55 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:27:55 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:27:55 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:28:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:28:25 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:28:34 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:29:04 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:29:04 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:29:05 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:29:35 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:29:35 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:29:36 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:30:06 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Nov  2 11:30:06 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Nov  2 11:30:06 shahin-Vostro-1500 NetworkManager[558]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
```I'd appreciate your helps mate.

---

### Post by wildmanne39 on 2011-11-02
Hi, I recommend installing wicd from synaptic or software center then get rid of net work manager with this command please but not before you install wicd.
Reboot
```
sudo apt-get purge network-manager network-manager-gnome
```
Thank you

---

### Post by shahin_67 on 2011-11-03
hey,

I did what you said. but when I connect to my home wireless network through wicd, the manager gets stuck is the phase *obtaining ip address*. I pressed the properties button of the network having four check boxes: Use Static IPs, Use Static DNS, Use these settings for all networks sharing this essid, Use encryption. I just applied settings to encryption --wpa 1/2 passphrase. 

sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e wpa -e etwork | tail -n55: (gnome network manager uninstalled, wcid installed)

```
Nov  3 07:56:17 shahin-Vostro-1500 avahi-daemon[868]: Interface wlan0.IPv6 no longer relevant for mDNS.
Nov  3 07:56:17 shahin-Vostro-1500 avahi-daemon[868]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21d:60ff:febf:236c.
Nov  3 07:56:17 shahin-Vostro-1500 avahi-daemon[868]: Withdrawing address record for fe80::21d:60ff:febf:236c on wlan0.
Nov  3 07:57:07 shahin-Vostro-1500 dhclient: Listening on LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:07 shahin-Vostro-1500 dhclient: Sending on   LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:07 shahin-Vostro-1500 kernel: [  500.428158] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Nov  3 07:57:07 shahin-Vostro-1500 kernel: [  500.529461] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 07:57:08 shahin-Vostro-1500 kernel: [  500.788152] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Nov  3 07:57:08 shahin-Vostro-1500 kernel: [  500.889295] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 07:57:08 shahin-Vostro-1500 pppd[864]: error receiving pppoe packet: Network is down
Nov  3 07:57:08 shahin-Vostro-1500 dhclient: Listening on LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:08 shahin-Vostro-1500 dhclient: Sending on   LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:08 shahin-Vostro-1500 kernel: [  501.460252] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Nov  3 07:57:08 shahin-Vostro-1500 kernel: [  501.565313] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 07:57:11 shahin-Vostro-1500 kernel: [  503.925149] wlan0: authenticate with 00:23:54:0f:d3:6e (try 1)
Nov  3 07:57:11 shahin-Vostro-1500 kernel: [  503.926857] wlan0: authenticated
Nov  3 07:57:11 shahin-Vostro-1500 kernel: [  503.926909] wlan0: associate with 00:23:54:0f:d3:6e (try 1)
Nov  3 07:57:11 shahin-Vostro-1500 kernel: [  503.929095] wlan0: RX AssocResp from 00:23:54:0f:d3:6e (capab=0x411 status=0 aid=1)
Nov  3 07:57:11 shahin-Vostro-1500 kernel: [  503.929107] wlan0: associated
Nov  3 07:57:11 shahin-Vostro-1500 kernel: [  503.937127] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov  3 07:57:12 shahin-Vostro-1500 dhclient: Listening on LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:12 shahin-Vostro-1500 dhclient: Sending on   LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:12 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  3 07:57:13 shahin-Vostro-1500 avahi-daemon[868]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21d:60ff:febf:236c.
Nov  3 07:57:13 shahin-Vostro-1500 avahi-daemon[868]: New relevant interface wlan0.IPv6 for mDNS.
Nov  3 07:57:13 shahin-Vostro-1500 avahi-daemon[868]: Registering new address record for fe80::21d:60ff:febf:236c on wlan0.*.
Nov  3 07:57:15 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Nov  3 07:57:18 shahin-Vostro-1500 dhclient: Listening on LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:18 shahin-Vostro-1500 dhclient: Sending on   LPF/wlan0/00:1d:60:bf:23:6c
Nov  3 07:57:18 shahin-Vostro-1500 kernel: [  511.534732] wlan0: deauthenticating from 00:23:54:0f:d3:6e by local choice (reason=3)
Nov  3 07:57:19 shahin-Vostro-1500 avahi-daemon[868]: Interface wlan0.IPv6 no longer relevant for mDNS.
Nov  3 07:57:19 shahin-Vostro-1500 avahi-daemon[868]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21d:60ff:febf:236c.
Nov  3 07:57:19 shahin-Vostro-1500 avahi-daemon[868]: Withdrawing address record for fe80::21d:60ff:febf:236c on wlan0.
Nov  3 08:00:42 shahin-Vostro-1500 kernel: [  715.548358] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Nov  3 08:00:43 shahin-Vostro-1500 kernel: [  715.653396] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 08:00:43 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  3 08:00:45 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Nov  3 08:00:54 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov  3 08:01:00 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov  3 08:01:08 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov  3 08:01:21 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Nov  3 08:01:37 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Nov  3 08:01:53 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Nov  3 08:02:03 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Nov  3 08:02:17 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Nov  3 08:02:38 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Nov  3 08:02:47 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Nov  3 08:03:03 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Nov  3 08:03:18 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Nov  3 08:03:37 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Nov  3 08:03:49 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Nov  3 08:04:09 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Nov  3 08:04:25 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Nov  3 08:04:39 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Nov  3 08:05:01 shahin-Vostro-1500 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15

```ps, rebooting after uninstallation and installation, turning off and on the router and ... done!

---

### Post by wildmanne39 on 2011-11-03
Hi, it looks like it fixed the problem you were having set your encryption to just wpa2 if you can in wicd and your router if not make sure your router setting for encryption matches the setting in wicd and  make sure your dhclient is dhcpcd instead.
Thank you

---

### Post by shahin_67 on 2011-11-07
hi,

as I once said security things are not the case no longer. (my router security is configured to wpa2 personal.) as of dhcpcd, I typed the command in terminal but it wasn't recognized! 

input:
```
sudo dhcpcd wlan0
```

output:
```
sudo: dhcpcd: command not found
``` 

how can I fix it?

thanks ahead,

---

### Post by wildmanne39 on 2011-11-07
Hi, you should be able to setup up dhcpcd in the wicd manager and if that does not work set a static ip.
Thank you

---


---
title: "Broadcom 4312 cant connect to WPA network"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by benjoo on 2012-11-14
Hey everyone,

im running Ubuntu 12.10 32bit - 3.5.0-18-generic i686 on a Dell Studio 1558 with Core i5-520m, 4gb ram, hd 5470 mobility and a dell mini 1397 wireless card.
The first attempt of connecting to the wpa-secured network succeeds but the connection went down shortly after. 
The following attemps are not successful resulting in a loop of "the entered key is incorrect".

Since i cannot connect to my wpa network at home i tried the workarounds given on linuxwireless.org with no efforts.
Currently im using a lan cable to provide the connection to my router. 
Sometimes a connection is built up but no data can be transmitted and the connection shortly after went down.

Below this i added some logs maybe some of you can read anything out of them.

```

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

```
ben-Studio-1558:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:53:72:29  
          inet addr:192.168.178.45  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:fe53:7229/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47154825 (47.1 MB)  TX bytes:1206772 (1.2 MB)

eth1      Link encap:Ethernet  HWaddr 1c:65:9d:56:9f:d9  
          inet addr:192.168.178.39  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe56:9fd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:1243
          TX packets:90 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13345 (13.3 KB)  TX bytes:18890 (18.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61800 (61.8 KB)  TX bytes:61800 (61.8 KB) 
```

```
 lsmod
Module                  Size  Used by
michael_mic            12540  8 
arc4                   12473  4 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
joydev                 17161  0 
lib80211_crypt_tkip    17229  0 
wl                   2442848  0 
snd_hda_codec_hdmi     31423  1 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
psmouse                84843  0 
snd_hda_codec_idt      59761  1 
snd_hda_intel          32515  5 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
video                  18847  0 
wmi                    18590  1 dell_wmi
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            17161  0 
dcdbas                 14054  1 dell_laptop
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13031  0 
microcode              18209  0 
mac_hid                13037  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
radeon                820703  3 
intel_ips              17721  0 
soundcore              14599  1 snd
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
ttm                    75534  1 radeon
drm_kms_helper         45271  1 radeon
lpc_ich                16925  0 
drm                   230463  5 radeon,ttm,drm_kms_helper
mei                    35796  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
i2c_algo_bit           13197  1 radeon
r8169                  55976  0 
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci

```

```
ben@ben-Studio-1558:~$ sudo lshw -C network
[sudo] password for ben: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:56:9f:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 ip=192.168.178.39 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: f0:4d:a2:53:72:29
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.178.45 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff memory:f0420000-f043ffff
```

thanks in advance!

ben

---

### Post by wildmanne39 on 2012-11-14
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Reboot
Thanks

---

### Post by benjoo on 2012-11-19
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```Reboot
Thanks

Hi Wild Man,

thanks a lot for your quick response! I did the steps you described above. But it still wont connect to the WPA Network.
At my university i tried to connect to an unsecured wlan. The connection establishes but disconnects a few seconds later.

Are there other workarounds i could do instead?

> lsmod | grep b43 output

b43 347284 0
mac80211 461161 1 b43
cfg80211 175375 2 b43,mac80211
bcma 34483 1 b43
ssb 50087 1 b43

>  sudo lshw -C network

product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 64 bits
clock: 33mhz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
ressources: irq:17 memory:f0500000-f0503fff



Thanks in advance

Ben

---

### Post by wildmanne39 on 2012-11-19
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by benjoo on 2012-11-19
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

Hi again,
ill do this as soon as i reach my home.
thanks

---

### Post by benjoo on 2012-11-19
Here is the netinfo.txt
```

*************** info trace ****************



**** uname -a ****


Linux ben-Studio-1558 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:27:31 UTC 2012 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge
--
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Dell Device [1028:0413]
	Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6417 Microdia Integrated Webcam


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:"vlenzer"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
parport_pc             31968  0 
rfcomm                 37276  0 
ppdev                  12817  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
joydev                 17161  0 
snd_hda_codec_hdmi     31423  1 
arc4                   12473  2 
b43                   347284  0 
mac80211              461161  1 b43
cfg80211              175375  2 b43,mac80211
bcma                   34483  1 b43
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
snd_hda_codec_idt      59761  1 
dell_laptop            17161  0 
dcdbas                 14054  1 dell_laptop
ssb                    50087  1 b43
microcode              18209  0 
snd_hda_intel          32515  5 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
video                  18847  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18590  1 dell_wmi
mac_hid                13037  0 
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
radeon                820703  3 
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
psmouse                84843  0 
videodev               95841  2 uvcvideo,videobuf2_core
serio_raw              13031  0 
intel_ips              17721  0 
lpc_ich                16925  0 
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
ttm                    75534  1 radeon
drm_kms_helper         45271  1 radeon
drm                   230463  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13197  1 radeon
mei                    35796  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
firewire_ohci          35521  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
r8169                  55976  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.178.45
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             192.168.178.1


- Device: wlan0  [vlenzer] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FRITZ!Box Fon WLAN 7240: Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    ALICE-WLAN55:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2
    FRITZ!Box Fon WLAN 7270: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Paulchen:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA2
    FRITZ!Box Fon WLAN 7112: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    FRITZ!Box Fon WLAN 7390: Infra, <MAC address removed>, Freq 2427 MHz, Rate 48 Mb/s, Strength 17 WPA WPA2
    BeLLa:           Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    admin:           Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39 WPA2
    FRITZ!Box Fon WLAN 7112: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *vlenzer:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA
    EasyBox-148B34:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA

  IPv4 Settings:
    Address:         192.168.178.39
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.178.1

    DNS:             192.168.178.1




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN55"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001a5ded4167
                    Extra: Last beacon: 1740ms ago
                    IE: Unknown: 000C414C4943452D574C414E3535
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000077A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD8B0050F204104A00011010440001021041000100103B00010310470010000000000000000300001CC63C1B6E9E1021000B436F72706F726174696F6E1023000941525637353244505710240007312E30302E30391042000A323032323032343335351054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD1E00904C336E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000091adc235
                    Extra: Last beacon: 1808ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313132
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Paulchen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009c4c8234
                    Extra: Last beacon: 1592ms ago
                    IE: Unknown: 00085061756C6368656E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030103
                    IE: Unknown: 050C000300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-8 dBm  
                    Encryption key:on
                    ESSID:"vlenzer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000048f5845e
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0007766C656E7A6572
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
          Cell 05 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7240"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c345d982
                    Extra: Last beacon: 420ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037323430
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010A
                    IE: Unknown: 200100
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
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A0F0A00000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: DD5B0050F204104A0001101044000102103B000100104700100F00000B000F00000A000024FE1EF2261021000341564D1023000341564D10240000104200001054000800000000000000001011000341564D100800020188103C000103
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7270"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000029f97ef0
                    Extra: Last beacon: 828ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037323730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: DD6A0050F204104A0001101044000102103B00010010470010F5BF40824E421A2B27E8DB1165240B4B1021000341564D10230009465249545A21426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 07 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"admin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013d4e6b5054
                    Extra: Last beacon: 964ms ago
                    IE: Unknown: 000561646D696E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A400004243600062323000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409070400000000000000000000000000000000000000
                    IE: Unknown: DD770050F204104A0001101044000102103B000103104700102880288028801880A880001F1F2AB46C102100012E1023001620576972656C6573732041636365737320506F696E74102400012E1042000831323334353637381054000800060050F20400011011000531314E415010080002008A103C000101
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e251a2234
                    Extra: Last beacon: 22936ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313132
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-148B34"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000059b70efc0a7
                    Extra: Last beacon: 23260ms ago
                    IE: Unknown: 000E45617379426F782D313438423334
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000197A12
                    IE: Unknown: DD1E00904C336C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
          Cell 10 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7390"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 22.5 Mb/s
                    Mode:Master
                    Extra:tsf=000004906155a180
                    Extra: Last beacon: 23056ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037333930
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048602D
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604001500000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 11 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BeLLa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d1505182
                    Extra: Last beacon: 22656ms ago
                    IE: Unknown: 000542654C4C61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A0F0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001000000
                    IE: Unknown: DD0E0050F204104A0001101044000102



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search fritz.box


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    0.352972] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[   17.822308] wmi: Mapper loaded
[   17.906712] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[   17.906813] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[   17.906912] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[   17.907045] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[   17.907062] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[   17.989124] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[   17.998094] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   18.108578] Registered led device: b43-phy0::tx
[   18.108605] Registered led device: b43-phy0::rx
[   18.108629] Registered led device: b43-phy0::radio
[   20.504698] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   26.044655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.044968] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  140.279078] wlan0: authenticate with <MAC address removed>
[  140.302546] wlan0: send auth to <MAC address removed> (try 1/3)
[  140.304803] wlan0: authenticated
[  140.317874] wlan0: associate with <MAC address removed> (try 1/3)
[  140.321141] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  140.322320] wlan0: associated
[  140.322524] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


**************** done ********************


```

---

### Post by wildmanne39 on 2012-11-19
Hi, go into your router setting and change the channel to 1 or 11 and see if that helps.

Also if you can it would be best to set encryption in your router to just wpa2 only.

Unplug your wired connection after you make the changes so your wireless will take over.

It says it is connected.

Did you let network manager setup your ip address and all or did you do it manually? it would be best to let network manager do it.

Also set your wireless settings to match the screenshots.
Thanks

---

### Post by benjoo on 2012-11-20
Hi Wildman,

i did the steps described with no effort :/.
The connection establishes, im able to reload one page like ubuntuforums.com then the connection closes.

Im using the ubuntu internal network manager to configure the wireless connection.

how do i deinstall the used drivers? maybe a clean installation of the wireless-module could be a workaround??

thanks in advance

Ben

---

### Post by wildmanne39 on 2012-11-20
Hi, your DNS server is the same it has not changed, please post screenshots of your settings in network manager like mine in post 7 so we can see what they look like.
Thanks

---

### Post by benjoo on 2012-11-20
i added the dns-information provided into my network setting. 
What kind of screenshots should i send over?
i thought i should alter the dns in my config.

Now i added the ip of my router as default dns server (see screenshot)

regards

---

### Post by wildmanne39 on 2012-11-20
Hi, it would be best to leave the setting including the dns server set to match my screenshots.

Is your wireless set to infrastructure in network manager?
Thanks

---

### Post by benjoo on 2012-12-05
yeah its set to infrastructure mode.

Is there a distribution maybe from the developers of ubuntu out there which is known to be very handy in supporting third party wifi chips? 

regards

---


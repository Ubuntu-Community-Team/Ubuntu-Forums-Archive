---
title: "Atheros AR9462 keeps disconnecting."
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by Inamati on 2013-04-07
Hello,
I have an Acer Aspire v3-551G and I just installed Ubuntu 12.10. I have searched everywhere and tried everything I could find but wireless still disconnects after a while and sometimes just reactivating Wifi works and other times I have to reboot. Please help me I'm kind of new at this and I don't know what info I can give to help but please feel free to ask.

When I run lspci i get:
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9903
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

So I know my wireless card is Atheros AR9462.

---

### Post by forestG on 2013-04-07
Maybe this could help.
[http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10](http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10)

Personal opinion try the LTS version and if it works stick with that. Its support will last longer than the 12.10 and it is supposed to be more stable. and there is not much difference.

---

### Post by Inamati on 2013-04-07
> **forestG said:**
> Maybe this could help.
[http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10](http://askubuntu.com/questions/217539/acer-aspire-one-wifi-atheros-communications-inc-ar9462-problem-with-12-10)

Personal opinion try the LTS version and if it works stick with that. Its support will last longer than the 12.10 and it is supposed to be more stable. and there is not much difference.

That was already the only thing in that file and I would really like to get it working in 12.10.

---

### Post by wildmanne39 on 2013-04-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

Also post the output of:
```
modinfo ath9k
```
Thanks

---

### Post by Ashtonford on 2013-04-07
I went thru the same recently the only thing that helped was to change the channel of the wireless router.  After that no more drops.

---

### Post by Inamati on 2013-04-08
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

Also post the output of:
```
modinfo ath9k
```
Thanks

> **Ashtonford said:**
> I went thru the same recently the only thing that helped was to change the channel of the wireless router.  After that no more drops.

OK so I just formatted and reinstalled thinking this might help but no luck it's the same. I did realize that it just happens after I update the system. It was connected all night with no issues but this morning I did the 351 updates it was asking and it started happening. 

The file is attached as requested and the output of modinfo ath9k is:
filename:       /lib/modules/3.5.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E5320F189B3DF7787816AFB
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.5.0-26-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

I already tried to change to several channels, disable N and reset the router and it still happens.

Apparently the forum has a limit that doesn't allow me to upload the netinfo and it has more than 800 lines is there another way to post it?

---

### Post by Inamati on 2013-04-08
Here goes the netinfo:

*************** info trace ****************



**** uname -a ****


Linux inamati 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:20:06 UTC 2013 i686 athlon i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0696]
    Kernel driver in use: atl1c
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6621]
    Kernel driver in use: ath9k


**** lsusb ****


Bus 002 Device 002: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 005 Device 002: ID 09da:9090 A4 Tech Co., Ltd XL-750BK Laser Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:"Hello Bitches"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC address removed>   
          Bit Rate=104 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:105  Invalid misc:32   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_realtek    63579  1 
snd_hda_codec_hdmi     31457  1 
bnep                   17708  2 
rfcomm                 37277  0 
parport_pc             31969  0 
ppdev                  12818  0 
bluetooth             183270  10 bnep,rfcomm
kvm_amd                54395  0 
kvm                   357807  1 kvm_amd
aesni_intel            17939  2 
cryptd                 15615  1 aesni_intel
aes_i586               16996  1 aesni_intel
acer_wmi               27587  0 
sparse_keymap          13659  1 acer_wmi
snd_seq_midi           13133  0 
arc4                   12474  2 
microcode              18210  0 
snd_hda_intel          32516  5 
uvcvideo               71278  0 
videobuf2_core         32071  1 uvcvideo
snd_hda_codec         111548  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videodev               95842  2 uvcvideo,videobuf2_core
snd_hwdep              13273  1 snd_hda_codec
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            25383  1 snd_seq_midi
ath9k                 116558  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
joydev                 17162  0 
psmouse                84878  0 
mac80211              461261  1 ath9k
ath9k_common           13784  1 ath9k
ath9k_hw              376270  2 ath9k,ath9k_common
serio_raw              13032  0 
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
k10temp                12959  0 
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              175574  3 ath9k,mac80211,ath
i2c_piix4              12984  0 
rtsx_pci_ms            12876  0 
snd                    62146  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15843  1 rtsx_pci_ms
radeon                820764  4 
ttm                    75535  1 radeon
soundcore              14600  1 snd
drm_kms_helper         47304  1 radeon
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
drm                   238811  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13198  1 radeon
wmi                    18591  1 acer_wmi
video                  18895  1 acer_wmi
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
rtsx_pci_sdmmc         17239  0 
ahci                   25497  2 
rtsx_pci               27093  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                25938  1 ahci
atl1c                  36176  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [Hello Bitches] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           104 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MEO_500554227:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    CASA_2012:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    ThomsonECFC72:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    Thomson73E5C8:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    ZON-6D90-PM:     Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    ZON-B0E0:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    ThomsonBFA7D0:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ZON-E650:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Thomson4705FE:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    ZON-0190:        Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ZON-A100:        Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ZON-96B0:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    ZON-12D0:        Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    bernhome:        Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ZON-2230:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WEP
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 89
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 55
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 54
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 29
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 22
    *Hello Bitches:  Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 76 WPA2
    ZON-C250:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ZON-6530:        Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Thomson45E92E:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    ZON-5D80:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ZON-C440:        Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ZON-F4C0:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    ZON-76C0:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    In\EAs:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 55
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 44
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 25
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 42
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2457 MHz, Rate 11 Mb/s, Strength 39
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24
    ZON-5BD0:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20
    amenfis4:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA
    ZON-3810:        Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    MEO-Artur:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    ZON-61A0:        Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    MEO-CS:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ZON-F53C:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WEP
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2457 MHz, Rate 11 Mb/s, Strength 50
    private_router:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    dematos:         Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2457 MHz, Rate 11 Mb/s, Strength 22

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




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
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Hello Bitches"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000044ba2413f
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 000D48656C6C6F2042697463686573
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502004F127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409000400000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B286010005CA9285381021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption keyn
                    ESSID:"MEO_500554227"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002397fe43e8b
                    Extra: Last beacon: 11232ms ago
                    IE: Unknown: 000D4D454F5F353030353534323237
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010FAECF908B036502BA03FD61356A8D9FE1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420010383730663932636362656662306234391054000800060050F20400011011000D54686F6D736F6E205447373834100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption keyn
                    ESSID:"CASA_2012"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c5a8ff5ad
                    Extra: Last beacon: 11240ms ago
                    IE: Unknown: 0009434153415F32303132
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010B8FB43885BD65CCDACBA46A2196EA2131021000754484F4D534F4E1023000A54686F6D736F6E205447102400043738346E10420010333534633064613363623366646665631054000800060050F20400011011000E54686F6D736F6E2054473738346E100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption keyn
                    ESSID:"ZON-B0E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000108692914b
                    Extra: Last beacon: 1692ms ago
                    IE: Unknown: 00085A4F4E2D42304530
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500003E127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000100000000000000000000000000000000000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B286010005CACCB0E81021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption keyff
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010869f1c6f
                    Extra: Last beacon: 868ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500003E127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C338C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000100000000000000000000000000000000000000
          Cell 06 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption keyn
                    ESSID:"ZON-2230"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000057ce471153
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 00085A4F4E2D32323330
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0102
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption keyff
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000057ce4bc4e0
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0102
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD07000C4300000000
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption keyn
                    ESSID:"Thomson4705FE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023a47dbf972
                    Extra: Last beacon: 11244ms ago
                    IE: Unknown: 000D54686F6D736F6E343730354645
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010838653FC4EB1534E9CFEE2F6F7F41BFD1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420010653861353230383436303035623132331054000800060050F20400011011000D54686F6D736F6E205447373834100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption keyn
                    ESSID:"ThomsonECFC72"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003904b31b5ff
                    Extra: Last beacon: 9412ms ago
                    IE: Unknown: 000D54686F6D736F6E454346433732
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption keyn
                    ESSID:"ZON-6D90-PM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000581e1b0164
                    Extra: Last beacon: 9964ms ago
                    IE: Unknown: 000B5A4F4E2D364439302D504D
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A88000265B356D981021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 11 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption keyff
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000581e175ee7
                    Extra: Last beacon: 10204ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000017127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
          Cell 12 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption keyn
                    ESSID:"Thomson73E5C8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003e6f90142
                    Extra: Last beacon: 9944ms ago
                    IE: Unknown: 000D54686F6D736F6E373345354338
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7C0050F204104A0001101044000102103B00010310470010885E539B90E75E508E0E163B07F51F0B1021000754484F4D534F4E1023000A54686F6D736F6E20544710240003373834104200093130323654543431521054000800060050F20400011011000D54686F6D736F6E205447373834100800020084103C000100
                    IE: Unknown: DD09001018020000040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption keyff
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053b265da9f
                    Extra: Last beacon: 9932ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 05040103000A
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607000400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010047127A
                    IE: Unknown: DD07000C4300000000
          Cell 14 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption keyn
                    ESSID:"bernhome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000582f44c160
                    Extra: Last beacon: 7988ms ago
                    IE: Unknown: 00086265726E686F6D65
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 32048C98B060
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800005CAE8EE78103C000101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D000000000000000000000000000000000000000000
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
                    IE: Unknown: 0B0500002F127A
                    IE: Unknown: DD07000C4300000000
          Cell 15 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption keyn
                    ESSID:"dematos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000058335ed820
                    Extra: Last beacon: 5884ms ago
                    IE: Unknown: 000764656D61746F73
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption keyn
                    ESSID:"ZON-12D0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000057b43420a7
                    Extra: Last beacon: 10200ms ago
                    IE: Unknown: 00085A4F4E2D31324430
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 32048C98B060
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800005CAEA12D8103C000101
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605030400000000000000000000000000000000000000
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
                    IE: Unknown: 0B05010027127A
                    IE: Unknown: DD07000C4300000000
          Cell 17 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption keyn
                    ESSID:"ZON-1F9C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000582bc71523
                    Extra: Last beacon: 9668ms ago
                    IE: Unknown: 00085A4F4E2D31463943
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home


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


[   14.790960] ath: EEPROM regdomain: 0x6a
[   14.790964] ath: EEPROM indicates we should expect a direct regpair map
[   14.790969] ath: Country alpha2 being used: 00
[   14.790971] ath: Regpair used: 0x6a
[   14.797229] wmi: Mapper loaded
[   14.823343] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.823844] Registered led device: ath9k-phy0
[   14.919703] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.919726] acer_wmi: Function bitmap for Communication Button: 0x801
[   14.919734] acer_wmi: Brightness must be controlled by acpi video driver
[   16.806084] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.817031] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.469286] wlan0: authenticate with <MAC address removed>
[   24.483121] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.484285] wlan0: authenticated
[   24.491916] wlan0: associate with <MAC address removed> (try 1/3)
[   24.501255] wlan0: RX AssocResp from <MAC address removed> (capab=0xc31 status=0 aid=2)
[   24.501446] wlan0: associated
[   24.501638] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.249139] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   72.660899] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[   72.710456] ath: phy0: Failed to stop TX DMA, queues=0x004!
[   76.660330] wlan0: authenticate with <MAC address removed>
[   76.665918] wlan0: send auth to <MAC address removed> (try 1/3)
[   76.668668] wlan0: authenticated
[   76.674170] wlan0: associate with <MAC address removed> (try 1/3)
[   76.683673] wlan0: RX AssocResp from <MAC address removed> (capab=0xc31 status=0 aid=2)
[   76.683865] wlan0: associated
[   80.208846] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   80.626526] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[   80.686109] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   84.636242] wlan0: authenticate with <MAC address removed>
[   84.647127] wlan0: send auth to <MAC address removed> (try 1/3)
[   84.650258] wlan0: authenticated
[   84.656463] wlan0: associate with <MAC address removed> (try 1/3)
[   84.664560] wlan0: RX AssocResp from <MAC address removed> (capab=0xc31 status=0 aid=2)
[   84.664722] wlan0: associated
[   88.762411] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   89.488069] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   91.545345] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   92.327793] ath: phy0: Failed to stop TX DMA, queues=0x005!
[   99.047739] ath: phy0: Failed to stop TX DMA, queues=0x005!
[  135.103946] ath: phy0: Failed to stop TX DMA, queues=0x005!
[  136.561508] ath: phy0: Failed to stop TX DMA, queues=0x005!
[  137.587155] ath: phy0: Failed to stop TX DMA, queues=0x004!
[  139.077332] ath: phy0: Failed to stop TX DMA, queues=0x005!
[  140.523155] ath: phy0: Failed to stop TX DMA, queues=0x004!
[  142.548208] ath: phy0: Failed to stop TX DMA, queues=0x004!
[  144.570296] ath: phy0: Failed to stop TX DMA, queues=0x004!
[  146.588444] ath: phy0: Failed to stop TX DMA, queues=0x004!
[  148.066735] ath: phy0: Failed to stop TX DMA, queues=0x005!
[  148.859444] ath: phy0: Failed to stop TX DMA, queues=0x005!


**************** done ********************

---

### Post by wildmanne39 on 2013-04-08
Hi, first change your channel in the router to 1 or 11.
Please post the content of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Thanks

---

### Post by Inamati on 2013-04-08
> **Wild Man said:**
> Hi, first change your channel in the router to 1 or 11.
Please post the content of:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Thanks

The contents are:
options ath9k nohwcrypt=1

Changed the channel to 11 and am testing.

Nope still happens.

---

### Post by wildmanne39 on 2013-04-08
Hi, we are going to compile a new driver from compat, I am going to do it on my computer first to make sure it compiles so it will take some time to do that and write the dirctions.
Thanks

---

### Post by Inamati on 2013-04-08
> **Wild Man said:**
> Hi, we are going to compile a new driver from compat, I am going to do it on my computer first to make sure it compiles so it will take some time to do that and write the dirctions.
Thanks

OK thank's a lot. Before I reformatted the PC I compiled and installed a compat driver but maybe I did it wrong. Bluetooth started working when I did it.

---

### Post by wildmanne39 on 2013-04-08
Which driver did you compile? did you have  options ath9k nohwcrypt=1 applied with the compiled driver?
If the driver installed it should have worked if it was going too.
Link please and the directions you used.
Thanks

---

### Post by Inamati on 2013-04-08
> **Wild Man said:**
> Which driver did you compile? did you have  options ath9k nohwcrypt=1 applied with the compiled driver?
If the driver installed it should have worked if it was going too.
Link please and the directions you used.
Thanks

I lost the link when formatting and can't find it but I think it wasn't a specific driver. If I'm not mistaken it said to compile all drivers and then I removed the ones that were beeing used and rebooted. According to the guide the network manager would assume the correct driver but it didn't work. And I think I had the nohwcrypt applied but I'm not sure... I tried so many things it's hard to keep track.

---

### Post by wildmanne39 on 2013-04-08
Okay, I am going to work on it then.
Thanks

---

### Post by wildmanne39 on 2013-04-08
It is going to take a little longer then expected I have to download 12.10 and install it in virtualbox before I can compile the driver but I have a fast internet connection so the process will not take to long.
Thanks

---

### Post by wildmanne39 on 2013-04-08
This driver compiled on the kernel you are using with no errors or warning.

Install linux-headers-generic for your kernel version and build-essentials then:

Please download compat-wireless-3.6.8-1 from the link below.
[http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases)
Then drag the file to your desktop right click on it and select extract here:
```
cd Desktop/compat-wireless-3.6.8-1
sudo su
./scripts/driver-select ath9k
make
make install
exit
```
After build and installation unload modules and drivers: 
```
sudo make unload
sudo modprobe ath9k
```
When there is an upgrade to the kernel you will need to recompile this driver:
```
cd Desktop/compat-wireless-3.6.8-1
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```
[COLOR="#FF0000"]Copy and paste all commands for accuracy.[/COLOR]
Thanks

---

### Post by Inamati on 2013-04-08
OK just finished now I will test and hopefully it's solved. You sound confident.

---

### Post by wildmanne39 on 2013-04-08
You will probably still need this  options ath9k nohwcrypt=1.
I just compiled and installed it I do not have that device so I could not test it.
Thanks

---

### Post by Inamati on 2013-04-09
OK so it didn't drop not even once so it seems to be solved. I did lose internet access this morning but it stayed connected and then it came back. Probably a misunderstanding between router and pc. If it's not too much to ask you think you could help me get bluetooth working too?

---

### Post by wildmanne39 on 2013-04-09
Hi, I am glad to hear that it is working!!!

Did you have to add the parameter to the driver to make it work properly?

For the bluetooth issue please start a new thread because we are only suppose to have one issue per thread.
Thanks

---

### Post by Inamati on 2013-04-09
> **Wild Man said:**
> Hi, I am glad to hear that it is working!!!

Did you have to add the parameter to the driver to make it work properly?

For the bluetooth issue please start a new thread because we are only suppose to have one issue per thread.
Thanks

Yes I added the parameter. Thank you so much. I will start a new thread then. I just tested after the newest kernel update and everything is ok.

---

### Post by leoxis on 2013-04-09
I extract the package in my home and it worked!!!

now my wifi is working ok!!! It is not as fast as windows but it is so much better!

Thank u so much and I'm sorry to bother u with so many questions...


> **Wild Man said:**
> This driver compiled on the kernel you are using with no errors or warning.

Install linux-headers-generic for your kernel version and build-essentials then:

Please download compat-wireless-3.6.8-1 from the link below.
[http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_3.6_stable_releases)
Then drag the file to your desktop right click on it and select extract here:
```
cd Desktop/compat-wireless-3.6.8-1
sudo su
./scripts/driver-select ath9k
make
make install
exit
```
After build and installation unload modules and drivers: 
```
sudo make unload
sudo modprobe ath9k
```
When there is an upgrade to the kernel you will need to recompile this driver:
```
cd Desktop/compat-wireless-3.6.8-1
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```
[COLOR=#FF0000]Copy and paste all commands for accuracy.[/COLOR]
Thanks

---

### Post by Inamati on 2013-04-26
I just installed ubuntu 13.04 and it's happening again. And the previous solution doesn't work it gives errors.

---

### Post by wildmanne39 on 2013-04-26
Hi please show:
```
modinfo ath9k
gksudo gedit /etc/modprobe.d/ath9k.conf
```
copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Inamati on 2013-04-26
> **Wild Man said:**
> Hi please show:
```
modinfo ath9k
gksudo gedit /etc/modprobe.d/ath9k.conf
```
copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

modinfo ath9k:
```
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.kolicense:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     99BC2D0E2F8B67646D6C273
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int) 
```

ath9k.conf:

```
options nohwcrypt=1
```

wireless script:
```


*************** info trace ****************






**** uname -a ****




Linux inamati 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:19:42 UTC 2013 i686 athlon i686 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0696]
	Kernel driver in use: atl1c
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6621]
	Kernel driver in use: ath9k




**** lsusb ****




Bus 002 Device 002: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 004 Device 002: ID 04ca:3006 Lite-On Technology Corp. 
Bus 005 Device 002: ID 09da:9090 A4 Tech Co., Ltd XL-750BK Laser Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub




**** iwconfig ****




wlan0     IEEE 802.11abgn  ESSID:"Hello Bitches"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:05:CA:92:85:38   
          Bit Rate=130 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:53   Missed beacon:0






**** rfkill ****




0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  12 
bnep                   17669  2 
acer_wmi               27592  0 
sparse_keymap          13658  1 acer_wmi
video                  18894  1 acer_wmi
arc4                   12543  2 
snd_hda_codec_realtek    63791  1 
kvm_amd                50336  0 
kvm                   376505  1 kvm_amd
snd_hda_codec_hdmi     36185  1 
ath9k                 134875  0 
ath9k_common           13783  1 ath9k
snd_hda_intel          38307  6 
ath9k_hw              398520  2 ath9k_common,ath9k
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
aesni_intel            18156  2 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15613  1 ablk_helper
snd_hwdep              13272  1 snd_hda_codec
radeon                870822  4 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
mac80211              526519  1 ath9k
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
rtsx_pci_ms            12875  0 
joydev                 17097  0 
ttm                    71289  1 radeon
videodev               95806  2 uvcvideo,videobuf2_core
cfg80211              436177  3 ath,ath9k,mac80211
memstick               15842  1 rtsx_pci_ms
wmi                    18590  1 acer_wmi
psmouse                81038  0 
snd                    56485  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac_hid                13037  0 
i2c_piix4              13066  0 
drm_kms_helper         47545  1 radeon
serio_raw              13031  0 
ath3k                  12790  0 
drm                   228750  6 ttm,drm_kms_helper,radeon
btusb                  17986  0 
bluetooth             202069  23 bnep,ath3k,btusb,rfcomm
soundcore              12600  1 snd
i2c_algo_bit           13197  1 radeon
k10temp                12958  0 
microcode              18286  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
rtsx_pci_sdmmc         17238  0 
atl1c                  36175  0 
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25507  2 
libahci                26108  1 ahci




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: wlan0  [Hello Bitches] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        44:6D:57:26:90:69


  Capabilities:
    Speed:           130 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Thomson73E5C8:   Infra, 00:26:44:73:E5:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    ThomsonECFC72:   Infra, 00:1D:68:A9:5F:5D, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    ZON-6D90-PM:     Infra, 00:26:5B:35:6D:98, Freq 2432 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    ZON-7850:        Infra, 00:05:CA:C3:78:58, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ZON-0190:        Infra, 00:26:5B:17:01:98, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    ZON-C440:        Infra, 00:05:CA:C5:C4:48, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ZON-96B0:        Infra, 00:26:5B:7F:96:B8, Freq 2457 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ZON-12D0:        Infra, 00:05:CA:EA:12:D8, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    ZON-C250:        Infra, 00:05:CA:7A:C2:58, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Diana:           Infra, 00:05:CA:9E:40:F8, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ZON-A100:        Infra, 00:26:5B:0B:A1:08, Freq 2467 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    KIKA:            Infra, 00:26:5B:D0:E3:88, Freq 2447 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    ZON-C360:        Infra, 00:05:CA:AC:C3:68, Freq 2467 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    CASA_2012:       Infra, 00:26:44:A5:8D:8E, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    ZON-76C0:        Infra, 00:26:5B:D1:76:C8, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ZON-E650:        Infra, 00:26:5B:54:E6:58, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    MEO-CS:          Infra, 08:76:FF:98:ED:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    ZON-F4C0:        Infra, 00:05:CA:E9:F4:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    ZON-9480:        Infra, 00:05:CA:C5:94:88, Freq 2427 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    ZON-6530:        Infra, 00:26:5B:86:65:38, Freq 2467 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    ZON-B0E0:        Infra, 00:05:CA:CC:B0:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Thomson4705FE:   Infra, 00:24:17:44:49:A4, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    ZON-1F9C:        Infra, 00:24:8C:99:D3:EE, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    ZON-F53C:        Infra, 00:24:8C:50:32:7E, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WEP
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:E9:F4:C9, Freq 2437 MHz, Rate 54 Mb/s, Strength 50
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:C3:78:59, Freq 2417 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:9E:40:F9, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:17:01:99, Freq 2442 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:86:65:39, Freq 2467 MHz, Rate 54 Mb/s, Strength 45
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:C5:C4:49, Freq 2417 MHz, Rate 54 Mb/s, Strength 40
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:0B:A1:09, Freq 2467 MHz, Rate 54 Mb/s, Strength 40
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:7A:C2:59, Freq 2422 MHz, Rate 54 Mb/s, Strength 22
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:35:6D:99, Freq 2432 MHz, Rate 54 Mb/s, Strength 35
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:7F:96:B9, Freq 2457 MHz, Rate 54 Mb/s, Strength 34
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:EA:12:D9, Freq 2432 MHz, Rate 54 Mb/s, Strength 30
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:7E:43:09, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:D1:76:C9, Freq 2427 MHz, Rate 54 Mb/s, Strength 19
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:D0:E3:89, Freq 2447 MHz, Rate 54 Mb/s, Strength 14
    *Hello Bitches:  Infra, 00:05:CA:92:85:38, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:05:CA:CC:B0:E9, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    ZON-4300:        Infra, 00:05:CA:7E:43:08, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    ZON-6B90:        Infra, 00:26:5B:07:6B:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ThomsonE95C5A:   Infra, 00:24:17:4D:49:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ThomsonBFA7D0:   Infra, 00:24:17:6D:B3:D2, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    ZON-5FB0:        Infra, 00:26:5B:35:5F:B8, Freq 2447 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:35:5F:B9, Freq 2447 MHz, Rate 54 Mb/s, Strength 30
    MEO_500554227:   Infra, 00:1F:9F:6B:D5:AA, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Thomson45E92E:   Infra, 08:76:FF:45:E9:2E, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:3F:61:A9, Freq 2467 MHz, Rate 54 Mb/s, Strength 30
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:16:34:D9, Freq 2442 MHz, Rate 54 Mb/s, Strength 27
    ZON-61A0:        Infra, 00:26:5B:3F:61:A8, Freq 2467 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    ThomsonA4D10F:   Infra, 00:26:44:A4:D1:0F, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ZON-34D0:        Infra, 00:26:5B:16:34:D8, Freq 2442 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, 00:26:5B:7E:B7:59, Freq 2442 MHz, Rate 54 Mb/s, Strength 25


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        DC:0E:A1:AE:6F:64


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off








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



```

---

### Post by Inamati on 2013-04-26
I run ./scripts/driver-select ath9k as before and it's ok.
But when I run sudo make after a while i get this error:
```
make -C /lib/modules/3.8.0-19-generic/build M=/home/inamati/Documentos/compat-wireless-3.6.8-1 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.o
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:58:22: erro: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rfkill_regulator_probe’
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:125:22: erro: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rfkill_regulator_remove’
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:139:11: erro: ‘rfkill_regulator_probe’ undeclared here (not in a function)
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:140:2: erro: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:140:24: erro: ‘rfkill_regulator_remove’ undeclared here (not in a function)
cc1: alguns avisos estão sendo tratados como erros
make[3]: ** [/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.o] Erro 1
make[2]: ** [/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill] Erro 2
make[1]: ** [_module_/home/inamati/Documentos/compat-wireless-3.6.8-1] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.8.0-19-generic'
make: ** [modules] Erro 2



```

---

### Post by wildmanne39 on 2013-04-26
Do you have linux-headers-generic for your kernel version and build-essentials installed?

Are you in the directory where you extracted the driver?

Did you do a fresh install or is this an upgrade?

When there is an upgrade to the kernel you will need to recompile this driver:
```
cd Desktop/compat-wireless-3.6.8-1
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```
Thanks

---

### Post by Inamati on 2013-04-26
> **Wild Man said:**
> Do you have linux-headers-generic for your kernel version and build-essentials installed?

Are you in the directory where you extracted the driver?

Did you do a fresh install or is this an upgrade?

When there is an upgrade to the kernel you will need to recompile this driver:
```
cd Desktop/compat-wireless-3.6.8-1
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```
Thanks


It was a fresh install of ubuntu 13.04. I do have build essential and headers installed and those commands gave me the same error I posted.

---

### Post by wildmanne39 on 2013-04-26
I will have to try to compile the driver on 13.04 so I will need some time, it is possible the driver will not compile on the new kernel.
Thanks

---

### Post by wildmanne39 on 2013-04-26
I could not get it to compile on 13.04 either.

---

### Post by Inamati on 2013-04-26
OK so now what?

---

### Post by wildmanne39 on 2013-04-26
I would go back to the previous release that worked.

---

### Post by Inamati on 2013-04-26
when the laptop is booting it says "Unable to read bad line in ath9k.conf starting with options..." does that help?

---

### Post by wildmanne39 on 2013-04-26
Please post the output of:
```
grep -R [0-9a-zA-Z] /sys/module/ath9k/parameters/
```
Thanks

---

### Post by wildmanne39 on 2013-04-26
I just tried to compile the driver again and this time I got the exact same errors as you did.

---

### Post by Inamati on 2013-04-26
> **Wild Man said:**
> Please post the output of:
```
grep -R [0-9a-zA-Z] /sys/module/ath9k/parameters/
```
Thanks

The output is:
/sys/module/ath9k/parameters/enable_diversity:0
/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/nohwcrypt:0
/sys/module/ath9k/parameters/btcoex_enable:0

The full error is : libkmod: ERROR ../libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/ath9k.conf line 1: ignoring bad line starting with 'options'.
and it appears before the login window

---

### Post by wildmanne39 on 2013-04-26
I see the error this:
```
options nohwcrypt=1
```
Should be ```
options ath9k nohwcrypt=1
``` 
Thanks

---

### Post by Inamati on 2013-04-26
> **Wild Man said:**
> I see the error this:
```
options nohwcrypt=1
```
Should be ```
options ath9k nohwcrypt=1
``` 
Thanks

Yeah I saw it after i posted it and corrected it then rebooted but the error still appears and wireless still drops.

The output is now:
/sys/module/ath9k/parameters/enable_diversity:0
/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/nohwcrypt:1
/sys/module/ath9k/parameters/btcoex_enable:0

---

### Post by wildmanne39 on 2013-04-26
We can try two things:
Change this:
```
options ath9k nohwcrypt=1
```
To:
```
options ath9k nohwcrypt=1 enable_diversity:1
```
Thanks

---

### Post by Inamati on 2013-04-26
> **Wild Man said:**
> We can try two things:
Change this:
```
options ath9k nohwcrypt=1
```
To:
```
options ath9k nohwcrypt=1 enable_diversity:1
```
Thanks

I almost had a heart attack. With diversity enabled when booting it says that it wasn't able to detect my harware and that I had to configure it all manually and if I wanted to start in low res just this once. I replied yes and nothing happened. Luckily for me, for the first time, rebooting your computer endlessly while staring with an empty gaze at infinity solved the problem. I had to delete the diversity option.

---

### Post by wildmanne39 on 2013-04-26
The only option left is to disable bluetooth temperarily and see if that works but then you woud be back to square one with it if that is what fixes your wireless issue.

---

### Post by matt_symes on 2013-04-26
Hi

> **Inamati said:**
> I run ./scripts/driver-select ath9k as before and it's ok.
But when I run sudo make after a while i get this error:
```
make -C /lib/modules/3.8.0-19-generic/build M=/home/inamati/Documentos/compat-wireless-3.6.8-1 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.o
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:58:22: erro: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rfkill_regulator_probe&#8217;
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:125:22: erro: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rfkill_regulator_remove&#8217;
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:139:11: erro: &#8216;rfkill_regulator_probe&#8217; undeclared here (not in a function)
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:140:2: erro: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c:140:24: erro: &#8216;rfkill_regulator_remove&#8217; undeclared here (not in a function)
cc1: alguns avisos estão sendo tratados como erros
make[3]: ** [/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.o] Erro 1
make[2]: ** [/home/inamati/Documentos/compat-wireless-3.6.8-1/net/rfkill] Erro 2
make[1]: ** [_module_/home/inamati/Documentos/compat-wireless-3.6.8-1] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.8.0-19-generic'
make: ** [modules] Erro 2



```

Well i managed to get this driver to build in 3.8.0-19. 

Well actually i'm using 3.9..rc8 but i have the headers for 3.8.0-19.

```

matthew-S206:/home/matthew/compat-wireless/compat-wireless-3.6.8-1 % uname -r && ls -ld /lib/modules/3.8.0-19-generic
3.9.0-030900rc8-generic
drwxr-xr-x 5 root root 4096 Apr 23 16:11 /lib/modules/3.8.0-19-generic/
matthew-S206:/home/matthew/compat-wireless/compat-wireless-3.6.8-1 % 
```

I cannot test it though as i do not have a card that requires the ath9k driver.

It seems all references to __devinit, __devexit and __devexit_p() have been remove from 

```
include/linux/init.h 
```

in the Linux kernel headers which is why you are getting the error you are getting there. 

You need to edit the file

```
compat-wireless-3.6.8-1/net/rfkill/rfkill-regulator.c
```

and remove the the three references.

Lines 144, 129, 62. 

Actually the way i bypassed that was just to create some preprocessor switches and remove the other reference.
```

#define __devinit
#define __devexit
```

That will allow to continue building up until you hit the next set of errors.

It also seems the netlink interface has changed some of the definitions in some of the kernel structures.

These errors appear in the file

```
compat-wireless-3.6.8-1/net/wireless/nl80211.c
```

because of changes in 

```
include/linux/netlink.h
```


In the structure..

```
struct netlink_notify {
        struct net *net;
        int pid;
        int protocol;
};
```

pid has become portid

```
struct netlink_notify {
        struct net *net;
        int portid;
        int protocol;
};
```

In the same file pid (in bold)

```
struct netlink_skb_parms {
        struct scm_creds        creds;          /* Skb credentials      */
        **__u32                   pid;**
        __u32                   dst_group;
        struct sock             *ssk;
};
```

has become

```
__u32                   portid;
```

and finally in the file 

```
include/linux/genetlink.h
```

the structure

```
struct genl_info {
        u32                     snd_seq;
        **u32                     snd_pid;**
        struct nlmsghdr *       nlhdr;
        struct genlmsghdr *     genlhdr;
        void *                  userhdr;
        struct nlattr **        attrs;
#ifdef CONFIG_NET_NS
        struct net *            _net;
#endif
        void *                  user_ptr[2];
};
```

has changed to ```
u32                     snd_portid;
```

So you would need to change all reference to these variables in the file nl80211.c to point to the new names.

I believe that's all it is; a series of name changes.

This allows you to build the driver.
```

<snip>
  CC      /home/matthew/compat-wireless/compat-wireless-3.6.8-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/matthew/compat-wireless/compat-wireless-3.6.8-1/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
matthew-S206:/home/matthew/compat-wireless/compat-wireless-3.6.8-1 %
```

Whether these changes will allow the driver to work or not is another question but that did get it built.

```
matthew-S206:/home/matthew/compat-wireless/compat-wireless-3.6.8-1 % find * -name "*.ko"
compat/compat.ko
drivers/net/wireless/ath/ath.ko
drivers/net/wireless/ath/ath9k/ath9k.ko
drivers/net/wireless/ath/ath9k/ath9k_hw.ko
drivers/net/wireless/ath/ath9k/ath9k_htc.ko
drivers/net/wireless/ath/ath9k/ath9k_common.ko
net/rfkill/rfkill-regulator.ko
net/wireless/cfg80211.ko
net/mac80211/mac80211.ko
matthew-S206:/home/matthew/compat-wireless/compat-wireless-3.6.8-1 % 

```

I have no way of even testing it.

Kind regards

---

### Post by Inamati on 2013-04-26
I don't know if I can make all those changes without screwing up. What are preprocessor switches? I don't mind losing bluetooth so we can test that too.

---

### Post by matt_symes on 2013-04-26
Hi

I would be very surprised if someone has not already written a patch for this.

I am going on the assumption that pid and portid are synonymous and that is going out on a limb. 

I'm pretty sure that __dev... has been removed and a google search also seems to suggest that.

I'll look around and see if someone, who has spent longer than a couple of hours looking at this, has written a patch,as i could be totally wrong.

Kind regards

---

### Post by Inamati on 2013-04-27
OK thanks.

---

### Post by wildmanne39 on 2013-04-27
Thanks Matt, I am afraid I have done all I can do.

---

### Post by Inamati on 2013-04-28
Still nothing? Getting kind of desperate here...

---

### Post by scottku on 2013-12-30
Inamati- Did you ever find a solution to this problem?

I'm experiencing similar problems on Ubuntu 13.10. I get the "Failed to stop TX DMA" and "DMA failed to stop in 10 ms" messages in my kernel logs. My wireless card is "03:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)".

In an attempt to fix the problem, I've tried installing the 2013-12-06 wifi driver backports and the problem persists. It seems that the problem tends to occur when I'm transferring large amounts of data over wifi (or maybe that is when I'm most aware of the problem).

---

### Post by unattached on 2014-02-04
Hey scottku,

I have the same problem, any news?

---

### Post by scottku on 2014-02-04
> **unattached said:**
> 
I have the same problem, any news?

I fixed it by installing an Ethernet cable in my house to my desktop that had this problem so I don't have to use WiFi anymore.

I doubt it was a problem with my WiFi network (other iPhones, Ubuntu and Windows devices connect fine). I also thought about buying another network card for my desktop, but this is the 2nd card I've had in that machine---and the 1st card didn't work well either. I didn't have a high confidence that buying a 3rd card would make the situation any better.

---

### Post by Lólindir on 2014-02-06
> **unattached said:**
> Hey scottku,

I have the same problem, any news?

Also here I could not yet make the connection stable. I have an incredible unstable connection in Ubuntu. Win7 seems to work fine. I also have other devices on this network (Lubuntu laptop, android phones) working fine.
It is so bad that I often simply cannot work when starting up Ubuntu :(

Unfortunatelly installing a cable will not be an easy job here...

---


---
title: "Disabled wireless on ASUS U32U"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by jdominik on 2013-05-05
Hello!
That's my first thread here. I searched for example here: [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled) and I see that's my wifi is disabled...
But I can switch device on on my keyboard and device is in "networking window" clickable but after turns on only for 2-3 seconds...
I don't know what I should to do. I use kubuntu 13.04 and I am rather beginner in linux.
Thanks for reply!

---

### Post by varunendra on 2013-05-06
Welcome to the forums jdominik! :)

Please follow the "Wireless Script" link in my signature and post back the diagnostics report as mentioned in the linked post.

---

### Post by jdominik on 2013-05-06
For lucky I have connection from my broadband modem, so here you are:

---

### Post by praseodym on 2013-05-06
Tried to reset the BIOS to default settings? Is it a (U)EFI installation? If yes, do not reset!!

---

### Post by varunendra on 2013-05-06
Please do what praseodym suggested. Resetting BIOS does magic in most of the mysterious 'Hard-blocked' issues. But as he also pointed out, DON't reset if it is a UEFI installation.

If this doesn't help, other possible reason may be a buggy hardware switch (although it *maybe* an OS problem, but that is rare, while hardware switches are a more common cause).

Not sure if it can be related or not, but you should also turn the Power Management off on the wireless adapter -
```
sudo iwconfig wlan0 power off
```

Let us know of any progress you make.

---

### Post by jdominik on 2013-05-07
I don't have a reset function in BIOS - only - 'default options'. There  is an UEFI boot but this option is default disabled. So after loading  defaults there is no changes... experimental: after change unblock for  block in wireless security my wireless is no visible in system, so there  is no proper match. Second too. :(

---

### Post by jdominik on 2013-05-07
I trying to install wireless windows drivers but it's to hard for me..  and adiitionally I'm doing something wrong and my wlan device is not  visible in system - I must to run every system session: sudo modprobe  ath9k... and now is worse.

---

### Post by varunendra on 2013-05-07
> **jdominik said:**
> I must to run every system session: sudo modprobe  ath9k... and now is worse.

Please run the wireless script and post back the results once again.

---

### Post by john1113 on 2013-05-08
Hi , I got the same problem since I've upgraded to 13.04 with my u32u , before I was on 12.10 and it worked fine. It's not an interuptor problem , the wifi is still working on windows for me .

---

### Post by varunendra on 2013-05-08
> **john1113 said:**
> Hi , I got the same problem since I've upgraded to 13.04 with my u32u , before I was on 12.10 and it worked fine. It's not an interuptor problem , the wifi is still working on windows for me .

Welcome to the forums john!

Please do the same thing I asked the OP for. That is - please follow the "Wireless Script" link in my signature, do what the linked post asks to do, and post back the contents of "netinfo.txt" file the script gentrates. Thanks.

@ jdominik,
Awaiting the repost of new netinfo.txt. Maybe it can explain to us better the meaning and reason of "now it is worse" :).

---

### Post by john1113 on 2013-05-09
I think the problem comes from the new kernel , when I boot with my older kernel (3.5) everything works fine .
I've done the netinfo.txt with my 3.8 kernel.

---

### Post by john1113 on 2013-05-09
And here is the one done with th 3.5 kernel (too heavy for upload the file)


```

*************** info trace ****************



**** uname -a ****


Linux Bryan-PC 3.5.0-28-generic #48-Ubuntu SMP Tue Apr 23 23:03:38 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


**** lspci ****


04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1437]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k


**** lsusb ****


Bus 001 Device 002: ID 12d1:141b Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSIDff/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thrff
          Power Managementff
          


**** rfkill ****


0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
ppp_deflate            12951  0 
zlib_deflate           26915  1 ppp_deflate
bsd_comp               12922  0 
ppp_async              17414  1 
crc_ccitt              12708  1 ppp_async
nls_iso8859_1          12714  1 
dm_crypt               23012  1 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
binfmt_misc            17501  1 
fglrx                5201123  152 
arc4                   12530  2 
snd_hda_codec_realtek    78147  1 
snd_hda_codec_hdmi     32049  1 
ath9k                 131317  0 
uvcvideo               76750  0 
kvm_amd                55605  0 
ath9k_common           14056  1 ath9k
snd_hda_intel          33492  5 
kvm                   414071  1 kvm_amd
ath9k_hw              395357  2 ath9k_common,ath9k
snd_hda_codec         134213  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
ath                    23828  3 ath9k_common,ath9k,ath9k_hw
videobuf2_core         32852  1 uvcvideo
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
option                 30142  2 
usb_wwan               20099  1 option
videodev              120310  2 uvcvideo,videobuf2_core
usbserial              42356  7 option,usb_wwan
snd_page_alloc         18485  2 snd_pcm,snd_hda_intel
snd_seq_midi           13325  0 
mac80211              540032  1 ath9k
snd_seq_midi_event     14900  1 snd_seq_midi
joydev                 17458  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi_event,snd_seq_midi
cfg80211              206797  3 ath,ath9k,mac80211
snd_seq_device         14498  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29426  2 snd_pcm,snd_seq
rtsx_pci_ms            13012  0 
asus_nb_wmi            12711  0 
snd                    78921  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
memstick               16555  1 rtsx_pci_ms
asus_wmi               24089  1 asus_nb_wmi
sparse_keymap          13891  1 asus_wmi
soundcore              15048  1 snd
sp5100_tco             13698  0 
lp                     17760  0 
amd_iommu_v2           19098  1 fglrx
psmouse                95595  0 
k10temp                13127  0 
i2c_piix4              13168  0 
mac_hid                13206  0 
parport                46346  3 lp,ppdev,parport_pc
serio_raw              13216  0 
microcode              22804  0 
vesafb                 13798  1 
rtsx_pci_sdmmc         17476  0 
rtsx_pci               33452  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  61651  0 
pata_atiixp            13205  0 
ahci                   25721  2 
libahci                31192  1 ahci
wmi                    19071  1 asus_wmi
video                  19391  0 
usb_storage            48839  1 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: ttyUSB0  [Orange Business Contract 1] --------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         80.10.4.19
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             193.253.141.132
    DNS:             193.253.141.133


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    CA2I-WIFI5:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    NEUF_DC10:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    Neo Services 2 (37-38): Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67
    Neo Services 3 (42-43): Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    Neo Services 7 (52-53): Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    Neo Services 16 (22-23): Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    Neo Services 15 (27-28): Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    Neo Services 4 (44-45): Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    Neo Services 6 (59-60): Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17
    Neo Services 5 (57-58): Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15
    FreeWifi:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22
    Neo Services 10 (67-68): Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    WIFI:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    SFR WiFi Public: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key
                    ESSID:"Neo Services 2 (37-38)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b664719ff0
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00164E656F2053657276696365732032202833372D333829
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key
                    ESSID:"Neo Services 16 (22-23)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b663b4450c
                    Extra: Last beacon: 740ms ago
                    IE: Unknown: 00174E656F205365727669636573203136202832322D323329
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key
                    ESSID:"Neo Services 5 (57-58)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b6680c9181
                    Extra: Last beacon: 724ms ago
                    IE: Unknown: 00164E656F2053657276696365732035202835372D353829
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key
                    ESSID:"Neo Services 3 (42-43)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b660869aa5
                    Extra: Last beacon: 464ms ago
                    IE: Unknown: 00164E656F2053657276696365732033202834322D343329
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key
                    ESSID:"Neo Services 7 (52-53)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b668769c23
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 00164E656F2053657276696365732037202835322D353329
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000293f6a41e59
                    Extra: Last beacon: 4800ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1604050600000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010049127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404050600000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key
                    ESSID:"Neo Services 10 (67-68)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b661d19fdb
                    Extra: Last beacon: 740ms ago
                    IE: Unknown: 00174E656F205365727669636573203130202836372D363829
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key
                    ESSID:"Neo Services 4 (44-45)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b663397736
                    Extra: Last beacon: 744ms ago
                    IE: Unknown: 00164E656F2053657276696365732034202834342D343529
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ae2bc80160
                    Extra: Last beacon: 4544ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A6C0003FFFFFF0001000000000000000100000000000000000000
                    IE: Unknown: 3D1608000700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key
                    ESSID:"CA2I-WIFI6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000279493118b
                    Extra: Last beacon: 4484ms ago
                    IE: Unknown: 000A434132492D5749464936
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key
                    ESSID:"Neo Services 15 (27-28)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000012b65d8f5be2
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00174E656F205365727669636573203135202832372D323829
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 0706474220010D0E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aee46e3b47
                    Extra: Last beacon: 928ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1603050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020030127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key
                    ESSID:"WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ccb63450df
                    Extra: Last beacon: 460ms ago
                    IE: Unknown: 000457494649
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key
                    ESSID:"free_choupette"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f2aa89d4d
                    Extra: Last beacon: 456ms ago
                    IE: Unknown: 000E667265655F63686F757065747465
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 15 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005e905b1a0b
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0502001E127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


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


[    0.420518] pci 0000:00:01.1: reg 10: [mem 0xfeb44000-0xfeb47fff]
[    0.421883] pci 0000:00:14.2: reg 10: [mem 0xfeb40000-0xfeb43fff 64bit]
[    2.000585] wmi: Mapper loaded
[   23.981139] asus_wmi: ASUS WMI generic driver loaded
[   24.151185] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.6
[   24.151357] asus_wmi: SFUN value: 0xa0877<6>[   24.153957] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input6
[   24.318860] asus_wmi: Backlight controlled by ACPI video driver
[   25.554665] ath: EEPROM regdomain: 0x60
[   25.554674] ath: EEPROM indicates we should expect a direct regpair map
[   25.554681] ath: Country alpha2 being used: 00
[   25.554683] ath: Regpair used: 0x60
[   25.670832] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   25.671931] Registered led device: ath9k-phy0
[   29.230070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.233728] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************

```

---

### Post by varunendra on 2013-05-09
Hi John1113,

From your previous output -
```
**** rfkill ****


**0: phy0: Wireless LAN**
	Soft blocked: no
	**Hard blocked: [COLOR="#FF0000"]yes[/COLOR]**
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```
Which means it was switched off by the hardware switch (which is Fn+F2 on my Asus X54C). Please make sure it is turned on before trying to connect. If the hardware switch does not seem to work, post back.

**EDIT:**
And Please use 'Code' tags to post long outputs. Follow the 'Code Tags example' link in my signature to see how to do it.

---

### Post by john1113 on 2013-05-09
It is on , when I take it Off and On , I can see the wifi network for a second and it disappears , like if I had take it off.
Sometimes the wifi works , but it's totaly random

---

### Post by varunendra on 2013-05-09
> **john1113 said:**
> It is on , when I take it Off and On , I can see the wifi network for a second and it disappears , like if I had take it off.
Sometimes the wifi works , but it's totaly random

For a test, please blacklist the asus_nb_wmi driver :
```
echo "blacklist asus_nb_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
reboot and retry. Note that blacklisting this driver will also prevent asus_wmi from loading which in turn will disable some Fn+ key combinations. It is just to test if it is the culprit (it caused troubles with my bluetooth, so I have permanently blacklisted it..)

**PS:**
Please edit your previous post to wrap the scary output within 'Code' Tags :)
Follow the 'Code Tags example' link in my signature to see how.

---

### Post by john1113 on 2013-05-09
Done !
It seems to work :D

---

### Post by varunendra on 2013-05-09
> **john1113 said:**
> Done !
It seems to work :D

Really??

It would be a surprisingly pleasant shock for me if it does (even though it has side effects). I'd recommend you reboot/retry a few hundred million times before concluding :D

Unfortunately, I haven't yet figured out how to keep the good parts that asus_wmi provides. So as of now, it is a compromise between your wireless and the Fn key functionalities that asus_wmi provides. These functionalities, in my Asus x54c are : Enable/Disable Touchpad (Fn+F9), and Volume Control (Mute/Decrease/Increase - Fn+F10 through F12). If you can live without these, keep it blacklisted.

And let us know if it has any other side effects too. As always, user feedbacks are what help us offer better help next time :)

---

### Post by john1113 on 2013-05-09
All works good , I've done 4 reboot :)
The first reboot after the blacklist I had no more sound , but since the second reboot all is okay :D
Some Fn key functionalities have been disabled like volume control/mute ; enable/disable touchpad and some useless, but some are still working like screen brightness , wifi on/off Oo , num lock ;)

PS: what is the code for undo if necessary ?

---

### Post by varunendra on 2013-05-09
> **john1113 said:**
> All works good , I've done 4 reboot :)
The first reboot after the blacklist I had no more sound , but since the second reboot all is okay :D
Some Fn key functionalities have been disabled like volume control/mute ; enable/disable touchpad and some useless, but some are still working like screen brightness , wifi on/off Oo , num lock ;)
I'd call it fantastic then :)
Another weirdness you might have noticed - the wireless on/off works in four steps (at least in my asus) - 1) wireless on, 2) wireless LED on, 3) wireless off, 4) wireless LED off.

> PS: what is the code for undo if necessary ?
Remove the "**blacklist asus_nb_wmi**" line from the **/etc/modprobe.d/blacklist.conf** file (or place a **#** in its beginning to comment it out).
You'll have to open it with root privileges to be able to edit it. For example, if the text editor is gedit -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

A one-step, easier way is the following command :
```
sudo sed -i 's:blacklist asus_nb_wmi:# $:' /etc/modprobe.d/blacklist.conf
```
it will comment it out by placing a **#** in the beginning of the blacklist line.

Thanks for the feedback, we all appreciate it! :)

---

### Post by john1113 on 2013-05-09
> **varunendra said:**
> 
Another weirdness you might have noticed - the wireless on/off works in four steps (at least in my asus) - 1) wireless on, 2) wireless LED on, 3) wireless off, 4) wireless LED off.


Mine is still working in two steps , with no led on :)

> 
Remove the "**blacklist asus_nb_wmi**" line from the **/etc/modprobe.d/blacklist.conf** file (or place a **#** in its beginning to comment it out).
You'll have to open it with root privileges to be able to edit it. For example, if the text editor is gedit -
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

A one-step, easier way is the following command :
```
sudo sed -i 's:blacklist asus_nb_wmi:# $:' /etc/modprobe.d/blacklist.conf
```
it will comment it out by placing a **#** in the beginning of the blacklist line.

Thanks for the feedback, we all appreciate it! :)

Thank you for all :D

---

### Post by jdominik on 2013-05-09
Please wait for me. This u32u is my wife's computer which I brought her so now I can use her's older one.In the evening - here I'm going to construct and attach the file.
Thanks for reply ;)

---

### Post by varunendra on 2013-05-09
> **jdominik said:**
> Please wait for me. This u32u is my wife's computer which I brought her so now I can use her's older one.In the evening - here I'm going to construct and attach the file.

We'll be right here.. awaiting :)

If the main problem is of the same nature (wireless switches on momentarily, then turns off again), with references to asus_wmi in dmesg part of the generated report, you can safely try the blacklisting trick that worked for john1113. As mentioned in my last post, it can be quickly and easily reverted if doesn't work.

---

### Post by jdominik on 2013-05-09
My new netinfo file...

---

### Post by varunendra on 2013-05-09
Hardware switch is okay, but ath9k is not loaded. Strange.

You said in [post #6]("http://ubuntuforums.org/showthread.php?t=2142462&p=12637880#post12637880") that you now have to do 'sudo modprobe ath9k' everytime you boot. Do you get connected after that? Or is there anything even worse?

If manually modprob'ing the ath9k module gets you connected, try-
```
sudo modprobe -v ath9k
sudo update-initramfs -u
```
..then reboot. Does ath9k load automatically after reboot? (check - **lsmod | grep ath**)

If not, we can force it by adding it to **/etc/modules** file -
```
echo ath9k | sudo tee -a /etc/modules
```

Does it make life any better?

---

### Post by jdominik on 2013-05-12
[B]This makes life better: ;)
Code:

echo ath9k | sudo tee -a /etc/modules
[/B]And instruction with whick my wireless is still enabled:


echo "blacklist asus_nb_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf

But it also disabled my volume keywords... so what if I want to enabled this? They're very usefull so...

---

### Post by varunendra on 2013-05-13
> **jdominik said:**
> [B]This makes life better: ;)
Code:

echo ath9k | sudo tee -a /etc/modules
[/B]
It shouldn't have been required in the first place, so apparently we seem to have some messed up configuration requiring us to force it. But anyway, as long as it works.... :)

> And instruction with whick my wireless is still enabled:

echo "blacklist asus_nb_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf

But it also disabled my volume keywords... so what if I want to enabled this? They're very usefull so...
In the netinfo.txt file you attached, the hardware key looked okay, so the above blacklisting shouldn't have been required. Was the wireless switched off again after force-loading ath9k as above? Please confirm.

As of now, please try -
```
sudo modprobe -v asus_nb_wmi
```
..and see if the volume control works again. If it doesn't, or if the Fn+ key combinations start working strangely, please run a module unload/load cycle -
```
sudo modprobe -rfv asus_nb_wmi
sudo modprobe -v asus_nb_wmi
```
Does everything start working as expected? (may take a few seconds to a minute, plus a few random Fn key combos initially).
Or is something still falling apart?

If the above cycle makes everything normal, we may remove the blacklisting above to make this normality permanent.

---

### Post by Martin_Solstad on 2013-08-26
I got the same problem on my Asus U32U with AMD E450 APU.
The solution I found was to go in "suspend-mode" and wake it up again.. Then the Wifi will work. Untill the next time I reboot and I have to suspend and wake up again.

Does anyone have a better and permanent solution for this?


Mvh
Martin

---

### Post by bndMfbF on 2013-10-08
> **Martin_Solstad said:**
> I got the same problem on my Asus U32U with AMD E450 APU.
The solution I found was to go in "suspend-mode" and wake it up again.. Then the Wifi will work. Untill the next time I reboot and I have to suspend and wake up again.

Does anyone have a better and permanent solution for this?


Mvh
Martin

I've exactly the same problem with my Asus U32U. Tried all major distros, and I get the same problem. It's annoying.

---

### Post by varunendra on 2013-10-08
Welcome to the forums bndMfbF! :)

And thanks for bumping the thread, I had forgotten this one.

I think I have recently found a better solution (workaround, without any compromises) than blacklisting asus_nb_wmi. Please try this and let us all know whether it works or not for you : [http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891](http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891)

Look at post#32 below the linked post to see a nicely listed progress report from shao2.

**_NOTE:_** If you have not blacklisted the "**asus_nb_wmi**" driver, you **don't need** the 2nd command in the post - "**sudo sed -i '/asus_nb_wmi/ d' /etc/modprobe.d/blacklist.conf**".

Of the three people who tried this so far (in my knowledge), it worked for two, but the third (actually the first with whom we tried it, thanks to chili555) actually had the opposite problem - he couldn't turn his wifi off. So from the point of view of "making wifi work", it seems to work for all.

---

### Post by bndMfbF on 2013-10-09
> **varunendra said:**
> Welcome to the forums bndMfbF! :)

And thanks for bumping the thread, I had forgotten this one.

I think I have recently found a better solution (workaround, without any compromises) than blacklisting asus_nb_wmi. Please try this and let us all know whether it works or not for you : [http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891](http://ubuntuforums.org/showthread.php?t=2174901&p=12805891#post12805891)

Look at post#32 below the linked post to see a nicely listed progress report from shao2.

**_NOTE:_** If you have not blacklisted the "**asus_nb_wmi**" driver, you **don't need** the 2nd command in the post - "**sudo sed -i '/asus_nb_wmi/ d' /etc/modprobe.d/blacklist.conf**".

Of the three people who tried this so far (in my knowledge), it worked for two, but the third (actually the first with whom we tried it, thanks to chili555) actually had the opposite problem - he couldn't turn his wifi off. So from the point of view of "making wifi work", it seems to work for all.

Good evening

Thank you very much. It's working!! Started to work after changing to wapf=1 and rebooting.

Too bad I've to send the laptop in a few days for warranty. Screen problems :(

And again, awesome job.

Cheers, Filipe

---

### Post by varunendra on 2013-10-10
> **bndMfbF said:**
> It's working!! Started to work after changing to wapf=1 and rebooting.

Great ! Thanks for the valuable feedback. I guess it makes it now a certified workaround. ;)

---

### Post by pixolex on 2013-10-28
Can some one help resolving this bug bisecting the kernel?

Please see this bug report I did:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681)

---

### Post by varunendra on 2013-10-28
> **pixolex said:**
> Can some one help resolving this bug bisecting the kernel?

Please see this bug report I did:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681)

Thanks for linking the workaround to your bug report pixolex. :)
But you should mention in your update on the bug report that it is only applicable to Asus Notebooks/netbooks that use the "ausu_nb_wmi" driver.

Also, you may change/update the link to a better, complete and less confusing post than the current ones ;) : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)
It is rather clean, complete and you may find post #2 as an extra help to compensate your Fn+F2 key function.

**@ To others,** I would still request to submit a separate bug report specific to Asus laptops (or "asus_nb_wmi" driver), since this bug is not limited to ath9k driver  but is definitely limited to Asus models.

Of course add yourselves to the "affected" list of pixolex's bug report too.

**PS:**
Sorry I didn't answer your main question. I don't yet know how to 'bisect the kernel'. I'm reading [the wiki]("https://wiki.ubuntu.com/Kernel/KernelBisection#Bisecting_Ubuntu_kernel_versions") now, although I don't think I can help since I'm not yet affected (still using kernel 3.2.36.. due to ultra slow bandwidth)

---

### Post by pixolex on 2013-10-30
I've added that link to the workaround section in the bug description and stated that's only for the "asus_nb_wmi" driver.

_We need momentum in this bug_. 

Please EVERYONE subscrive this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681?comments=all)

---

### Post by pixolex on 2013-10-30
I think the problem is in this Kernel C file:  [https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/platform/x86/asus-nb-wmi.c?id=refs/tags/v3.12-rc7](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/platform/x86/asus-nb-wmi.c?id=refs/tags/v3.12-rc7)

Do you have the skills to submit a patch to "quirk" this problem? 

Do you know how the asus_nb_wmi.conf file work? Maybe it forces the "wapf=1" parameter, isn't it?

---

### Post by varunendra on 2013-10-30
Yes it does exactly that.

[list][*]All the files in the /etc/modprobe.d/ directory are read before loading a module.
[*]If it is blacklisted, it won't load (unless required by another driver).
[*]If a line starting with "options.." has its name, whatever option is provided will be used while loading it.[/list]

It is not necessary to have the .conf file's name same as module name, we do it just for clarity and consistency. You can name it whatever you wish. It is the syntax of the line in it that matters. It is also *recommended* to add the ".conf" extension to it. It is not necessary as of now, but will be in future.

Creating a patch is not difficult. I haven't created any myself, but it is just a diff file with context and reference lines. The time taking part is to analyse the code and make sure exactly which part we need to patch. And then compiling - testing to make sure it works as expected without any (or any serious) side effects.

I haven't tried that so far, but may get some time to look into it.

---


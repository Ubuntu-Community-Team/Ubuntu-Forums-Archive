---
title: "Wireless startup and shutdown problems on 13.04"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by zqjxkv on 2013-04-29
Ever since upgrading from 12.10 to 13.04, I've been getting a lot of wireless problems.

Bootup is slow. The dmesg output shows on my screen with wlan0 is not ready (full output here [http://pastebin.com/cqmnCAz9](http://pastebin.com/cqmnCAz9)).

And on shutdown, it varies but usually I get something along the lines of Caught signal 15, Unknown job: S35networking, mount: / busy, or umount: /run/lock: not mounted.

I've Googled these error messages extensively, but to no avail so far. I've somewhat concluded that it maybe has to do with some race condition regarding my wireless. I'd appreciate any help.

---

### Post by varunendra on 2013-04-29
Your wireless seems to be handled by iwlwifi. I don't see a 'race condition' in the dmesg output you linked to. Also, the last line in the output says "[  105.639436] wlan0: associated" , which means it got connected to some access point. Did it?

Please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the contents of "netinfo.txt" file the script creates.

---

### Post by zqjxkv on 2013-04-29
Did as you asked. Here's the output:

```



*************** info trace ****************






**** uname -a ****




Linux stephenT410 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
	Subsystem: Lenovo Device [17aa:2153]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)
	Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
	Kernel driver in use: iwlwifi




**** lsusb ****




Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 004: ID 17ef:480f Lenovo Integrated Webcam [R5U877]




**** iwconfig ****




wlan0     IEEE 802.11abgn  ESSID:"Columbia U Secure"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=26 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1602  Invalid misc:187   Missed beacon:0






**** rfkill ****




0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
rfcomm                 42641  12 
bnep                   18036  2 
joydev                 17377  0 
snd_hda_codec_hdmi     36913  4 
arc4                   12615  2 
iwldvm                241834  0 
mac80211              606457  1 iwldvm
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
snd_hda_codec_conexant    62000  1 
aesni_intel            55399  2 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_rawmidi            30180  1 snd_seq_midi
thinkpad_acpi          81222  0 
nvidia              11309139  43 
tpm_tis                18675  0 
iwlwifi               173477  1 iwldvm
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_memops       13202  1 videobuf2_vmalloc
nvram                  14362  1 thinkpad_acpi
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
mxm_wmi                13021  0 
snd_timer              29425  2 snd_pcm,snd_seq
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd                    68876  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
wmi                    19070  1 mxm_wmi
btusb                  22474  0 
video                  19390  0 
intel_ips              17978  0 
lpc_ich                17061  0 
soundcore              12680  1 snd
mac_hid                13205  0 
bluetooth             228619  22 bnep,btusb,rfcomm
psmouse                95870  0 
serio_raw              13215  0 
mei                    41158  0 
lp                     17759  0 
microcode              22881  0 
parport                46345  3 lp,ppdev,parport_pc
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   25731  3 
libahci                31364  1 ahci
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
e1000e                198787  0 




**** nm-tool ****






NetworkManager Tool


State: connected (global)


- Device: wlan0  [Columbia U Secure] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           26 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Columbia U Secure: Infra, <MAC address removed>, Freq 5825 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    Columbia U Secure: Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    Columbia U Secure: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    Columbia U Secure: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    Columbia U Secure: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    Steven Nowick's Guest Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Columbia U Secure: Infra, <MAC address removed>, Freq 5805 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    Columbia University: Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 44
    Columbia University: Infra, <MAC address removed>, Freq 5825 MHz, Rate 54 Mb/s, Strength 44
    Columbia University: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    Columbia University: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    Columbia University: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    Columbia University: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    Columbia University: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    Columbia University: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    Columbia U Secure: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    Who the **** is Ken Thompson?: Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 52 WPA2
    Internal:        Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 24 WPA
    Annapurna_Lives: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Columbia University: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59
    Columbia University: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65
    Columbia University: Infra, <MAC address removed>, Freq 5805 MHz, Rate 54 Mb/s, Strength 24
    Columbia U Secure: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2 Enterprise
    Columbia U Secure: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    belkin.4b6:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Columbia U Secure: Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    Steven Nowick's Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Columbia U Secure: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    SMARTCITY-WSN:   Ad-Hoc, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25
    Columbia U Secure: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    Columbia University: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    p53:             Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    Columbia U Secure: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    Columbia U Secure: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    *Columbia U Secure: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 53 WPA2 Enterprise
    chester:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WEP
    Columbia University: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    IRAAS1-guest:    Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22
    SakaAirMac:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Mudd937:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2


  IPv4 Settings:
    Address:         160.39.133.31
    Prefix:          22 (255.255.252.0)
    Gateway:         160.39.132.1


    DNS:             128.59.1.3
    DNS:             128.59.1.4




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Columbia U Secure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000076ef527e7
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0011436F6C756D626961205520536563757265
                    IE: Unknown: 01088B8C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Columbia U Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002963b0e593
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0011436F6C756D626961205520536563757265
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1624000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Steven Nowick's Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005e42ecb3cbb
                    Extra: Last beacon: 6808ms ago
                    IE: Unknown: 001D53746576656E204E6F7769636B2773204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E9D
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301710208
                    IE: Unknown: DD0E0017F2070001010660334BE80C75
          Cell 04 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Internal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000203a1ba4b4b8
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0008496E7465726E616C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180205F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Who the **** is Ken Thompson?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001450ffbc788
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 001D57686F20746865206675636B206973204B656E2054686F6D70736F6E3F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"p53"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035dc33bab6
                    Extra: Last beacon: 6552ms ago
                    IE: Unknown: 0003703533
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F020101660002534000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"Columbia University"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000076ef52b06
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0013436F6C756D62696120556E6976657273697479
                    IE: Unknown: 01088B8C121618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1AED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Columbia U Secure"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008d15df180
                    Extra: Last beacon: 6356ms ago
                    IE: Unknown: 0011436F6C756D626961205520536563757265
                    IE: Unknown: 01088B168C1218243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"Columbia University"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008d15df36a
                    Extra: Last beacon: 6356ms ago
                    IE: Unknown: 0013436F6C756D62696120556E6976657273697479
                    IE: Unknown: 01088B168C1218243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1AED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 10 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Columbia U Secure"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003023d72180
                    Extra: Last beacon: 6348ms ago
                    IE: Unknown: 0011436F6C756D626961205520536563757265
                    IE: Unknown: 01088B168C1218243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"Columbia University"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003023d7236a
                    Extra: Last beacon: 6348ms ago
                    IE: Unknown: 0013436F6C756D62696120556E6976657273697479
                    IE: Unknown: 01088B168C1218243048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0102
                    IE: Unknown: 3202606C
                    IE: Unknown: 2D1AED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED111BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 12 - Address: <MAC address removed>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"Columbia University"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002963b0e741
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0013436F6C756D62696120556E6976657273697479
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030124
                    IE: Unknown: 2D1AED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1624000A000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3424000A000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 13 - Address: <MAC address removed>
                    Channel:165
                    Frequency:5.825 GHz
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Columbia U Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015c1e0f4f31
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0011436F6C756D626961205520536563757265
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0301A5
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1AED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D16A5001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34A5001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000
          Cell 14 - Address: <MAC address removed>
                    Channel:165
                    Frequency:5.825 GHz
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Columbia University"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015c1e0f50df
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0013436F6C756D62696120556E6976657273697479
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 0301A5
                    IE: Unknown: 2D1AED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D16A5001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C33ED011BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34A5001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000






**** resolv ****




# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search columbia.edu




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




[    0.464047] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    1.217797] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[   25.823235] wmi: Mapper loaded
[   25.882992] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   26.016708] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   26.030371] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   26.030375] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   26.030377] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   26.030379] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   26.030381] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   26.030383] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   26.030445] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   26.030615] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[   26.075674] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   30.094115] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   30.094310] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   30.455818] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   30.456011] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   30.706033] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.738126] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.457052] wlan0: authenticate with <MAC address removed>
[   74.510538] wlan0: send auth to <MAC address removed> (try 1/3)
[   74.512574] wlan0: <MAC address removed> denied authentication (status 17)
[   74.910802] wlan0: authenticate with <MAC address removed>
[   74.958699] wlan0: send auth to <MAC address removed> (try 1/3)
[   74.962953] wlan0: <MAC address removed> denied authentication (status 17)
[   75.364943] wlan0: authenticate with <MAC address removed>
[   75.415646] wlan0: send auth to <MAC address removed> (try 1/3)
[   75.437226] wlan0: authenticated
[   75.439992] wlan0: associate with <MAC address removed> (try 1/3)
[   75.449914] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   75.459590] wlan0: associated
[   75.459628] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  129.836208] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  144.738340] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  325.775378] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  362.282188] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues




**************** done ********************

```

The main problem is that it almost always hangs while shutting down. Here's one of the hanging errors: [http://i.imgur.com/ySH0EYt.jpg](http://i.imgur.com/ySH0EYt.jpg).

---

### Post by varunendra on 2013-04-30
The error messages in your screenshot seem normal to me. However following are a few things that may cause a bad connection -
> **zqjxkv said:**
> ```

wlan0     IEEE 802.11abgn  ESSID:"Columbia U Secure"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=**[COLOR="#FF0000"]26 Mb/s[/COLOR]**   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:**[COLOR="#FF0000"]on[/COLOR]**
          Link Quality=**[COLOR="#FF0000"]43/70[/COLOR]**  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1602  Invalid misc:187   Missed beacon:0
..
<snip>
..
wlan0     Scan completed :
          ....<snip>....
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"Columbia University"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:**[COLOR="#800000"]48 Mb/s; 54 Mb/s[/COLOR]**


[COLOR="#FF0000"][  129.836208] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  144.738340] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  325.775378] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues
[  362.282188] iwlwifi 0000:03:00.0: fail to flush all tx fifo queues[/COLOR]

**************** done ********************

```
**1)**
Even though the access point supports upto 54 Mbps speed, the negotiated speed is only 26 Mbps, which may be due to the weak signal you are getting (43/70). Still, you may try to fix the bit rate with -
```
sudo iwconfig wlan0 rate 54M
```
or
```
sudo iwconfig wlan0 rate 54M auto
```
Please note that this 'fixed' rate is not guaranteed to improve speed or connectivity. In some cases it may even worsen the situation. So you will have to experiment with different (supported) speeds yourself.

**2)**
Turn the power management off on wlan0 -
```
sudo iwconfig wlan0 power off
```

**3)**
Since the access points don't support N-channel (speeds higher than 54 Mbps) anyway, disable it on the driver :
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot for the change to take effect.

**4)**
The dmesg errors may be due to a bug in iwlwifi driver : [https://bugzilla.kernel.org/show_bug.cgi?id=48921](https://bugzilla.kernel.org/show_bug.cgi?id=48921)
It may occur frequently if you suspend often : [https://wiki.archlinux.org/index.php/ThinkPad_X230#Suspension](https://wiki.archlinux.org/index.php/ThinkPad_X230#Suspension)

Not sure yet what to do about it. But try the suggestions in points 1, 2 and 3, and post back the result.

Also, if the main problem is system hang during shutdown, the relevant messages won't be found in syslog or dmesg, as they contain messages from the current session only. Immediately after a problematic shutdown/restart, check dmesg.0 and syslog.1 (in /var/log directory). They will contain the message logs from the previous session and may give us hint about the problem.

---

### Post by zqjxkv on 2013-05-05
I've tried all the commands and waited a couple of days before posting to make sure the immediate results were persistent.

My laptop no longer hangs on shutdown. But now it does hang on start-up every now and then with the error that anacron fails, though that sounds like a separate problem.

Thanks for all the help, varunendra. Though still not optimal, it's much more bearable now being able to shutdown properly.

I'll mark the thread as solved for now. Since I don't really prefix option outlined in your signature, I'll just edit the title for now.

---

### Post by varunendra on 2013-05-05
> **zqjxkv said:**
> My laptop no longer hangs on shutdown. But now it does hang on start-up every now and then with the error that anacron fails, though that sounds like a separate problem.
Indeed seems to be a different problem with a different reason. Since it happens at the beginning of the session, you may find hints in the syslog and dmesg logs for current session. Take a look at /var/log/dmesg and /var/log/syslog and note the activities which take too long to finish (the numbers at the beginning of lines in dmesg are time in 'seconds' since the OS loading started). You should post these logs (relevant parts if you can identify them, or whole of it if you can't) if you post a new thread for it.

> I'll mark the thread as solved for now. Since I don't really prefix option outlined in your signature, I'll just edit the title for now.
You're not the first one who couldn't find the prefix box : [http://ubuntuforums.org/showthread.php?t=2141000&page=2](http://ubuntuforums.org/showthread.php?t=2141000&page=2)

---


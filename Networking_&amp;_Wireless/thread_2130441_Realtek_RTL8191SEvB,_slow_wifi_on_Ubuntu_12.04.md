---
title: "Realtek RTL8191SEvB, slow wifi on Ubuntu 12.04"
date: 2013-03-29
forum: Networking &amp; Wireless
---

### Post by noobydooby on 2013-03-29
Hi everybody,

i have win7 an Ubuntu 12.04 installed om my laptop. I wanted to start using Ubuntu more frequently to get to know it a bit better and have noticed that downloads are pretty slow compared to when I'm running win7. I have seen some post with similar problems but I dont uderstand the answers nor linux well eneugh to aply them to my laptop (I tried and suddenly my wireless was gone, luckyly after I restarted my computer everything was fine I think).  I know that the more information you have the easier it will be to help me so I think I have managed to print my system spec.
```

description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3701MiB
     *-cpu
          product: Pentium(R) Dual-Core CPU       T4400  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dtherm cpufreq
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:1c00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: NVIDIA Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:2000(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor
             description: Co-processor
             product: MCP79 Co-processor
             vendor: NVIDIA Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=nvidia latency=0 maxlatency=1 mingnt=3
             resources: irq:18 memory:f0700000-f077ffff
        *-usb:0
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:18 memory:f0786000-f0786fff
        *-usb:1
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:f0789000-f07890ff
        *-usb:2
             description: USB controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: NVIDIA Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:f0787000-f0787fff
        *-usb:3
             description: USB controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: NVIDIA Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:f0789400-f07894ff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:17 memory:f0780000-f0783fff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:22:20:07:13:de
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:19 memory:f0788000-f0788fff ioport:30d0(size=8) memory:f0789c00-f0789cff memory:f0789800-f078980f
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:40 ioport:30e8(size=8) ioport:30dc(size=4) ioport:30e0(size=8) ioport:30d8(size=4) ioport:30c0(size=16) memory:f0784000-f0785fff
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:23 ioport:4000(size=4096) memory:ae000000-afefffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT216 [GeForce GT 230M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:23 memory:ae000000-aeffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:4000(size=128) memory:af000000-af07ffff
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:ac000000-acffffff ioport:b0000000(size=469762048)
           *-display
                description: VGA compatible controller
                product: C79 [GeForce 9100M G]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:23 memory:ac000000-acffffff memory:b0000000-bfffffff memory:ca000000-cbffffff ioport:5000(size=128) memory:c0000000-c001ffff
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:22 ioport:6000(size=4096) memory:f0200000-f03fffff ioport:f0000000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:21 ioport:7000(size=4096) memory:f0400000-f04fffff
           *-network
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 10
                serial: e0:b9:a5:16:df:82
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-39-generic firmware=N/A ip=192.168.1.62 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:21 ioport:7000(size=256) memory:f0400000-f0403fff
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: NVIDIA Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19


```

I hope sombody can help me. 

thanks in andvance

noobydooby

---

### Post by wildmanne39 on 2013-03-29
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by noobydooby on 2013-03-29
hey wild man,

thanks for the quick answer. I saw you helped the other guy who had a similar problem. unfortunately the file seems to be to big to be uploaded (30.4 Kb).

---

### Post by wildmanne39 on 2013-03-29
It should not be, you can post it by hitting the # and copying the text between the brackets.

It is possible that you are trying to upload the script and not the textinfo file.
Thanks

---

### Post by noobydooby on 2013-03-29
ok here it goes```

*************** info trace ****************



**** uname -a ****


Linux ubuntu 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Mitac Device [1071:9072]
    Kernel driver in use: forcedeth
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0505 Genesys Logic, Inc. 
Bus 003 Device 002: ID 24ae:2000  


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"interneq"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1350   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
vesafb                 13844  1 
nvidia              12319264  60 
snd_hda_codec_hdmi     32474  1 
bnep                   18281  2 
snd_hda_codec_realtek   224173  1 
rfcomm                 47604  0 
bluetooth             180153  10 bnep,rfcomm
arc4                   12529  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_intel          33719  3 
lp                     17799  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
parport                46562  3 parport_pc,ppdev,lp
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192se              99989  0 
snd_seq_midi           13324  0 
rtlwifi               111245  1 rtl8192se
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
snd_timer              29990  2 snd_pcm,snd_seq
joydev                 17693  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506862  2 rtl8192se,rtlwifi
videodev               98259  1 uvcvideo
usbhid                 47238  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ums_realtek            18248  0 
hid                    99636  1 usbhid
v4l2_compat_ioctl32    17128  1 videodev
psmouse                97485  0 
soundcore              15091  1 snd
i2c_nforce2            13058  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  2 rtlwifi,mac80211
shpchp                 37201  0 
video                  19651  0 
serio_raw              13211  0 
mac_hid                13253  0 
binfmt_misc            17540  1 
usb_storage            49243  1 ums_realtek
forcedeth              63460  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [interneq] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    JD Home:         Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    FRITZ!Box Fon WLAN 7170: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    WLAN-4C4C14:     Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *interneq:       Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 82 WPA2
    luft:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    ALICE-WLAN55:    Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA2
    TP-LINK_C4BFE2:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    WLAN-8EC665:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.1.62
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
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
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"interneq"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000227998847
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 0008696E7465726E6571
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1016FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1609000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010003127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A880001C286EA8571021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN55"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bb33f50ebd
                    Extra: Last beacon: 744ms ago
                    IE: Unknown: 000C414C4943452D574C414E3535
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD900050F204104A00011010440001021041000100103B00010310470010000000000000000300001CC63C1F1F721021000848616E73654E657410230008415237353035535710240007312E30302E31361042000A323033313031343135351054000800060050F20400011011001D48616E73654E657420576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD1E00904C336E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050000000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"JD Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000462a1d03d
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 00074A4420486F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0600000000000000000000000000000000000000
                    IE: Unknown: 3416040D0600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD650050F204104A0001101044000102103B00010310470010D0F0CFDE0E75304AE4DA0FB6A21003101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000765ca69
                    Extra: Last beacon: 496ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"luft"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bb2ff17627
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 00046C756674
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"WLAN-4C4C14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c8efb2c4a3
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000B574C414E2D344334433134
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0E181AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160D0F1600000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E181AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D0F1600000000000000000000000000000000000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search localdomain


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


[   13.293054] rtl8192se 0000:06:00.0: PCI INT A -> Link[Z00I] -> GSI 21 (level, low) -> IRQ 21
[   13.293062] rtl8192se 0000:06:00.0: setting latency timer to 64
[   13.302432] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   13.302561] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   13.302562] Loading firmware rtlwifi/rtl8192sefw.bin
[   19.790640] type=1400 audit(1364565711.433:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=935 comm="apparmor_parser"
[   19.791149] type=1400 audit(1364565711.433:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=935 comm="apparmor_parser"
[   22.913499] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.913852] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  142.027544] wlan0: authenticate with <MAC address removed> (try 1)
[  142.035230] wlan0: authenticated
[  142.035509] wlan0: associate with <MAC address removed> (try 1)
[  142.039954] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  142.039958] wlan0: associated
[  142.052327] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.067159] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  152.088606] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  152.959357] wlan0: authenticate with <MAC address removed> (try 1)
[  153.156099] wlan0: authenticate with <MAC address removed> (try 2)
[  153.356116] wlan0: authenticate with <MAC address removed> (try 3)
[  153.556074] wlan0: authentication with <MAC address removed> timed out
[  159.582308] wlan0: authenticate with <MAC address removed> (try 1)
[  159.589984] wlan0: authenticated
[  159.590442] wlan0: associate with <MAC address removed> (try 1)
[  159.629972] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  159.629976] wlan0: associated
[  169.659878] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  169.688975] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  170.567491] wlan0: authenticate with <MAC address removed> (try 1)
[  170.576036] wlan0: authenticated
[  170.576305] wlan0: associate with <MAC address removed> (try 1)
[  170.605464] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  170.605471] wlan0: associated
[  180.638311] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  180.653636] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  181.526504] wlan0: authenticate with <MAC address removed> (try 1)
[  181.534156] wlan0: authenticated
[  181.534555] wlan0: associate with <MAC address removed> (try 1)
[  181.568156] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  181.568163] wlan0: associated
[  191.594822] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  191.609241] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  192.478158] wlan0: authenticate with <MAC address removed> (try 1)
[  192.485914] wlan0: authenticated
[  192.488346] wlan0: associate with <MAC address removed> (try 1)
[  192.518787] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  192.518794] wlan0: associated
[  201.020582] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  622.049211] wlan0: authenticate with <MAC address removed> (try 1)
[  622.056959] wlan0: authenticated
[  622.057166] wlan0: associate with <MAC address removed> (try 1)
[  622.078322] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  622.078327] wlan0: associated
[  632.112541] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  632.133146] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  633.008217] wlan0: authenticate with <MAC address removed> (try 1)
[  633.015899] wlan0: authenticated
[  633.016347] wlan0: associate with <MAC address removed> (try 1)
[  633.050024] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  633.050031] wlan0: associated
[  643.074404] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  643.084970] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  643.966177] wlan0: authenticate with <MAC address removed> (try 1)
[  643.973875] wlan0: authenticated
[  643.974105] wlan0: associate with <MAC address removed> (try 1)
[  643.998608] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  643.998612] wlan0: associated
[  651.668070] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  683.140152] wlan0: authenticate with <MAC address removed> (try 1)
[  683.340074] wlan0: authenticate with <MAC address removed> (try 2)
[  683.540059] wlan0: authenticate with <MAC address removed> (try 3)
[  683.740071] wlan0: authentication with <MAC address removed> timed out
[  695.921865] wlan0: direct probe to <MAC address removed> (try 1/3)
[  696.120138] wlan0: direct probe to <MAC address removed> (try 2/3)
[  696.320090] wlan0: direct probe to <MAC address removed> (try 3/3)
[  696.524088] wlan0: direct probe to <MAC address removed> timed out
[  702.700112] wlan0: authenticate with <MAC address removed> (try 1)
[  702.900074] wlan0: authenticate with <MAC address removed> (try 2)
[  703.100102] wlan0: authenticate with <MAC address removed> (try 3)
[  703.300069] wlan0: authentication with <MAC address removed> timed out
[  709.489520] wlan0: direct probe to <MAC address removed> (try 1/3)
[  709.510971] wlan0: direct probe responded
[  709.516089] wlan0: authenticate with <MAC address removed> (try 1)
[  709.716072] wlan0: authenticate with <MAC address removed> (try 2)
[  709.916060] wlan0: authenticate with <MAC address removed> (try 3)
[  710.116058] wlan0: authentication with <MAC address removed> timed out
[  716.300084] wlan0: direct probe to <MAC address removed> (try 1/3)
[  716.500078] wlan0: direct probe to <MAC address removed> (try 2/3)
[  716.700076] wlan0: direct probe to <MAC address removed> (try 3/3)
[  716.900076] wlan0: direct probe to <MAC address removed> timed out
[  723.077996] wlan0: direct probe to <MAC address removed> (try 1/3)
[  723.091831] wlan0: direct probe responded
[  723.104058] wlan0: authenticate with <MAC address removed> (try 1)
[  723.304096] wlan0: authenticate with <MAC address removed> (try 2)
[  723.504060] wlan0: authenticate with <MAC address removed> (try 3)
[  723.704058] wlan0: authentication with <MAC address removed> timed out
[  729.888300] wlan0: direct probe to <MAC address removed> (try 1/3)
[  730.088146] wlan0: direct probe to <MAC address removed> (try 2/3)
[  730.288084] wlan0: direct probe to <MAC address removed> (try 3/3)
[  730.488064] wlan0: direct probe to <MAC address removed> timed out
[  745.855557] wlan0: authenticate with <MAC address removed> (try 1)
[  746.052087] wlan0: authenticate with <MAC address removed> (try 2)
[  746.255461] wlan0: authenticate with <MAC address removed> (try 3)
[  746.452076] wlan0: authentication with <MAC address removed> timed out
[  758.650692] wlan0: direct probe to <MAC address removed> (try 1/3)
[  758.848064] wlan0: direct probe to <MAC address removed> (try 2/3)
[  759.048067] wlan0: direct probe to <MAC address removed> (try 3/3)
[  759.248091] wlan0: direct probe to <MAC address removed> timed out
[  765.420470] wlan0: authenticate with <MAC address removed> (try 1)
[  765.620071] wlan0: authenticate with <MAC address removed> (try 2)
[  765.820115] wlan0: authenticate with <MAC address removed> (try 3)
[  766.020096] wlan0: authentication with <MAC address removed> timed out
[  772.192154] wlan0: direct probe to <MAC address removed> (try 1/3)
[  772.392071] wlan0: direct probe to <MAC address removed> (try 2/3)
[  772.592065] wlan0: direct probe to <MAC address removed> (try 3/3)
[  772.792092] wlan0: direct probe to <MAC address removed> timed out
[  778.968298] wlan0: direct probe to <MAC address removed> (try 1/3)
[  779.168084] wlan0: direct probe to <MAC address removed> (try 2/3)
[  779.368096] wlan0: direct probe to <MAC address removed> (try 3/3)
[  779.568057] wlan0: direct probe to <MAC address removed> timed out
[  785.748299] wlan0: direct probe to <MAC address removed> (try 1/3)
[  785.948058] wlan0: direct probe to <MAC address removed> (try 2/3)
[  786.148088] wlan0: direct probe to <MAC address removed> (try 3/3)
[  786.348114] wlan0: direct probe to <MAC address removed> timed out
[  798.517183] wlan0: direct probe to <MAC address removed> (try 1/3)
[  798.716074] wlan0: direct probe to <MAC address removed> (try 2/3)
[  798.916074] wlan0: direct probe to <MAC address removed> (try 3/3)
[  799.116063] wlan0: direct probe to <MAC address removed> timed out
[  855.868165] wlan0: direct probe to <MAC address removed> (try 1/3)
[  856.068068] wlan0: direct probe to <MAC address removed> (try 2/3)
[  856.268075] wlan0: direct probe to <MAC address removed> (try 3/3)
[  856.468117] wlan0: direct probe to <MAC address removed> timed out
[  862.640710] wlan0: direct probe to <MAC address removed> (try 1/3)
[  862.840076] wlan0: direct probe to <MAC address removed> (try 2/3)
[  863.040066] wlan0: direct probe to <MAC address removed> (try 3/3)
[  863.240076] wlan0: direct probe to <MAC address removed> timed out
[  869.416978] wlan0: direct probe to <MAC address removed> (try 1/3)
[  869.616063] wlan0: direct probe to <MAC address removed> (try 2/3)
[  869.816079] wlan0: direct probe to <MAC address removed> (try 3/3)
[  870.016082] wlan0: direct probe to <MAC address removed> timed out
[  876.200783] wlan0: direct probe to <MAC address removed> (try 1/3)
[  876.280065] wlan0: direct probe responded
[  876.296047] wlan0: authenticate with <MAC address removed> (try 1)
[  876.496060] wlan0: authenticate with <MAC address removed> (try 2)
[  876.696038] wlan0: authenticate with <MAC address removed> (try 3)
[  876.896051] wlan0: authentication with <MAC address removed> timed out
[  883.084091] wlan0: direct probe to <MAC address removed> (try 1/3)
[  883.162639] wlan0: direct probe responded
[  883.166282] wlan0: authenticate with <MAC address removed> (try 1)
[  883.364070] wlan0: authenticate with <MAC address removed> (try 2)
[  883.564070] wlan0: authenticate with <MAC address removed> (try 3)
[  883.764075] wlan0: authentication with <MAC address removed> timed out
[  889.944071] wlan0: direct probe to <MAC address removed> (try 1/3)
[  889.966931] wlan0: direct probe responded
[  889.972065] wlan0: authenticate with <MAC address removed> (try 1)
[  890.172063] wlan0: authenticate with <MAC address removed> (try 2)
[  890.372101] wlan0: authenticate with <MAC address removed> (try 3)
[  890.572092] wlan0: authentication with <MAC address removed> timed out
[  895.991838] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  898.689269] wlan0: direct probe to <MAC address removed> (try 1/3)
[  898.888067] wlan0: direct probe to <MAC address removed> (try 2/3)
[  899.088063] wlan0: direct probe to <MAC address removed> (try 3/3)
[  899.288070] wlan0: direct probe to <MAC address removed> timed out
[  905.488083] wlan0: direct probe to <MAC address removed> (try 1/3)
[  905.688051] wlan0: direct probe to <MAC address removed> (try 2/3)
[  905.888093] wlan0: direct probe to <MAC address removed> (try 3/3)
[  906.088090] wlan0: direct probe to <MAC address removed> timed out
[  918.264136] wlan0: direct probe to <MAC address removed> (try 1/3)
[  918.464098] wlan0: direct probe to <MAC address removed> (try 2/3)
[  918.664099] wlan0: direct probe to <MAC address removed> (try 3/3)
[  918.864090] wlan0: direct probe to <MAC address removed> timed out
[  925.036926] wlan0: direct probe to <MAC address removed> (try 1/3)
[  925.236053] wlan0: direct probe to <MAC address removed> (try 2/3)
[  925.436052] wlan0: direct probe to <MAC address removed> (try 3/3)
[  925.636124] wlan0: direct probe to <MAC address removed> timed out
[  931.828878] wlan0: direct probe to <MAC address removed> (try 1/3)
[  932.030615] wlan0: direct probe to <MAC address removed> (try 2/3)
[  932.228094] wlan0: direct probe to <MAC address removed> (try 3/3)
[  932.428044] wlan0: direct probe to <MAC address removed> timed out
[  944.617844] wlan0: direct probe to <MAC address removed> (try 1/3)
[  944.816090] wlan0: direct probe to <MAC address removed> (try 2/3)
[  945.016064] wlan0: direct probe to <MAC address removed> (try 3/3)
[  945.220039] wlan0: direct probe to <MAC address removed> timed out
[  951.412100] wlan0: direct probe to <MAC address removed> (try 1/3)
[  951.492484] wlan0: direct probe responded
[  951.492558] wlan0: authenticate with <MAC address removed> (try 1)
[  951.692074] wlan0: authenticate with <MAC address removed> (try 2)
[  951.892058] wlan0: authenticate with <MAC address removed> (try 3)
[  952.092075] wlan0: authentication with <MAC address removed> timed out
[ 1095.714935] wlan0: authenticate with <MAC address removed> (try 1)
[ 1095.716597] wlan0: authenticated
[ 1095.716933] wlan0: associate with <MAC address removed> (try 1)
[ 1095.728088] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1095.728093] wlan0: associated
[ 1095.743116] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1106.720039] wlan0: no IPv6 routers present


**************** done ********************
```

it realy was over 30 kb

---

### Post by wildmanne39 on 2013-03-29
That driver is a problem in ubuntu but there are ways to fix it, lets start with:
```
echo 'options rtl8192se swenc=1' | sudo tee /etc/modprobe.d/rtl8192se.conf
```
Then go into your router settings and change 802.11bgn to 802.11bg save and let your router reboot.

Also set your wireless settings in network manager to match the screenshoots.

Just copy and paste the command for accuracy.
Thanks

---

### Post by noobydooby on 2013-03-29
I changed the configuration as you told me, and restarted the router. i can connect to the internet but i cant get into the router configuration anymore. i get an error mesage from my browser. has this happened to you befor?

---

### Post by wildmanne39 on 2013-03-29
No, are you hardwired to the router? you should be to make changes to the configuration.
What error message?
Thanks

---

### Post by noobydooby on 2013-03-29
Ok i have to corect myself. I just got into the router confi again. What doesnt seem to work anymore is the just typing "alice.box" i have to type in the ip adress.

---

### Post by wildmanne39 on 2013-03-29
I did not know that you could get into the router without typing the ip address that is the correct way to do it.
So is your speed better?
Thanks

---

### Post by noobydooby on 2013-03-29
If i type "alice.box" into my browser i get
```
Server not found
      
      
      
      
      
        
        
          Firefox can't find the server at www.alice.box.
        

        
        

  Check the address for typing errors such as
    ww.example.com instead of
    www.example.com
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.
```

I have to look up the ip and type it in. There are worse things but it was easyer when i could just type the name.

---

### Post by noobydooby on 2013-03-29
well I think it is possible thanks to WPS but i dont know anything about these kind of things :). I wil try to download somthing and to see if the speed has changed. ill be back in a couple of minutes.

---

### Post by wildmanne39 on 2013-03-29
Okay.

---

### Post by noobydooby on 2013-03-29
I tried downloading a game with th ubuntu software center and it still feels kind of slow.  I tried this to determin my speed more accuratly. dont know if its a good test for this purpose but i read it on some post. ```
 ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=51 time=42.8 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=51 time=43.1 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=51 time=42.1 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 42.180/42.716/43.127/0.396 ms



```

---

### Post by wildmanne39 on 2013-03-29
Downloads with software center can be slow, I suggest type in internet speed test and try one of those to see what your actual speed is.

Also how fast is your connection to begin with according to your isp?
Thanks

---

### Post by noobydooby on 2013-03-29
Hey wild man,

acording to my isp i have a 16000 conection. I did a speed test with the following page "http://www.wieistmeineip.de/speedtest/" yesterday runnig win7 and got a over 300000 kbit/s (download) which is kind of weird because its more than i pay for. Running Ubuntu its moro around 6000. I just repeated the test an have the following result: 5441 kbit/s download an 628 upload. Which the page itself rates as much to slow      [h=1][/h]

---

### Post by wildmanne39 on 2013-03-29
Can you attach a screenshot of your test please?

Do you know what your isp speed is suppose to be in mbps? 
This is mine.

---

### Post by noobydooby on 2013-03-29
Hi, sorry for the delay. I seem to be to much of a noob to do a screen shot. I tried out the samespeed test as you an have the following results. Download speed 5.25Mbps, Upload 0.60 Mbps and Ping 139 ms. I am sure that the 16000 stands for 16000 kbit/s or 16 Mbps.

---

### Post by noobydooby on 2013-03-29
I got it

---

### Post by wildmanne39 on 2013-03-29
Probably,  that is not actually that bad for the speed you have from your isp.

Does it load web pages a lot faster then before? I believe it does, you can remove the infotext file from your home folder and run the script again and post the new file and I will see what differences the changes made.
Thanks

---

### Post by noobydooby on 2013-03-29
and here is the other one

---

### Post by noobydooby on 2013-03-29
Hey,

here is the new file ```

*************** info trace ****************



**** uname -a ****


Linux ubuntu 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Mitac Device [1071:9072]
    Kernel driver in use: forcedeth
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0505 Genesys Logic, Inc. 
Bus 003 Device 002: ID 24ae:2000  


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:"interneq"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1421   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
vesafb                 13844  1 
nvidia              12319264  60 
snd_hda_codec_hdmi     32474  1 
bnep                   18281  2 
snd_hda_codec_realtek   224173  1 
rfcomm                 47604  0 
bluetooth             180153  10 bnep,rfcomm
arc4                   12529  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_intel          33719  3 
lp                     17799  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
parport                46562  3 parport_pc,ppdev,lp
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192se              99989  0 
snd_seq_midi           13324  0 
rtlwifi               111245  1 rtl8192se
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
snd_timer              29990  2 snd_pcm,snd_seq
joydev                 17693  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506862  2 rtl8192se,rtlwifi
videodev               98259  1 uvcvideo
usbhid                 47238  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ums_realtek            18248  0 
hid                    99636  1 usbhid
v4l2_compat_ioctl32    17128  1 videodev
psmouse                97485  0 
soundcore              15091  1 snd
i2c_nforce2            13058  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  2 rtlwifi,mac80211
shpchp                 37201  0 
video                  19651  0 
serio_raw              13211  0 
mac_hid                13253  0 
binfmt_misc            17540  1 
usb_storage            49243  1 ums_realtek
forcedeth              63460  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0  [interneq] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    JD Home:         Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    FRITZ!Box Fon WLAN 7170: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    WLAN-4C4C14:     Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ALICE-WLAN55:    Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *interneq:       Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 85 WPA2
    FRITZ!Box Fon WLAN 7113: Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    luft:            Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA

  IPv4 Settings:
    Address:         192.168.1.62
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
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
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"interneq"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000134598166
                    Extra: Last beacon: 116ms ago
                    IE: Unknown: 0008696E7465726E6571
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A880001C286EA8571021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN55"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bccf5e7940
                    Extra: Last beacon: 732ms ago
                    IE: Unknown: 000C414C4943452D574C414E3535
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD900050F204104A00011010440001021041000100103B00010310470010000000000000000300001CC63C1F1F721021000848616E73654E657410230008415237353035535710240007312E30302E31361042000A323033313031343135351054000800060050F20400011011001D48616E73654E657420576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD1E00904C336E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050000000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"JD Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005fe0bd507
                    Extra: Last beacon: 488ms ago
                    IE: Unknown: 00074A4420486F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16040D0600000000000000000000000000000000000000
                    IE: Unknown: 3416040D0600000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD650050F204104A0001101044000102103B00010310470010D0F0CFDE0E75304AE4DA0FB6A21003101021000341564D1023000446426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000caac6234
                    Extra: Last beacon: 412ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7170"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cbc9c3233
                    Extra: Last beacon: 476ms ago
                    IE: Unknown: 0017465249545A21426F7820466F6E20574C414E2037313730
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
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
          Cell 06 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"WLAN-4C4C14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca8b1ad183
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000B574C414E2D344334433134
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0E181AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160D0F1600000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E181AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D0F1600000000000000000000000000000000000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


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


[   13.293054] rtl8192se 0000:06:00.0: PCI INT A -> Link[Z00I] -> GSI 21 (level, low) -> IRQ 21
[   13.293062] rtl8192se 0000:06:00.0: setting latency timer to 64
[   13.302432] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   13.302561] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   13.302562] Loading firmware rtlwifi/rtl8192sefw.bin
[   19.790640] type=1400 audit(1364565711.433:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=935 comm="apparmor_parser"
[   19.791149] type=1400 audit(1364565711.433:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=935 comm="apparmor_parser"
[   22.913499] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.913852] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  142.027544] wlan0: authenticate with <MAC address removed> (try 1)
[  142.035230] wlan0: authenticated
[  142.035509] wlan0: associate with <MAC address removed> (try 1)
[  142.039954] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  142.039958] wlan0: associated
[  142.052327] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.067159] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  152.088606] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  152.959357] wlan0: authenticate with <MAC address removed> (try 1)
[  153.156099] wlan0: authenticate with <MAC address removed> (try 2)
[  153.356116] wlan0: authenticate with <MAC address removed> (try 3)
[  153.556074] wlan0: authentication with <MAC address removed> timed out
[  159.582308] wlan0: authenticate with <MAC address removed> (try 1)
[  159.589984] wlan0: authenticated
[  159.590442] wlan0: associate with <MAC address removed> (try 1)
[  159.629972] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  159.629976] wlan0: associated
[  169.659878] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  169.688975] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  170.567491] wlan0: authenticate with <MAC address removed> (try 1)
[  170.576036] wlan0: authenticated
[  170.576305] wlan0: associate with <MAC address removed> (try 1)
[  170.605464] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  170.605471] wlan0: associated
[  180.638311] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  180.653636] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  181.526504] wlan0: authenticate with <MAC address removed> (try 1)
[  181.534156] wlan0: authenticated
[  181.534555] wlan0: associate with <MAC address removed> (try 1)
[  181.568156] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  181.568163] wlan0: associated
[  191.594822] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  191.609241] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  192.478158] wlan0: authenticate with <MAC address removed> (try 1)
[  192.485914] wlan0: authenticated
[  192.488346] wlan0: associate with <MAC address removed> (try 1)
[  192.518787] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  192.518794] wlan0: associated
[  201.020582] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  622.049211] wlan0: authenticate with <MAC address removed> (try 1)
[  622.056959] wlan0: authenticated
[  622.057166] wlan0: associate with <MAC address removed> (try 1)
[  622.078322] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  622.078327] wlan0: associated
[  632.112541] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  632.133146] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  633.008217] wlan0: authenticate with <MAC address removed> (try 1)
[  633.015899] wlan0: authenticated
[  633.016347] wlan0: associate with <MAC address removed> (try 1)
[  633.050024] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  633.050031] wlan0: associated
[  643.074404] wlan0: disassociating from <MAC address removed> by local choice (reason=3)
[  643.084970] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  643.966177] wlan0: authenticate with <MAC address removed> (try 1)
[  643.973875] wlan0: authenticated
[  643.974105] wlan0: associate with <MAC address removed> (try 1)
[  643.998608] wlan0: RX ReassocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  643.998612] wlan0: associated
[  651.668070] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  683.140152] wlan0: authenticate with <MAC address removed> (try 1)
[  683.340074] wlan0: authenticate with <MAC address removed> (try 2)
[  683.540059] wlan0: authenticate with <MAC address removed> (try 3)
[  683.740071] wlan0: authentication with <MAC address removed> timed out
[  695.921865] wlan0: direct probe to <MAC address removed> (try 1/3)
[  696.120138] wlan0: direct probe to <MAC address removed> (try 2/3)
[  696.320090] wlan0: direct probe to <MAC address removed> (try 3/3)
[  696.524088] wlan0: direct probe to <MAC address removed> timed out
[  702.700112] wlan0: authenticate with <MAC address removed> (try 1)
[  702.900074] wlan0: authenticate with <MAC address removed> (try 2)
[  703.100102] wlan0: authenticate with <MAC address removed> (try 3)
[  703.300069] wlan0: authentication with <MAC address removed> timed out
[  709.489520] wlan0: direct probe to <MAC address removed> (try 1/3)
[  709.510971] wlan0: direct probe responded
[  709.516089] wlan0: authenticate with <MAC address removed> (try 1)
[  709.716072] wlan0: authenticate with <MAC address removed> (try 2)
[  709.916060] wlan0: authenticate with <MAC address removed> (try 3)
[  710.116058] wlan0: authentication with <MAC address removed> timed out
[  716.300084] wlan0: direct probe to <MAC address removed> (try 1/3)
[  716.500078] wlan0: direct probe to <MAC address removed> (try 2/3)
[  716.700076] wlan0: direct probe to <MAC address removed> (try 3/3)
[  716.900076] wlan0: direct probe to <MAC address removed> timed out
[  723.077996] wlan0: direct probe to <MAC address removed> (try 1/3)
[  723.091831] wlan0: direct probe responded
[  723.104058] wlan0: authenticate with <MAC address removed> (try 1)
[  723.304096] wlan0: authenticate with <MAC address removed> (try 2)
[  723.504060] wlan0: authenticate with <MAC address removed> (try 3)
[  723.704058] wlan0: authentication with <MAC address removed> timed out
[  729.888300] wlan0: direct probe to <MAC address removed> (try 1/3)
[  730.088146] wlan0: direct probe to <MAC address removed> (try 2/3)
[  730.288084] wlan0: direct probe to <MAC address removed> (try 3/3)
[  730.488064] wlan0: direct probe to <MAC address removed> timed out
[  745.855557] wlan0: authenticate with <MAC address removed> (try 1)
[  746.052087] wlan0: authenticate with <MAC address removed> (try 2)
[  746.255461] wlan0: authenticate with <MAC address removed> (try 3)
[  746.452076] wlan0: authentication with <MAC address removed> timed out
[  758.650692] wlan0: direct probe to <MAC address removed> (try 1/3)
[  758.848064] wlan0: direct probe to <MAC address removed> (try 2/3)
[  759.048067] wlan0: direct probe to <MAC address removed> (try 3/3)
[  759.248091] wlan0: direct probe to <MAC address removed> timed out
[  765.420470] wlan0: authenticate with <MAC address removed> (try 1)
[  765.620071] wlan0: authenticate with <MAC address removed> (try 2)
[  765.820115] wlan0: authenticate with <MAC address removed> (try 3)
[  766.020096] wlan0: authentication with <MAC address removed> timed out
[  772.192154] wlan0: direct probe to <MAC address removed> (try 1/3)
[  772.392071] wlan0: direct probe to <MAC address removed> (try 2/3)
[  772.592065] wlan0: direct probe to <MAC address removed> (try 3/3)
[  772.792092] wlan0: direct probe to <MAC address removed> timed out
[  778.968298] wlan0: direct probe to <MAC address removed> (try 1/3)
[  779.168084] wlan0: direct probe to <MAC address removed> (try 2/3)
[  779.368096] wlan0: direct probe to <MAC address removed> (try 3/3)
[  779.568057] wlan0: direct probe to <MAC address removed> timed out
[  785.748299] wlan0: direct probe to <MAC address removed> (try 1/3)
[  785.948058] wlan0: direct probe to <MAC address removed> (try 2/3)
[  786.148088] wlan0: direct probe to <MAC address removed> (try 3/3)
[  786.348114] wlan0: direct probe to <MAC address removed> timed out
[  798.517183] wlan0: direct probe to <MAC address removed> (try 1/3)
[  798.716074] wlan0: direct probe to <MAC address removed> (try 2/3)
[  798.916074] wlan0: direct probe to <MAC address removed> (try 3/3)
[  799.116063] wlan0: direct probe to <MAC address removed> timed out
[  855.868165] wlan0: direct probe to <MAC address removed> (try 1/3)
[  856.068068] wlan0: direct probe to <MAC address removed> (try 2/3)
[  856.268075] wlan0: direct probe to <MAC address removed> (try 3/3)
[  856.468117] wlan0: direct probe to <MAC address removed> timed out
[  862.640710] wlan0: direct probe to <MAC address removed> (try 1/3)
[  862.840076] wlan0: direct probe to <MAC address removed> (try 2/3)
[  863.040066] wlan0: direct probe to <MAC address removed> (try 3/3)
[  863.240076] wlan0: direct probe to <MAC address removed> timed out
[  869.416978] wlan0: direct probe to <MAC address removed> (try 1/3)
[  869.616063] wlan0: direct probe to <MAC address removed> (try 2/3)
[  869.816079] wlan0: direct probe to <MAC address removed> (try 3/3)
[  870.016082] wlan0: direct probe to <MAC address removed> timed out
[  876.200783] wlan0: direct probe to <MAC address removed> (try 1/3)
[  876.280065] wlan0: direct probe responded
[  876.296047] wlan0: authenticate with <MAC address removed> (try 1)
[  876.496060] wlan0: authenticate with <MAC address removed> (try 2)
[  876.696038] wlan0: authenticate with <MAC address removed> (try 3)
[  876.896051] wlan0: authentication with <MAC address removed> timed out
[  883.084091] wlan0: direct probe to <MAC address removed> (try 1/3)
[  883.162639] wlan0: direct probe responded
[  883.166282] wlan0: authenticate with <MAC address removed> (try 1)
[  883.364070] wlan0: authenticate with <MAC address removed> (try 2)
[  883.564070] wlan0: authenticate with <MAC address removed> (try 3)
[  883.764075] wlan0: authentication with <MAC address removed> timed out
[  889.944071] wlan0: direct probe to <MAC address removed> (try 1/3)
[  889.966931] wlan0: direct probe responded
[  889.972065] wlan0: authenticate with <MAC address removed> (try 1)
[  890.172063] wlan0: authenticate with <MAC address removed> (try 2)
[  890.372101] wlan0: authenticate with <MAC address removed> (try 3)
[  890.572092] wlan0: authentication with <MAC address removed> timed out
[  895.991838] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  898.689269] wlan0: direct probe to <MAC address removed> (try 1/3)
[  898.888067] wlan0: direct probe to <MAC address removed> (try 2/3)
[  899.088063] wlan0: direct probe to <MAC address removed> (try 3/3)
[  899.288070] wlan0: direct probe to <MAC address removed> timed out
[  905.488083] wlan0: direct probe to <MAC address removed> (try 1/3)
[  905.688051] wlan0: direct probe to <MAC address removed> (try 2/3)
[  905.888093] wlan0: direct probe to <MAC address removed> (try 3/3)
[  906.088090] wlan0: direct probe to <MAC address removed> timed out
[  918.264136] wlan0: direct probe to <MAC address removed> (try 1/3)
[  918.464098] wlan0: direct probe to <MAC address removed> (try 2/3)
[  918.664099] wlan0: direct probe to <MAC address removed> (try 3/3)
[  918.864090] wlan0: direct probe to <MAC address removed> timed out
[  925.036926] wlan0: direct probe to <MAC address removed> (try 1/3)
[  925.236053] wlan0: direct probe to <MAC address removed> (try 2/3)
[  925.436052] wlan0: direct probe to <MAC address removed> (try 3/3)
[  925.636124] wlan0: direct probe to <MAC address removed> timed out
[  931.828878] wlan0: direct probe to <MAC address removed> (try 1/3)
[  932.030615] wlan0: direct probe to <MAC address removed> (try 2/3)
[  932.228094] wlan0: direct probe to <MAC address removed> (try 3/3)
[  932.428044] wlan0: direct probe to <MAC address removed> timed out
[  944.617844] wlan0: direct probe to <MAC address removed> (try 1/3)
[  944.816090] wlan0: direct probe to <MAC address removed> (try 2/3)
[  945.016064] wlan0: direct probe to <MAC address removed> (try 3/3)
[  945.220039] wlan0: direct probe to <MAC address removed> timed out
[  951.412100] wlan0: direct probe to <MAC address removed> (try 1/3)
[  951.492484] wlan0: direct probe responded
[  951.492558] wlan0: authenticate with <MAC address removed> (try 1)
[  951.692074] wlan0: authenticate with <MAC address removed> (try 2)
[  951.892058] wlan0: authenticate with <MAC address removed> (try 3)
[  952.092075] wlan0: authentication with <MAC address removed> timed out
[ 1095.714935] wlan0: authenticate with <MAC address removed> (try 1)
[ 1095.716597] wlan0: authenticated
[ 1095.716933] wlan0: associate with <MAC address removed> (try 1)
[ 1095.728088] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1095.728093] wlan0: associated
[ 1095.743116] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1106.720039] wlan0: no IPv6 routers present
[11809.525658] wlan0: deauthenticated from <MAC address removed> (Reason: 6)
[11810.658816] wlan0: authenticate with <MAC address removed> (try 1)
[11810.856036] wlan0: authenticate with <MAC address removed> (try 2)
[11811.056071] wlan0: authenticate with <MAC address removed> (try 3)
[11811.256073] wlan0: authentication with <MAC address removed> timed out
[11817.276124] wlan0: authenticate with <MAC address removed> (try 1)
[11817.279729] wlan0: authenticated
[11817.280230] wlan0: associate with <MAC address removed> (try 1)
[11817.282525] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[11817.282532] wlan0: associated
[12012.120886] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[12148.931105] wlan0: authenticate with <MAC address removed> (try 1)
[12148.932749] wlan0: authenticated
[12148.933149] wlan0: associate with <MAC address removed> (try 1)
[12148.935396] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[12148.935400] wlan0: associated
[12159.376074] wlan0: no IPv6 routers present


**************** done ********************


```

Probably you are right and it was just the download center that got me this "slow" feeling

---

### Post by wildmanne39 on 2013-03-29
Truthfully when I had that speed from my isp your download speeds are about the best I could do too.

Do you set your setting to match the screenshots I posted earlier?

When this driver causes slow internet speed it is usually real slow which is what you had before because you had a lot of packet loss.

So it may be about the best it will do.
Thanks

---

### Post by noobydooby on 2013-03-29
Yes i did. should i leave them that way or is it better if i go back the way they where. Can you explain to me what i changed. I thing i read somewhere that the n in the rooter configuration stands for negotiating which means that it always negotiates the best speed am i wright? What do the connection setings do 8.8.8.8,  8.8.4.4?

---

### Post by wildmanne39 on 2013-03-29
Can you confirm that 802.11bgn is changed to 802.11bg? sometimes the settings do not save propely.
I have to go to the doctor, be back in a few hours.
Thanks

---

### Post by noobydooby on 2013-03-29
Yes. I checked again an it is 802.11b/g (54 Mbit/s). Ok godd luck at the doc and manny thanks for your time.

---

### Post by wildmanne39 on 2013-03-29
> Yes i did. should i leave them that way or is it better if i go back the way they where.
Yes
> Can you explain to me what i changed. I thing i read somewhere that the n in the rooter configuration stands for negotiating which means that it always negotiates the best speed am i wright?
N is a faster speed but some linux drivers have problems with N speed as this on does, unless your ips is giving you mre then 54 mbps then you do not need N.
> 8.8.8.8, 8.8.4.4
This is the DNS serer in my experience the numbers above are always a lot faster then the isp dns server.

Is ipv6 set to ignore in your wireless settings as well?
Can try this parameter as well.
```
sudo su
echo 'options rtl8192se disable_hw_scan:disable=0' | sudo tee /etc/modprobe.d/rtl8129se.conf

```
You can compile a new driver yourself but it is not a real easy process.
Thanks

---

### Post by noobydooby on 2013-03-30
Hi Wild man,

thanks for the answer. Yes ipv6 is set to ignore. I laso tried out the last command, although im not quite sure if it worked.  My speed is a bit faster than yesterday ,although not much. Could just  be that there are fewer people online now. 

Compiling my own driver WoW that sounds realy interesting. I dont mind a bit of complication (If you dont :) )and  would realy like to try that. But I guess that would take quite some time in order to do it whright. Unfortunatly I dont have a lot of time left this weekend. Should I start a new thread about this next week or so or just continue on  this one later on ?

EIther way, many thanks for your help so far and happy eastern :)

---

### Post by wildmanne39 on 2013-03-30
Hi, we can do it in this thread it will not take to long hopefully, I need to find the exact link you need and instructions, also when the kernel is updated you will need to recompile the driver but it is easy the second time around.
Thanks

---

### Post by noobydooby on 2013-04-07
Hello, hope it did not neglect this thread to long. I just had no time at all this week, Sorry. Before compiling a driver i should say that since I last posted I can't conect to wifi at all (when runnig ubuntu, win7 works fine). I am not sure if it is related to the changes we did in order to speed up the wifi. I am sure it's not the router congfiguration changes because I cant even see the neighbours wifi networks. I am connected with the cable now.

---

### Post by wildmanne39 on 2013-04-07
Hi, please remove the netinfo.txt file from your home folder and run the script again and post the outcome so we can see what has changed.
Thanks

---

### Post by noobydooby on 2013-04-08
hi wild man, thanks for the response. here is the new file content:

```

*************** info trace ****************



**** uname -a ****


Linux ubuntu 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Mitac Device [1071:9072]
    Kernel driver in use: forcedeth
--
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel modules: rtl8192se


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0505 Genesys Logic, Inc. 
Bus 003 Device 002: ID 24ae:2000  


**** iwconfig ****




**** rfkill ****




**** lsmod ****


Module                  Size  Used by
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              12319264  60 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtlwifi               111245  0 
mac80211              506862  1 rtlwifi
psmouse                97485  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
cfg80211              205774  2 rtlwifi,mac80211
soundcore              15091  1 snd
serio_raw              13211  0 
usbhid                 47238  0 
v4l2_compat_ioctl32    17128  1 videodev
shpchp                 37201  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hid                    99636  1 usbhid
i2c_nforce2            13058  0 
video                  19651  0 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
binfmt_misc            17540  1 
mac_hid                13253  0 
ums_realtek            18248  0 
usb_storage            49243  1 ums_realtek
forcedeth              63460  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.221
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




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




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search localdomain


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


[   30.789816] rtl8192se: Unknown parameter `disable_hw_scan:disable'
[   31.502335] type=1400 audit(1365444221.102:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=821 comm="apparmor_parser"


**************** done ********************


```

---

### Post by wildmanne39 on 2013-04-08
Please open this file:
```
gksudo gedit /etc/modprobe.d/rtl8192se.conf
```
and remove:
```
disable_hw_scan:disable=0
```
save the file in gedit close and reboot.
Thanks

---

### Post by noobydooby on 2013-04-09
Hi,

when I open the terminal and paste ```

gksudo gedit /etc/modprobe.d/rtl8192se.conf
```

the texeditor opens two tabs. one is "rtl8192se.conf" and the other is "Untitled Document 1 ". Both seem to be empty or at least i cant see anything.

---

### Post by wildmanne39 on 2013-04-12
Hi, please try ```
echo 'options rtl8192se swenc=1' | sudo tee /etc/modprobe.d/rtl8192se.conf
```
Then open that file again and see if anything is in it. Do not be concerned with the one that says untitled gedit always opens an empty file along with the one you wanted it to open.
Thanks

---

### Post by noobydooby on 2013-04-12
hello wild man,

first of all thanks for hanging in there with me. second I did as your previous post said and got this content ```
options rtl8192se swenc=1
```. However I just looked into the modprobe directory and there are 2 other files with a similar name. 
[LIST=1]
[*]rtl8129.conf 
[*]rtl81_**29**_se.con 
[/LIST]

Number 2 contains  ```
options rtl81**_92_**se disable_hw_scan:disable=0
``` I asume this is the one i was looking for ans will remove 

```
disable_hw_scan:disable=0
```
from here
Should i also change the remaining text  from ```
options rtl81**_92_**se 
```to  options ```
rtl81**_29_**se
```

thanks

---

### Post by noobydooby on 2013-04-12
just rebooted and wireless is working again. Thanks a lot for your help :D

---

### Post by wildmanne39 on 2013-04-12
That is good!!! If you know the path of the two files I would remove them completely using the sudo rm command, if not it should be okay.
Thanks

---

### Post by syniurge2 on 2013-09-07
This thread has greatly helped me to finally solve the random disconnect/poor speed issue on my Toshiba laptop, thank you Wildman!

I'm on a 3.11 kernel and the situation hasn't improved since the last time I had to use Wifi heavily 2 years ago, but after adding those options:

```
echo 'options rtl8192se swenc=1 fwlps=0 swlps=1' | sudo tee /etc/modprobe.d/rtl8192se.conf
```

and reloading Network Manager and the kernel module, the wifi is flawless, perfectly stable and reaching the same speed it has on Windows :o

I'll email the maintainer of the module to make him know, there has been dozens of people on forums and mailing lists asking for a solution (a proper one, without having to turn off power saving) without success.

---

### Post by syniurge2 on 2013-09-09
I spoke too fast, it still seems very random. Sometimes it's rock stable and fast and sometimes the old issues are back. After a few tries it works though, and to reload everything without restarting the computer you can use:

```
killall plasma-desktop ; sudo stop network-manager ; sleep 2; sudo rmmod rtl8192se ; sleep 1; sudo modprobe rtl8192se; sleep 2; sudo start network-manager ; plasma-desktop & disown
```

(plasma-desktop is KDE-specific, there should be a similar process for the NM applet on Unity and it may not even be needed to restart it)

---


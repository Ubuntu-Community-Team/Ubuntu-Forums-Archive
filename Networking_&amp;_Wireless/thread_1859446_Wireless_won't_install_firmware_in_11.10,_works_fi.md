---
title: "Wireless won't install firmware in 11.10, works fine prior"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by Dragonbite on 2011-10-13
I cleared out my Ubuntu 11.04 installation with 11.10 and as usual try to install the broadcom wireless drivers using **sudo apt-get install firmware-b43-installer** except this time it Aborts and doesn't run.

These are the stats of my system (via lspci)```
lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
01:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
01:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
01:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11a/b/g (rev 03)

```

And this is the message I get when I try to install the drivers.  I did try running the legacy ones as well and get the same results.  Usually this version is what I use and it has worked perfectly.```
 sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,272 B of archives.
After this operation, 53.2 kB of additional disk space will be used.
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 127289 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a014-9_all.deb) ...
Setting up firmware-b43-installer (1:014-9) ...
An unsupported BCM4301, BCM4303, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.

```

No surprise, jockey doesn't find any proprietary items on my system so it is no help either.

Help!!

---

### Post by Dragonbite on 2011-10-14
From the looks of it, I am not alone in this issue.

---

### Post by BalaViknesh on 2011-10-14
Same issue with me....  while booting it shows "Waiting for network configuration" ..? is that same there ???

---

### Post by Dragonbite on 2011-10-14
When I open Network Manager I get "firmware not installed" for the wireless part.

---

### Post by rchildress87 on 2011-10-14
I have the same problem on my Gateway 400VTX laptop.  Here is the output of lspci for the card:

```
02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
```

Here is what apt-get outputs when i try to install "firmware-b43-installer":

```
richardc@richardc-Gateway-400VTX:~$ sudo apt-get install firmware-b43-installer Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,272 B of archives.
After this operation, 53.2 kB of additional disk space will be used.
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 131144 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a014-9_all.deb) ...
Setting up firmware-b43-installer (1:014-9) ...
An unsupported BCM4301, BCM4303, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.
```

I had this same problem in Debian testing (wheezy) a few months ago.  I never had this problem with Ubuntu 11.04.  Looks like the bug crept its way into Ubuntu 11.10.

Here is a bug report with possible solution for Debian (I tried it in August on Debian and remember having success):
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=636077](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=636077)

Finally, here is documentation stating that the bcm4306/3 is supported by the b43 firmware:
[http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices) (refer to row 5)

---

### Post by rchildress87 on 2011-10-14
A little progress:

I installed the version of "firmware-b43-installer" that is available for Ubuntu 11.04.  You can get it from here:
[http://packages.ubuntu.com/natty/all/firmware-b43-installer/download](http://packages.ubuntu.com/natty/all/firmware-b43-installer/download)

How I installed:

[LIST=1]
[*]Opened terminal
[*]Removed the b43 and b43legacy installer packages: "sudo apt-get remove firmware-b43-installer firmware-b43legacy-installer"
[*]Changed to the directory where I saved the older, Natty version of the package (ex: "cd ~/Downloads")
[*]Installed the Natty version of firmware-b43-installer: "sudo dpkg -i firmware-b43-installer"
[/LIST]
I can now view a list of all available wireless networks, including my home wireless network.  However, I can not connect to any of them.  I even tried removing the WPA security on my wireless network.

---

### Post by wildmanne39 on 2011-10-14
Hi Dragonbite, I am not sure this will work with 11.10 like it has with 11.04 and other previous versions but let&#347; try it please:

Down load the b43 zip file then drag and drop the file to your desktop, then disconnect your wired connection. Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run the commands one at  a tim4e please.
Thank you

---

### Post by rchildress87 on 2011-10-14
wildmanne39: I can verify that this does not work on my laptop (Gateway 400VTX).  I am running xubuntu 11.10 and have the same network card (bcm4306/3) as Dragonbite.  After performing the steps you've asked, however, I see a list of available wireless networks.  Unfortunately, I still can not connect to any of them.

---

### Post by wildmanne39 on 2011-10-14
Hi, let&#347; see if we can make it connect please post the results of:
```
sudo lshw -C network
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
lsmod
```
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm|radio|switch|wlan0'
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by rchildress87 on 2011-10-14
sudo lshw -C network

```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:e0200000-e0201fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:54:de:79
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.119 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:e0202000-e0202fff ioport:3000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:26:a0:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

```nm-tool:
```

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:E0:B8:54:DE:79

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.119
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.87.68.166
    DNS:             68.87.74.166


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:0B:7D:26:A0:EB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    572:             Infra, 00:25:9C:5A:8B:CF, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2
    2WIRE676:        Infra, 00:24:56:E3:D8:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    SMITH735:        Infra, B0:E7:54:FB:96:F1, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    2WIRE065:        Infra, 3C:EA:4F:FD:17:D9, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    2WIRE406:        Infra, 3C:EA:4F:0E:2C:11, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA
    2WIRE595:        Infra, 00:22:A4:81:97:91, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA

```lspci -nnk | grep -iA2 net
```
02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge
--
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Gateway 2000 Device [107b:0402]
    Kernel driver in use: e100

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```rfkill list all
```

8: phy8: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod
```

Module                  Size  Used by
b43                   318816  0 
ssb                    50682  1 b43
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
arc4                   12473  2 
snd_intel8x0           33318  3 
snd_ac97_codec        106082  1 snd_intel8x0
pcmcia                 39822  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_rawmidi            25241  1 snd_seq_midi
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
ppdev                  12849  0 
snd                    55902  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
shpchp                 32356  0 
i915                  505108  2 
drm_kms_helper         32889  1 i915
parport_pc             32114  1 
drm                   192226  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
floppy                 60310  0

```sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:5A:8B:CF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"572"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00015c019c04d180
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 0003353732
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259C5A8BCF1021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303110420001301054000800060050F20400011011000757525435344732100800020084103C000101
          Cell 02 - Address: 00:22:A4:81:97:91
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"2WIRE595"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eaf563c181
                    Extra: Last beacon: 292ms ago
                    IE: Unknown: 00083257495245353935
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 3C:EA:4F:0E:2C:11
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"2WIRE406"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002541d091181
                    Extra: Last beacon: 1204ms ago
                    IE: Unknown: 00083257495245343036
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: B0:E7:54:FB:96:F1
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SMITH735"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb91386181
                    Extra: Last beacon: 428ms ago
                    IE: Unknown: 0008534D495448373335
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C

```dmesg | egrep 'b43|firm|radio|switch|wlan0'
```

[ 5909.341307] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5909.341413]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5909.341430]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5909.341446]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5909.341453]  [<c1001d22>] ? __switch_to+0x192/0x1a0
[ 5909.341467]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5909.341479]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5909.341490]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5909.401421] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5909.401475] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5909.401584]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5909.401602]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5909.401618]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5909.401624]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5909.401639]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5909.401651]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5909.401664]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5909.443632] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5909.443683] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5909.443783]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5909.443799]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5909.443814]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5909.443820]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5909.443833]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5909.443844]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5909.443855]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.059452] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.059505] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.059609]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.059625]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.059640]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.059646]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.059660]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.059670]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.059682]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.366644] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.366696] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.366798]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.366814]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.366829]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.366836]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.366850]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.366861]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.366872]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.464933] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.464983] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.465083]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.465100]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.465114]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.465121]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.465135]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.465146]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.465157]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.468139] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.468186] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.468277]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.468292]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.468306]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.468312]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.468326]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.468336]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.468348]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.499956] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.500050] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.500176]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.500193]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.500208]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.500214]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.500229]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.500245]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.500261]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.563243] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.563293] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.563393]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.563410]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.563424]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.563430]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.563443]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.563454]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.563465]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.566577] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.566628] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.566730]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.566745]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.566760]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.566766]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.566780]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.566790]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.566801]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.673820] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.673872] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.673974]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.673990]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.674005]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.674011]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.674024]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.674035]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.674046]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.772070] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.772123] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.772247]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.772264]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.772280]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.772287]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.772302]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.772318]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.772334]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.870434] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.870484] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.870591]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.870608]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.870624]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.870630]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.870645]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.870657]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.870670]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.873665] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.873717] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.873823]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.873841]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.873856]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.873863]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.873878]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.873889]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.873902]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5928.981032] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5928.981084] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5928.981187]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5928.981204]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5928.981219]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5928.981225]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5928.981240]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5928.981251]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5928.981262]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.177622] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.177674] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.177783]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.177801]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.177817]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.177824]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.177838]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.177852]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.177865]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.180848] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.180902] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.181031]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.181051]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.181067]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.181073]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.181089]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.181108]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.181127]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.288120] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.288172] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.288283]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.288304]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.288319]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.288326]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.288341]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.288356]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.288372]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.292556] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.292609] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.292706]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.292722]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.292736]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.292742]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.292756]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.292767]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.292778]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.309049] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.309101] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.309200]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.309217]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.309231]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.309237]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.309251]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.309262]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.309273]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.386514] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.386565] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.386669]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.386686]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.386702]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.386708]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.386722]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.386734]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.386747]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.394987] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.395038] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.395138]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.395155]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.395169]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.395175]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.395189]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.395200]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.395211]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.411435] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.411486] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.411588]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.411604]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.411619]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.411626]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.411640]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.411651]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.411663]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.496292] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.496344] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.496450]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.496468]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.496483]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.496498]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.496510]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.496538]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.513840] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.513892] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.513992]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.514008]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.514022]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.514028]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.514042]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.514052]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.514063]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.573837] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.573887] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.573987]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.574003]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.574018]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.574024]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.574037]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.574048]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.574059]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.595413] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.595463] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.595567]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.595584]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.595599]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.595605]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.595619]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.595632]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.595644]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.616250] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.616300] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.616401]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.616418]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.616432]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.616438]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.616451]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.616462]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.616473]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.821045] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.821096] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.821215]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.821234]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.821249]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.821255]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.821271]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.821286]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.821302]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 5929.881018] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 5929.881068] Pid: 8492, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 5929.881167]  [<f8719892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 5929.881184]  [<f87335d3>] b43_rx+0x343/0x470 [b43]
[ 5929.881198]  [<f873794d>] dma_rx+0x19d/0x2a0 [b43]
[ 5929.881205]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 5929.881218]  [<f8738ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 5929.881229]  [<f871c65d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 5929.881240]  [<f871c81d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6015.910784] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
[ 6131.736127] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[ 6131.771364] b43-phy5: Broadcom 4306 WLAN found (core revision 5)
[ 6131.819885] Registered led device: b43-phy5::tx
[ 6131.819932] Registered led device: b43-phy5::rx
[ 6131.819978] Registered led device: b43-phy5::radio
[ 6137.440107] b43-phy5: Loading firmware version 644.1001 (2011-01-10 21:12:08)
[ 6137.500752] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6137.589288] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6137.589342] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6137.589481]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6137.589497]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6137.589511]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6137.589517]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6137.589531]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6137.589542]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6137.589553]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6137.623336] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6137.623391] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6137.623500]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6137.623518]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6137.623534]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6137.623541]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6137.623557]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6137.623568]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6137.623581]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6137.896460] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6137.896513] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6137.896617]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6137.896634]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6137.896650]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6137.896657]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6137.896672]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6137.896684]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6137.896695]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6137.994785] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6137.994839] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6137.994949]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6137.994966]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6137.994983]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6137.994990]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6137.995005]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6137.995017]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6137.995030]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.093085] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.093138] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.093263]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.093281]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.093298]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.093305]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.093322]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.093341]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.093355]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.097343] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.097397] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.097503]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.097520]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.097539]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.097545]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.097561]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.097579]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.097598]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.301982] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.302037] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.302146]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.302163]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.302179]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.302186]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.302204]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.302225]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.302246]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.372568] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.372621] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.372729]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.372748]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.372763]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.372770]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.372784]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.372795]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.372807]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.400252] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.400305] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.400411]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.400428]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.400444]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.400451]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.400469]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.400490]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.400511]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.502898] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.502951] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.503060]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.503076]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.503092]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.503100]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.503115]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.503127]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.503139]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.707465] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.707519] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.707625]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.707642]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.707658]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.707665]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.707679]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.707691]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.707702]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.818048] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.818103] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.818218]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.818237]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.818252]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.818259]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.818273]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.818284]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.818295]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.841696] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.841750] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.841861]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.841879]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.841895]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.841903]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.841921]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.841941]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.841962]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.916341] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.916395] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.916501]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.916519]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.916535]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.916543]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.916560]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.916581]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.916602]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6138.926151] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6138.926204] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6138.926314]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6138.926331]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6138.926347]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6138.926354]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6138.926369]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6138.926381]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6138.926394]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.046488] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.046569] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.046673]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.046689]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.046704]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.046711]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6139.046724]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.046735]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.046746]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.125231] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.125284] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.125393]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.125410]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.125426]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.125433]  [<c1001d22>] ? __switch_to+0x192/0x1a0
[ 6139.125449]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.125460]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.125473]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.206738] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.206793] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.206900]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.206922]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.206938]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.206946]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6139.206962]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.206980]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.206999]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.251289] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.251343] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.251453]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.251470]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.251486]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.251493]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6139.251508]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.251520]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.251533]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.309127] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.309181] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.309287]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.309304]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.309318]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.309325]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6139.309339]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.309349]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.309360]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.353685] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.353740] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.353866]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.353884]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.353901]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.353908]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6139.353924]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.353940]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.353956]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6139.411540] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6139.411596] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6139.411745]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6139.411762]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6139.411776]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6139.411783]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6139.411796]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6139.411807]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6139.411818]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6146.506567] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6146.506619] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6146.506721]  [<f87e4892>] ? b43_tsf_read+0x32/0x50 [b43]
[ 6146.506737]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6146.506751]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6146.506758]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6146.506771]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6146.506782]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6146.506793]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6146.531439] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6146.531491] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6146.531610]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6146.531626]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6146.531631]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6146.531646]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6146.531657]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6146.531669]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6147.317822] Modules linked in: b43 ssb rfcomm bnep bluetooth arc4 snd_intel8x0 snd_ac97_codec pcmcia ac97_bus snd_pcm snd_seq_midi yenta_socket pcmcia_rsrc snd_rawmidi pcmcia_core snd_seq_midi_event mac80211 cfg80211 snd_seq snd_timer snd_seq_device joydev ppdev snd psmouse soundcore snd_page_alloc serio_raw shpchp i915 drm_kms_helper parport_pc drm i2c_algo_bit video lp parport e100 floppy [last unloaded: ssb]
[ 6147.317874] Pid: 8662, comm: irq/11-b43 Tainted: G        W   3.0.0-12-generic #20-Ubuntu
[ 6147.317991]  [<f87fe5d3>] b43_rx+0x343/0x470 [b43]
[ 6147.318006]  [<f880294d>] dma_rx+0x19d/0x2a0 [b43]
[ 6147.318012]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 6147.318026]  [<f8803ab2>] b43_dma_rx+0x32/0x60 [b43]
[ 6147.318036]  [<f87e765d>] b43_do_interrupt_thread+0x13d/0x2e0 [b43]
[ 6147.318047]  [<f87e781d>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[ 6447.966031] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
[ 6492.910716] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[ 6492.944938] b43-phy6: Broadcom 4306 WLAN found (core revision 5)
[ 6492.995039] Registered led device: b43-phy6::tx
[ 6492.995089] Registered led device: b43-phy6::rx
[ 6492.995135] Registered led device: b43-phy6::radio
[ 6502.568145] b43-phy6: Loading firmware version 508.154 (2009-08-18 00:58:22)
[ 6502.640738] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7018.466156] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
[ 7050.232186] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[ 7050.263964] b43-phy7: Broadcom 4306 WLAN found (core revision 5)
[ 7050.315340] Registered led device: b43-phy7::tx
[ 7050.315385] Registered led device: b43-phy7::rx
[ 7050.315432] Registered led device: b43-phy7::radio
[ 7058.814684] b43-phy7 ERROR: Firmware file "b43/ucode5.fw" not found
[ 7058.814692] b43-phy7 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 7058.814699] b43-phy7 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 7172.232409] b43-pci-bridge 0000:02:04.0: PCI INT A disabled
[ 7181.053625] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[ 7181.077534] b43-phy8: Broadcom 4306 WLAN found (core revision 5)
[ 7181.127364] Registered led device: b43-phy8::tx
[ 7181.127414] Registered led device: b43-phy8::rx
[ 7181.127457] Registered led device: b43-phy8::radio
[ 7187.404190] b43-phy8: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7187.461423] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by rchildress87 on 2011-10-14
To clean up the output of dmesg, i rebooted my computer and tried to connect to my home network once.  i then immediately ran the command dmesg | egrep 'b43|firm|radio|switch|wlan0' and got this:

```

[    0.000000] APIC: switched to apic NOOP
[    0.008959] SMP alternatives: switching to UP code
[    1.785123] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[   23.458462] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   23.551803] Registered led device: b43-phy0::tx
[   23.551935] Registered led device: b43-phy0::rx
[   23.552539] Registered led device: b43-phy0::radio
[   25.992056] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.068493] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.233381] Console: switching to colour frame buffer device 128x48

```line 4 draws my attention.  to my understanding, im using the broadcom 4306 WLAN card revision 3 and not revision 5 as is mentioned.

another question i have:
why am i testing with firmware version 410.2160?  there are multiple newer versions that have been released since according to [http://linuxwireless.org/en/users/Drivers/b43#List_of_firmware](http://linuxwireless.org/en/users/Drivers/b43#List_of_firmware)

---

### Post by westie457 on 2011-10-14
Hello try the attached file, it is slightly different to the one posted by wildmanne39.

Instructions on how to install are in this thread _[here]("http://ubuntuforums.org/showthread.php?t=1851701&page=11")_.

Even though the thread is for a different chip the drivers are the same.

Hope this helps.

---

### Post by rchildress87 on 2011-10-14
Unfortunately, that made no difference.  here is the dmesg output with the firmware that westie457 posted:

```

[    0.000000] APIC: switched to apic NOOP
[    0.004953] SMP alternatives: switching to UP code
[    1.716614] b43-pci-bridge 0000:02:04.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[   23.191853] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   23.286664] Registered led device: b43-phy0::tx
[   23.286787] Registered led device: b43-phy0::rx
[   23.286903] Registered led device: b43-phy0::radio
[   25.824144] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   25.902088] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.079510] Console: switching to colour frame buffer device 128x48

```

---

### Post by Dragonbite on 2011-10-14
> **wildmanne39 said:**
> Hi Dragonbite, I am not sure this will work with 11.10 like it has with 11.04 and other previous versions but let&#347; try it please:

Down load the b43 zip file then drag and drop the file to your desktop, then disconnect your wired connection. Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run the commands one at  a tim4e please.
Thank you

You, sir, are a genius!! It worked beautifully!!

Thanks!

---

### Post by wildmanne39 on 2011-10-14
Hi, I am glad to hear it Dragonbite, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by wildmanne39 on 2011-10-14
Hi rchildress87, make sure the commands you posted the information from are still showing the same information, because yours is trying to connect and we might can still make it.

Did you uninstall the b43 that you installed from me before you installed the one westie457 gave you? 
Thank you

---

### Post by rchildress87 on 2011-10-14
Yes, I removed your drivers and switched them for westie's after I posted the output you asked for.  After trying westie's firmware (to no avail), I dug into 11.10's "firmware-b43-installer" and figured out which version it wants to install before it improperly detects my wireless card revision.  After downloading the new firmware, removing westie's, and installing the new firmware (v 5.10.56.27.3), I still can not connect.

Any more suggestions?

---

### Post by wildmanne39 on 2011-10-14
Hi, I will need you to post all the information again since you have tried other things that way I know where we are at.
Thank you

---

### Post by rchildress87 on 2011-10-14
sudo lshw -C network
```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:e0200000-e0201fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:54:de:79
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.119 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:e0202000-e0202fff ioport:3000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:26:a0:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg

```

nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:0B:7D:26:A0:EB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SMITH735:        Infra, B0:E7:54:FB:96:F1, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    2WIRE406:        Infra, 3C:EA:4F:0E:2C:11, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    2WIRE676:        Infra, 00:24:56:E3:D8:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    2WIRE065:        Infra, 3C:EA:4F:FD:17:D9, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    572:             Infra, 00:25:9C:5A:8B:CF, Freq 2422 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    2WIRE595:        Infra, 00:22:A4:81:97:91, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:E0:B8:54:DE:79

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.119
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             xx.xx.xx.166
    DNS:             xx.xx.xx.166

```

lspci -nnk | grep -iA2 net
```

02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge
--
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Gateway 2000 Device [107b:0402]
    Kernel driver in use: e100

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

lsmod
```

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
b43                   318816  0 
snd_intel8x0           33318  3 
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
pcmcia                 39822  0 
snd_ac97_codec        106082  1 snd_intel8x0
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
ppdev                  12849  0 
snd                    55902  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
i915                  505108  2 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm_kms_helper         32889  1 i915
psmouse                73673  0 
serio_raw              12990  0 
drm                   192226  3 i915,drm_kms_helper
parport_pc             32114  1 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e100                   36289  0 
ssb                    50682  1 b43
floppy                 60310  0 

```

sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:5A:8B:CF
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"572"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00015c02c4cf0180
                    Extra: Last beacon: 652ms ago
                    IE: Unknown: 0003353732
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259C5A8BCF1021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303110420001301054000800060050F20400011011000757525435344732100800020084103C000101
          Cell 02 - Address: 00:22:A4:81:97:91
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"2WIRE595"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eefb042181
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 00083257495245353935
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 03 - Address: 3C:EA:4F:FD:17:D9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"2WIRE065"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009cf581a290
                    Extra: Last beacon: 540ms ago
                    IE: Unknown: 00083257495245303635
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010002
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: 3C:EA:4F:0E:2C:11
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2WIRE406"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000025822ac9181
                    Extra: Last beacon: 1184ms ago
                    IE: Unknown: 00083257495245343036
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 05 - Address: B0:E7:54:FB:96:F1
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"SMITH735"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf96dbe181
                    Extra: Last beacon: 568ms ago
                    IE: Unknown: 0008534D495448373335
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C

```

dmesg | egrep 'b43|firm|radio|switch|wlan0'
 	```

[ 8957.908174] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[ 8957.973315] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

the piped dmesg is different this time and doesnt seem like an improvement. would you like me to switch back to your copy of the firmware?

---

### Post by wildmanne39 on 2011-10-14
Hi, is the all the error messages that showed up this time?

Which network are you trying to connect too?
Thank you

---

### Post by rchildress87 on 2011-10-14
this is all the output that i was given.  i am trying to connect to "572"  which is accessible by both my phone, ps3, and windows laptop.  this laptop is about a foot away from the router. 

keep in mind that the firmware version has changed from the one you supplied me.  i am using the one that is fetched by the "firmware-b43-installer" package in 11.10 repositories.

---

### Post by portPirate on 2011-10-14
> **wildmanne39 said:**
> Hi Dragonbite, I am not sure this will work with 11.10 like it has with 11.04 and other previous versions but let&#347; try it please:

Down load the b43 zip file then drag and drop the file to your desktop, then disconnect your wired connection. Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Run the commands one at  a tim4e please.
Thank you

This worked brilliantly for me, thanks.

---

### Post by wildmanne39 on 2011-10-14
Hi, yes I know you are using the new firmware, it looks like it should connect but I have seen it before where is refused.

I would see if you can change your encryption in your router to just wpa2 and not wpa/wpa2.

I think you need to set your router speed to b,g and see if that helps.

---

### Post by wildmanne39 on 2011-10-14
Hi portPirate, your welcome! I am glad it worked.

Would you please do me a favor and post the information from the commands I gave on the previous page so we can see what is working in 11.10 and what is not.
Thank you

---

### Post by nm_geo on 2011-10-14
Hi wildmanne and rchildress87

Here is some interesting stuff.. from b43 linux google search.

14e4:4324 
   yes (b43legacy) 
   BCM4306 
   

 
as I remember rchildress87 has the 14e4:4324

I have not read back through all this thread and I probably won't LOL..

Question is have you guys tried the legacy firmware ??

firmware-b43legacy-installer

---

### Post by wildmanne39 on 2011-10-14
Hi, yes it is part of the b43zip file I gave him but he did not have it installed very long, by the time I got back it was gone, but it had a lot of errors but I have not research them since he uninstalled it.

You are more then welcome to help out here I would enjoy working with you again.
Thank you

---

### Post by spidymac on 2011-10-15
Having an issue with the wired network connection, shows connection established then, disconnected-you are now offline. This has been happening a lot since the upgrade to 11.10, is any one having these connection issues? 
Wired connection works fine on second laptop running kubuntu.  Please advise.

---

### Post by wildmanne39 on 2011-10-15
Hi spidymac, you should start your own thread since your issue is completely different from the original poster, and you will get more help that way.
Thank you

---

### Post by peepingtom on 2011-10-15
> **spidymac said:**
> Having an issue with the wired network connection, shows connection established then, disconnected-you are now offline. This has been happening a lot since the upgrade to 11.10, is any one having these connection issues? 
Wired connection works fine on second laptop running kubuntu.  Please advise.
 Please start a new thread, and post the output of running "lspci" without quotation marks in terminal.

---

### Post by dhodgson on 2011-10-15
I had the same problem, trying everything but to no avail. I have wiped my computer and gone back to 11.04 and will stay with this distribution until these bugs are fixed. I do not know why they put these new versions out when they obviously don't work, which to my mind would frustrate any new Linux user and possibly cause them to go back to windows. I mean I am no dummy I have been using Linux for the past 5 years and this one has stumped me.

---

### Post by spidymac on 2011-10-15
:D Thanks will do!
> **wildmanne39 said:**
> Hi spidymac, you should start your own thread since your issue is completely different from the original poster, and you will get more help that way.
Thank you

---

### Post by adbs98 on 2011-10-19
Thanks so much. That worked great and took care of me. You Rock!!

---

### Post by wildmanne39 on 2011-10-19
Hi, your welcome! just using what the master chili has taught, I am still learning networking myself.

---

### Post by justpaul on 2011-10-22
Worked perfectly on my Dell 610. Thanks, wildmanne39.

> **wildmanne39 said:**
> Hi Dragonbite, I am not sure this will work with 11.10 like it has with 11.04 and other previous versions but let&#347; try it please:

Down load the b43 zip file then drag and drop the file to your desktop, then disconnect your wired connection. Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run the commands one at  a tim4e please.
Thank you

---

### Post by joeyham on 2011-10-22
I am having the same problem with Dell D600.  The network card is 
joey@joey-Latitude-D600:~/bcm4306/b43$ lspci -vvnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)

additional info on drivers

joey@joey-Latitude-D600:~$ dmesg | egrep 'b43|firm|radio|switch|wlan0'
[    0.000000] APIC: switched to apic NOOP
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=cb469e03-2431-4267-b9f0-0760b430cf23 ro quiet splash vt.handoff=7
[    0.008648] SMP alternatives: switching to UP code
[    1.431114] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   20.020482] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.172857] Registered led device: b43-phy0::tx
[   20.172910] Registered led device: b43-phy0::rx
[   20.172962] Registered led device: b43-phy0::radio
[   20.988834] Console: switching to colour frame buffer device 128x48
[   21.207331] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   21.207337] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   21.207341] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1119.624163] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1119.624176] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 1119.624187] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1151.800806] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1151.800819] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 1151.800830] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1316.552380] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1316.552394] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 1316.552405] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5067.881614] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[ 5078.033991] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 5078.064247] b43-phy1: Broadcom 4306 WLAN found (core revision 5)
[ 5078.120827] Registered led device: b43-phy1::tx
[ 5078.120980] Registered led device: b43-phy1::rx
[ 5078.121131] Registered led device: b43-phy1::radio
[ 5078.276418] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5078.276432] b43-phy1 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5078.276443] b43-phy1 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5110.118607] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[ 5117.534186] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 5117.573062] b43-phy2: Broadcom 4306 WLAN found (core revision 5)
[ 5117.628479] Registered led device: b43-phy2::tx
[ 5117.628633] Registered led device: b43-phy2::rx
[ 5117.628787] Registered led device: b43-phy2::radio
[ 5117.805493] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5117.805506] b43-phy2 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5117.805517] b43-phy2 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5532.054870] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[ 5538.642283] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 5538.669184] b43-phy3: Broadcom 4306 WLAN found (core revision 5)
[ 5538.726767] Registered led device: b43-phy3::tx
[ 5538.726843] Registered led device: b43-phy3::rx
[ 5538.726912] Registered led device: b43-phy3::radio
[ 5538.847428] b43-phy3 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5538.847442] b43-phy3 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5538.847453] b43-phy3 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5570.067248] b43-phy3 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5570.067261] b43-phy3 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5570.067272] b43-phy3 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

so far I do not have working wireless.

---

### Post by wildmanne39 on 2011-10-22
Hi, the solution in post 7 should fix your problem.
Thank you

---

### Post by joeyham on 2011-10-23
Thanks, my issue is now resolved.

---

### Post by ernestj on 2011-10-23
Hello,
I have been trying to solve this same problem since I installed back on the 13th. I followed the instructions from post #7, but it did not work for me. If fact, command 3 and 4, said something like no such directory..
help

---

### Post by guigouz on 2011-11-04
Solution in post #7 also worked for me with a BCM4312 (rev 01).

But it seems like I have to run again the command "sudo modprobe b43" after a reboot (then it works instantly). 
Did I miss something ?

Thanks for your help btw :)

[I]Edit :

I add the command to my /etc/rc.local file and it seems to works \o/[/I]

---

### Post by wildmanne39 on 2011-11-04
Hi guigouz,is suppose to work on boot but when it does not this is the way we get it to load.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thank you

---

### Post by bigtel on 2011-11-16
Thank you for this thread as I have bee having real trouble connecting my Broadcom 4306 - but now as if by magic it is done - I could not even tell you how I did it...!


Just to add - since rebooting my connection has been lost again and the very existence of a wireless card has gone. But if I use the command 'sudo modprobe b43' in the Terminal is come back and connects - why is this? and will I have to do this every time?

---

### Post by wildmanne39 on 2011-11-16
Hi bigtel, run the command in post 40 then it will work at boot.
Thank you

---

### Post by bigtel on 2011-11-17
...I am not sure what you mean by post 40..? Can you explain that please? Thanks

---

### Post by westie457 on 2011-11-17
> **bigtel said:**
> ...I am not sure what you mean by post 40..? Can you explain that please? Thanks

Hi what wildmanne39 is suggesting is that you look at post number 40 of this thread. The answer is there.

---

### Post by bigtel on 2011-11-17
..OK..sorry It's early..!!

Thanks

---

### Post by bigtel on 2011-11-17
Thanks for your help here - It now works on boot up - Great.

---

### Post by wildmanne39 on 2011-11-17
Hi bigtel, your welcome! Glad to help.

Thank you westie457 for pointing him in the right direction.

---

### Post by scgeek on 2012-03-07
Wildmanne339 your post worked for me on a Dell D610.  Thank you!!

---

### Post by wildmanne39 on 2012-03-09
Hi, your welcome!

---

### Post by Go1denFlame on 2012-05-10
THANK YOU!!!! I signed up just to say that.... this helped me on Ubuntu 12.04

---

### Post by abendayan on 2012-06-22
I was able to resolve this problem by downloading the b43.zip file listed below and following the installation instructions.  After doing that I was able to detect my wireless network but I was not able to connect to it as others had also experienced.  After doing a little bit of testing I figured out that it failed to work because I was using WEP instead of WPA for authentication.  I changed my network to WPA and I was able to connect.  Not sure why WEP does not work but keep this in mind if you can see the network but are not able to connect to it.

---

### Post by wildmanne39 on 2012-06-22
Hi, also wpa2 usually works even better then wpa or wpa/wpa2 and is much more secure then wep.
Thanks

---

### Post by Tsillah on 2012-08-11
Many thanks mate...this also finally worked with mine!!!

---

### Post by toftscot on 2012-08-28
worked as in 7 many thanks all- dell1501 goes on and on

---


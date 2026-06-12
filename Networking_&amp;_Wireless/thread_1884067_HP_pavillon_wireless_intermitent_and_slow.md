---
title: "HP pavillon wireless intermitent and slow"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by yoramdavid on 2011-11-20
Hello.
I my wireless has worked well on previous versions of Ubuntu.
I now have Ubuntu 11.10, classic gnome desktop.
**The problem:** Wireless slow, dropping very often, and the led indicator is flashing all the time, it is supposed to be still blue when connected.

I hope someone can help, thank you.

Yoram


[U][B]
Wireless related information:[/B][/U]


**1 ) Machine Brand and Model (PC/Laptop):**
```
HP Pavillon Entertainment PC dv6000
```
[B]
2 ) Wireless Brand, Model and Wireless Chipset:[/B]
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]
Bus 003 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse

```

```
$ lspci -nn | grep 'Intel Corporation PRO/Wireless'
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

**3 ) check interface:**
```
$ ifconfig: comando não encontrado
$ sudo ifconfig
eth0      Link encap:Ethernet  Endereço de HW 00:1b:24:02:f2:b0  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:18 Memória:da000000-da020000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:1635 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1635 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:536873 (536.8 KB) TX bytes:536873 (536.8 KB)

wlan0     Link encap:Ethernet  Endereço de HW 00:19:d2:0b:f2:8d  
          inet end.: 192.168.65.106  Bcast:192.168.65.255  Masc:255.255.255.0
          endereço inet6: fe80::219:d2ff:fe0b:f28d/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:106843 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:58957 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:49634418 (49.6 MB) TX bytes:7180220 (7.1 MB)

```

```
$ iwconfig: comando não encontrado
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Galley Netgear"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:3F:47:16:BE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2103   Missed beacon:0

```

```
$ iwconfig: comando não encontrado
$ sudo iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"Galley Netgear"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:3F:47:16:BE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2104   Missed beacon:0

```

**4 ) Check for modules:**
```
$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
nfsd                  322390  11 
lockd                  86161  1 nfsd
nfs_acl                12883  1 nfsd
auth_rpcgss            53320  1 nfsd
sunrpc                240950  17 nfsd,lockd,nfs_acl,auth_rpcgss
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_conexant    62197  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
nvidia              11713772  33 
hp_wmi                 18092  0 
snd_rawmidi            30547  1 snd_seq_midi
sparse_keymap          13890  1 hp_wmi
usbhid                 47198  0 
hid                    95463  1 usbhid
r852                   18277  0 
sm_common              16865  1 r852
nand                   54966  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
btusb                  18600  0 
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
psmouse                73882  0 
serio_raw              13166  0 
bluetooth             166112  11 bnep,rfcomm,btusb
mtd                    33181  2 sm_common,nand
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
snd                    68266  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 hp_wmi
iwl3945                83391  0 
iwl_legacy             83487  1 iwl3945
mac80211              310872  2 iwl3945,iwl_legacy
cfg80211              199587  3 iwl3945,iwl_legacy,mac80211
soundcore              12680  1 snd
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
e1000e                160535  0
```

([COLOR="Red"]hint[/COLOR]) search for the Wireless module:
Could not fine that info ?

**5 ) Kernel boot messages**
Test is too long and does not even fit in konsole, I selected what I thought is relevant?
```
 54.702350] wlan0: authenticate with 00:22:3f:47:16:be (try 1)
[   54.704230] wlan0: authenticated
[   54.704440] wlan0: associate with 00:22:3f:47:16:be (try 1)
[   54.707042] wlan0: RX AssocResp from 00:22:3f:47:16:be (capab=0x431 status=0 aid=2)
[   54.707049] wlan0: associated

```
[B]
6 ) Network configuration[/B]
```
$ sudo lshw -C network
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:0b:f2:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 ip=192.168.65.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:d8000000-d8000fff
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:1b:24:02:f2:b0
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:da000000-da01ffff ioport:4000(size=32)

```

**7 ) Scan for networks:**
```
$ iwlist: comando não encontrado
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:47:16:BE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"Galley Netgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000121d545b72
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000E47616C6C6579204E657467656172
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD2D000CB401280102000100223F4716BE001910000014000000223F4716BE00000000000000000000000000000000
          Cell 02 - Address: 14:D6:4D:FE:97:5B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Wireless Access 1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000090f57f887
                    Extra: Last beacon: 4244ms ago
                    IE: Unknown: 0011576972656C657373204163636573732031
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180202F0000000
          Cell 03 - Address: 00:13:10:CD:F0:48
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"LabVan Linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010a3b14188
                    Extra: Last beacon: 4796ms ago
                    IE: Unknown: 000E4C616256616E204C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020013
```

```
sudo iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
```

**8 ) Ubuntu Version:**
```
lsb_release -d
Description:	Ubuntu 11.10

```

**9 ) Kernel/architecture (including 32 vs. 64 bit):**
```
$ uname -mr
3.0.0-12-generic x86_64
```

**10 ) Restarting the network:**
```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  
```

---


---
title: "Essid hidden and unaccessible only for ubuntu"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by Thibaud74 on 2012-07-02
Hi,

After an upgrade, the wifi applet shows no more my essid. Another PC at home (win32) connects to the Internet normally. With Ubuntu, I can see essid of some neighbors, but not the mine (freebox).
After trying to "add an invisible network" without success, I thought about a channel problem. So I configured the Internet Box and chose the first channel instead of the eleventh (Ubuntu used the U.S. standard, that accesses only to channels 1 to 10, while the European standard channel is 11 or 12). I also modified the file /etc/modprobe.d/options as follows:
```

options cfg80211 ieee80211_regdom=EU

```
...and reboot but it doesn't work.
Thanks you !

Best regards,
Thibaud.

Here some logs:

cat /etc/lsb-release```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

```lsusb```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 005 Device 002: ID 13d3:3315 IMC Networks Bluetooth module

```lspci ```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```lspci -nn | grep -i net ```

01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```sudo lshw -C network ```

  *-network
       description: Interface réseau sans fil
       produit: BCM4313 802.11b/g/n Wireless LAN Controller
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:02:00.0
       nom logique: eth1
       version: 01
       numéro de série: 48:5d:60:b5:a2:1a
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       ressources: irq:17 mémoire:fbffc000-fbffffff
  *-network
       description: Ethernet interface
       produit: AR8132 Fast Ethernet
       fabriquant: Atheros Communications Inc.
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       nom logique: eth0
       version: c0
       numéro de série: bc:ae:c5:d0:7c:88
       taille: 100Mbit/s
       capacité: 100Mbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       ressources: irq:46 mémoire:f7fc0000-f7ffffff portE/S:ec00(taille=128)

```lsmod ```

Module                  Size  Used by
hid_magicmouse         17938  0 
hidp                   22628  1 
hid                    99559  2 hid_magicmouse,hidp
xt_multiport           12597  1 
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  3 xt_multiport,iptable_filter,ip_tables
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               23125  0 
joydev                 17693  0 
autofs4                37024  2 
parport_pc             32866  0 
rfcomm                 47604  12 
bnep                   18281  2 
ppdev                  17113  0 
nfsd                  277809  13 
binfmt_misc            17540  1 
nfs                   356315  0 
lockd                  86161  2 nfsd,nfs
fscache                61529  1 nfs
auth_rpcgss            53380  2 nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
sunrpc                245464  19 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
asus_wmi               24456  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
btusb                  18288  5 
bluetooth             180104  30 hidp,rfcomm,bnep,btusb
snd_hda_codec_realtek   223867  1 
lib80211_crypt_tkip    17390  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_intel,snd_hda_codec
wl                   2568210  0 
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
lib80211               14381  2 lib80211_crypt_tkip,wl
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeepc_laptop           20200  0 
sparse_keymap          13890  2 asus_wmi,eeepc_laptop
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
coretemp               13525  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  468737  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
atl1c                  41717  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
wmi                    19256  1 asus_wmi

```iwconfig```

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```ifconfig ```

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:d0:7c:88  
          inet adr:192.168.0.12  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::beae:c5ff:fed0:7c88/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:6748 erreurs:0 :0 overruns:0 frame:0
          TX packets:6801 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 lg file transmission:1000 
          Octets reçus:6529557 (6.5 MB) Octets transmis:1496376 (1.4 MB)
          Interruption:46 

eth1      Link encap:Ethernet  HWaddr 48:5d:60:b5:a2:1a  
          adr inet6: fe80::4a5d:60ff:feb5:a21a/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17 Adresse de base:0xc000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:682 erreurs:0 :0 overruns:0 frame:0
          TX packets:682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:80319 (80.3 KB) Octets transmis:80319 (80.3 KB)


```sudo iwlist scan```

eth1      Scan completed :
          Cell 01 - Address: 00:1D:6A:69:2B:37
                    ESSID:"Livebox-9f4c"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-95 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD880050F204104A000110104400010210570001001041000100103B00010310470010002348BB9F4C002348BB9F4C48BB9F4C10210005536167656D102300084C697665626F7832102400084C697665626F78321042000A4C4B30393330374450331054000800060050F20400011011000D4C697665626F78322D39463443100800020086103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 5C:33:8E:EE:E6:FA
                    ESSID:"Livebox-7ad0"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/5  Signal level:-91 dBm  Noise level:-95 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD880050F204104A000110104400010210570001001041000100103B00010310470010988B5D1E7AD0988B5D1E7AD05D1E7AD010210005536167656D102300084C697665626F7832102400084C697665626F78321042000A4C4B31313032324450341054000800060050F20400011011000D4C697665626F78322D37414430100800020086103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


```uname -r -m```

3.2.0-26-generic x86_64

```cat  /etc/network/interfaces ```

auto lo
iface lo inet loopback



```nm-tool ```


NetworkManager Tool

State: connected (global)

- Device: eth0  [DHCP eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        BC:AE:C5:D0:7C:88

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             212.27.40.240
    DNS:             212.27.40.241


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        48:5D:60:B5:A2:1A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Livebox-9f4c:    Infra, 00:1D:6A:69:2B:37, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    hpsetup:         Ad-Hoc, 3A:23:7D:B2:E0:35, Freq 2437 MHz, Rate 0 Mb/s, Strength 32
    Livebox-7ad0:    Infra, 5C:33:8E:EE:E6:FA, Freq 2437 MHz, Rate 0 Mb/s, Strength 15 WPA WPA2
    FreeWifi:        Infra, F4:CA:E5:D4:64:C5, Freq 2462 MHz, Rate 54 Mb/s, Strength 22



```

---


---
title: "8187L chipset on 9.10 recognized but not activated"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by geobart on 2009-11-03
Hi,
i've installed my new usb dongle with realtek 8187L chipset with Ubuntu 9.10, and it seems that the dongle is ready to work (green led) but the network is disabled ? and the network manager says device not ready !!

what is the problem ?

i'm testing it on a live CD

here are the different codes :
ubuntu@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1687:0165 Kingmax Digital Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
15:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
15:00.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

ubuntu@ubuntu:~$ lspci -nn | grep -i net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 21)

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d3:3a:eb:ed
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5751m-v3.56 ip=172.25.93.28 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:ee000000-ee00ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:59:08:01:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
arc4                    1660  2 
ecb                     2524  2 
rtl8187                50624  0 
mac80211              181236  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
binfmt_misc             8356  1 
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_hda_codec_analog    59292  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
joydev                 10272  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
iptable_filter          3100  0 
snd_rawmidi            22208  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
pcmcia                 36808  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dm_crypt               12928  0 
yenta_socket           24200  1 
thinkpad_acpi          67108  0 
rsrc_nonstatic         11644  1 yenta_socket
psmouse                56180  0 
led_class               4096  2 rtl8187,thinkpad_acpi
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               5280  0 
nvram                   7528  1 thinkpad_acpi
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
squashfs               22912  1 
aufs                  149420  1 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52544  2 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
tg3                   109600  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
ramzswap                8880  1 
xvmalloc                5180  1 ramzswap
lzo_decompress          2620  1 ramzswap
lzo_compress            2300  1 ramzswap

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:3a:eb:ed  
          inet adr:172.25.93.28  Bcast:172.25.255.255  Masque:255.255.0.0
          adr inet6: fe80::216:d3ff:fe3a:ebed/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:13021 erreurs:0 :0 overruns:0 frame:0
          TX packets:2112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3786280 (3.7 MB) Octets transmis:253437 (253.4 KB)
          Interruption:16 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


ubuntu@ubuntu:~$ uname -r -m 
2.6.31-14-generic i686


ubuntu@ubuntu:~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback


ubuntu@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:16:D3:3A:EB:ED

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.25.93.28
    Prefix:          16 (255.255.0.0)
    Gateway:         172.25.100.1

    DNS:             194.2.0.20
    DNS:             194.98.65.65


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             unavailable
  Default:           no
  HW Address:        00:24:59:08:01:AA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points


Thx ):P

---

### Post by geobart on 2009-11-04
help please, no idea ?
 
thx

---


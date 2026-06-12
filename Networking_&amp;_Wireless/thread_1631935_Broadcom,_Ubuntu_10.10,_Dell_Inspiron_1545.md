---
title: "Broadcom, Ubuntu 10.10, Dell Inspiron 1545"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by Podas okys on 2010-11-27
After upgrading from Ubuntu 10.04 to 10.10, my wireless disappeared, and most lately even my wired connection ceased to work. 
Details about my Wireless are as follows: 

1) Machine Brand and Model (PC(Laptop):
Dell Inspiron 1545

2) Wireless Brand, Model and Wireless Chipset:
saklovitij@Saklovitij-Inspiron-1545:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

saklovitij@Saklovitij-Inspiron-1545:~$ lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. 

Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. 

Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. 

Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 004: ID 0c45:63ee Microdia 

Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

saklovitij@Saklovitij-Inspiron-1545:~$ 

(hint) {use grep to get only information about the Wireless}
saklovitij@Saklovitij-Inspiron-1545:~$ lspci -nn | grep 'Wireless Brand'

saklovitij@Saklovitij-Inspiron-1545:~$ 

3) check interface:
saklovitij@Saklovitij-Inspiron-1545:~$ ifconfig

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:319 errors:0 dropped:0 overruns:0 frame:0

          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:48325 (48.3 KB)  TX bytes:48325 (48.3 KB)

saklovitij@Saklovitij-Inspiron-1545:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



saklovitij@Saklovitij-Inspiron-1545:~$ 


(hint) if the Wireless interface name is wlan0...
saklovitij@Saklovitij-Inspiron-1545:~$ iwconfig wlan0

wlan0     No such device

saklovitij@Saklovitij-Inspiron-1545:~$ 

4) Check for modules:
saklovitij@Saklovitij-Inspiron-1545:~$ lsmod

Module                  Size  Used by

binfmt_misc             6599  1 

rfcomm                 32575  4 

sco                     7867  2 

bnep                    9305  2 

l2cap                  38677  16 rfcomm,bnep

deflate                 1657  0 

zlib_deflate           19266  1 deflate

ctr                     3209  0 

twofish                 5431  0 

twofish_common         12811  1 twofish

camellia               18896  0 

serpent                17529  0 

blowfish                7318  0 

cast5                  15556  0 

des_generic            15995  0 

aes_i586                7280  0 

aes_generic            26875  1 aes_i586

xcbc                    2235  0 

rmd160                  6348  0 

sha512_generic          7296  0 

sha256_generic         11267  0 

sha1_generic            1795  0 

parport_pc             26378  0 

ppdev                   5556  0 

crypto_null             2242  0 

af_key                 23878  0 

snd_hda_codec_idt      54887  1 

btusb                  11535  2 

fwload                  2430  1 btusb

bluetooth              53007  9 rfcomm,sco,bnep,l2cap,btusb

joydev                  8735  0 

snd_hda_intel          22203  2 

snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel

snd_hwdep               5040  1 snd_hda_codec

i915                  293387  2 

snd_pcm                71603  2 snd_hda_intel,snd_hda_codec

snd_seq_midi            4588  0 

drm_kms_helper         30200  1 i915

snd_rawmidi            17783  1 snd_seq_midi

drm                   168726  3 i915,drm_kms_helper

snd_seq_midi_event      6047  1 snd_seq_midi

snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event

snd_timer              19067  2 snd_pcm,snd_seq

snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq

uvcvideo               55911  0 

dell_wmi                2852  0 

dcdbas                  5442  0 

videodev               43098  1 uvcvideo

snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

intel_agp              26784  2 i915

v4l1_compat            13359  2 uvcvideo,videodev

psmouse                59033  0 

serio_raw               4022  0 

soundcore                880  1 snd

snd_page_alloc          7216  2 snd_hda_intel,snd_pcm

i2c_algo_bit            5168  1 i915

video                  18712  1 i915

output                  1883  1 video

agpgart                32075  2 drm,intel_agp

lp                      7342  0 

parport                31492  3 parport_pc,ppdev,lp

usbhid                 36978  0 

hid                    67742  1 usbhid

usb_storage            40204  0 

ahci                   19013  0 

libahci                21731  3 ahci

sky2                   45456  0 

saklovitij@Saklovitij-Inspiron-1545:~$ 


(hint) search for the Wireless module
saklovitij@Saklovitij-Inspiron-1545:~$ lsmod | grep "wlan_module_name"
saklovitij@Saklovitij-Inspiron-1545:~$ 

5) Kernel boot messages
[ 2468.105713] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.124055] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.128477] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.128705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.145054] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.149560] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.149789] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.168053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.172562] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.172788] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.189046] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.193483] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.193716] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.205052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.209480] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.209709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.224053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.228476] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.228702] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.241054] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.245481] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.245705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.260053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.264471] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.264698] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.277037] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.282034] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.282470] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.292038] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.296056] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.296616] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.305040] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.309561] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.309787] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.324039] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.328463] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.328689] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.341037] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.347549] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.347781] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.368052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.372473] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.372694] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.389052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.393479] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.393707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.412052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.416470] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.416697] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.433078] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.437500] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.437732] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.456054] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.460498] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.460747] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.477052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.481316] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.481546] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.500053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.504470] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.504697] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.521052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.525478] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.525701] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.544053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.548563] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.548791] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.560053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.564478] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.564709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.577052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.581482] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.581708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.596064] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.600487] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.600715] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.613052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.617480] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.617708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.632063] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.636593] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.636845] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.648056] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.652389] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.652618] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.661038] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.665292] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.665521] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.677053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.681478] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.681705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.696059] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.700476] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.700703] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.713075] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.717504] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.717738] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.732053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.736499] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.736824] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.749052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.753477] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.753704] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.768053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.772478] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.772706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.785054] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.789476] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.789702] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.804053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.808479] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.808699] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.821053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.825475] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.825695] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.840057] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.844486] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.844711] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.857053] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.861499] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.861724] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.876052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.880476] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.880703] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.893052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.897480] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.897707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.912025] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.916368] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.916595] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.925052] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.929477] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.929702] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.944059] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.948487] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.948715] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.961025] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.965367] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.965595] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2468.981054] sky2 0000:09:00.0: eth0: disabling interface

[ 2468.985477] sky2 0000:09:00.0: eth0: enabling interface

[ 2468.985706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.004053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.008477] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.008708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.025083] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.029503] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.029728] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.048053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.052476] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.052704] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.069052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.073484] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.073716] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.092052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.096471] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.096693] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.113054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.117482] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.117710] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.136913] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.141347] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.141576] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.153054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.157494] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.157715] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.176054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.180474] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.180700] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.197055] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.201485] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.201709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.220053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.224485] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.224716] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.241053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.245478] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.245703] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.264057] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.268488] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.268710] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.285054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.289484] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.289709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.308061] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.312505] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.312730] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.329052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.333477] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.333705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.352053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.356473] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.356699] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.373052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.377480] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.377708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.396052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.400476] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.400704] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.417052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.421481] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.421707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.440055] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.444476] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.444703] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.461039] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.465295] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.465516] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.481053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.485479] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.485707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.504059] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.508497] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.508960] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.520054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.524571] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.524804] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.537055] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.541483] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.541710] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.556052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.560494] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.560748] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.573052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.577313] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.577543] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.592052] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.596477] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.596706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.609075] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.613505] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.613730] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.628054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.632481] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.632707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.645059] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.649572] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.649796] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.664064] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.668490] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.668712] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.681053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.685476] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.685706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.700053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.704471] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.704697] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.717053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.721477] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.721708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.736918] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.741345] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.741575] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.753066] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.757489] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.757718] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.772054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.776479] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.776708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.789106] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.793523] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.793755] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.808062] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.812478] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.812705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.825053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.829487] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.829717] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.844053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.848472] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.848697] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.861034] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.865454] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.865675] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.880054] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.884477] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.884700] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.897081] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.901602] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.901867] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.916065] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.920573] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.920806] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.933057] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.937580] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.937809] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.952053] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.956480] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.956711] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.969065] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.973574] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.973803] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2469.988058] sky2 0000:09:00.0: eth0: disabling interface

[ 2469.992482] sky2 0000:09:00.0: eth0: enabling interface

[ 2469.992710] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.005052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.009478] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.009708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.024054] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.028414] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.028648] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.040054] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.044478] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.044706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.061034] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.065462] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.065689] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.084053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.088476] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.088704] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.105086] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.109613] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.109900] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.128056] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.132563] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.132793] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.145059] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.149573] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.149798] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.164069] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.168492] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.168719] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.181079] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.185587] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.185815] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.200058] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.204571] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.204796] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.217057] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.221566] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.221792] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.236315] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.240825] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.241073] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.253053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.257483] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.257713] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.272045] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.276561] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.276791] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.293036] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.297466] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.297696] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.312037] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.316928] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.317211] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.329036] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.333479] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.333705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.348056] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.352391] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.352611] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.361032] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.365455] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.365680] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.384057] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.388564] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.388787] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.405290] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.409810] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.410042] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.428053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.432558] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.432785] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.449052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.453477] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.453701] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.472053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.476479] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.476703] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.493054] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.497568] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.497797] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.516111] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.520624] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.520847] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.537078] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.541501] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.541723] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.560060] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.564569] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.564797] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.581052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.585478] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.585706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.604053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.608479] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.608708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.625052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.629480] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.629709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.648068] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.652412] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.652684] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.669055] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.673930] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.674159] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.685046] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.689555] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.689779] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.708053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.712479] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.712707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.729053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.733477] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.733707] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.752054] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.756385] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.756608] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.765078] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.769501] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.769723] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.788057] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.792475] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.792701] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.809078] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.813588] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.813820] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.832052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.836501] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.836826] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.853052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.857476] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.857701] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.876053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.880477] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.880704] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.897051] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.901478] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.901706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.920053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.924473] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.924695] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.941052] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.945477] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.945705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.964062] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.968483] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.968717] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2470.985053] sky2 0000:09:00.0: eth0: disabling interface

[ 2470.989481] sky2 0000:09:00.0: eth0: enabling interface

[ 2470.989709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.008052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.012474] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.012710] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.029052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.033480] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.033709] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.052053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.056479] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.056706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.073068] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.077490] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.077712] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.096052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.100471] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.100698] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.117053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.121479] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.121708] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.140055] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.144470] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.144692] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.161027] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.165370] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.165599] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.181052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.185490] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.185717] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.204057] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.208481] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.208705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.225053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.229477] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.229706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.248053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.252470] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.252698] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.269055] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.273565] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.273795] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.292053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.296476] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.296705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.313075] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.317330] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.317559] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.329053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.333477] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.333705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.352053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.356480] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.356705] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.373052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.377474] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.377697] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.396052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.400470] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.400701] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.417053] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.421477] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.421706] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.440057] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.444480] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.444703] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.461035] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.465280] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.465507] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2471.481052] sky2 0000:09:00.0: eth0: disabling interface

[ 2471.486086] sky2 0000:09:00.0: eth0: enabling interface

[ 2471.486365] ADDRCONF(NETDEV_UP): eth0: link is not ready

saklovitij@Saklovitij-Inspiron-1545:~$ 

6) Network configuration
saklovitij@Saklovitij-Inspiron-1545:~$ sudo lshw -C network
[sudo] password for saklovitij: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:48:05:5a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
saklovitij@Saklovitij-Inspiron-1545:~$ 

7) Scan for networks:
saklovitij@Saklovitij-Inspiron-1545:~$ iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



saklovitij@Saklovitij-Inspiron-1545:~$ 


8) Ubuntu Version:
saklovitij@Saklovitij-Inspiron-1545:~$ lsb_release -d

Description:	Ubuntu 10.10

saklovitij@Saklovitij-Inspiron-1545:~$ 


9) Kernel/architecture (including 32 vs. 64 bit):
saklovitij@Saklovitij-Inspiron-1545:~$ uname -mr

2.6.35-23-generic-pae i686

saklovitij@Saklovitij-Inspiron-1545:~$ 

10) Restarting the network:
saklovitij@Saklovitij-Inspiron-1545:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                   [ OK ] 

saklovitij@Saklovitij-Inspiron-1545:~$ 

I hope somebody will be able to help. Many thanks beforehand.

Podas okys

---

### Post by fallofshadows on 2010-12-02
I actually JUST got this problem fixed and my wireless working : D

System > Administration > Synaptic Package manager. In the search bar, type in firmware-b43-lpphy-installer. 

That little package will not fail to install like other drivers do (for reasons still unknown to me) and it will fix your wireless problem. It did for me anyways!

---


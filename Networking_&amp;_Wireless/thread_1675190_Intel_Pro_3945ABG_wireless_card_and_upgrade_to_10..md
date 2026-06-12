---
title: "Intel Pro 3945ABG wireless card and upgrade to 10.10 Maverick"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by djibdjib on 2011-01-25
Hello!

I already posted a thread on this subject on the french speaking ubuntu community website, but no one could help.
Maybe I'll be more lucky here. Thanks for reading this, anyway!

So, I upgraded my ubuntu 10.04 to ubuntu Maverick 10.10 one week ago and since then, I can't connect to wifi networks.
My wireless card (Intel Pro 3945ABG) detects wireless networks,but can't connect properly.
Sometimes, at launch or at wake up, I can connect to an unprotected wireless network, but I never could connect to my WPA2 protected wireless network.
Generally, I can't connect to any wireless networks.

I checked solutions on the web and I read about problems with Bluetooth devices, I tried to fix it, but it doesn't seem to work for me.
Fixing described [here]("http://www.minasolution.com/tools/codepad/ubuntu-10.10-intel-wifi-disconnects-1291631208.html") (that doesn't work for me).

Please find more information on my system here under.

Thank you for your help,

djibdjib

EDIT: I forgot to tell that it's the first time I've a problem with that wireless card at upgrade and that on previous ubuntu versions I could connect to protected and unprotected networks without problems.
EDIT 2: Documentation says [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") that the driver should be ipw3945, but the nm-tool command seems to say that I've the iwl3945 driver. A problem or not? ;-)

Info:
```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
```
```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
$ lspci -nn | grep -i net
01:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
```
```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 02
       serial: 00:**:**:**:**:aa
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-24-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:da000000-da000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:**:**:**:**:07
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.8 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:dc000000-dc000fff ioport:5000(size=64)
```
```
$ lsmod
Module                  Size  Used by
aes_i586                7280  0 
aes_generic            26875  1 aes_i586
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_conexant    29971  1 
btusb                  10969  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
arc4                    1165  2 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
i915                  294989  4 
iwl3945                85550  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
iwlcore               127415  1 iwl3945
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231541  2 iwl3945,iwlcore
drm                   168092  4 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                    9536  0 
bluetooth              50500  7 rfcomm,sco,bnep,l2cap,btusb
cfg80211              144470  3 iwl3945,iwlcore,mac80211
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
joydev                  8767  0 
nand_ecc                3938  1 nand
psmouse                59033  0 
intel_agp              26694  2 i915
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
mtd                    18877  2 sm_common,nand
soundcore                880  1 snd
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
sdhci_pci               6339  0 
usbhid                 36882  1 hid_logitech
firewire_ohci          21042  0 
sdhci                  15890  1 sdhci_pci
hid                    67742  2 hid_logitech,usbhid
firewire_core          46643  1 firewire_ohci
ahci                   19198  5 
libahci                21664  1 ahci
e100                   30356  0 
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 e100
```
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:**:**:**:**:07  
          inet adr:192.168.1.8  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::216:36ff:fe54:607/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4652 erreurs:0 :0 overruns:0 frame:0
          TX packets:4405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3752072 (3.7 MB) Octets transmis:913585 (913.5 KB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2502 erreurs:0 :0 overruns:0 frame:0
          TX packets:2502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:195269 (195.2 KB) Octets transmis:195269 (195.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:**:**:**:**:aa  
          adr inet6: fe80::213:2ff:fe4b:c0aa/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:43 erreurs:0 :0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2870 (2.8 KB) Octets transmis:40923 (40.9 KB)
```
```
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```
```
$ uname -r -m 
2.6.35-24-generic i686
```
```
cat  /etc/network/interfaces
auto lo
iface lo inet loopback
```
```
$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:**:**:**:**:AA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ********:         Infra, 00:**:**:**:**:41, Freq 2452 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:**:**:**:**:07

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: 00:**:**:**:**:B8 ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:
```

---

### Post by djibdjib on 2011-01-26
Heeeeeeeeeeeelp!
Do I have to reinstall 10.04 to fix it?

---

### Post by djibdjib on 2011-01-29
Ok, I think I'll reinstall 10.04, no one seems to be able to help me ;-)
Thanks for ur interest...

---


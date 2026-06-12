---
title: "How to activate my Atheros ar5001 on my laptop?"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by kkwete on 2009-12-27
Hi all!
I've just a little problem:
I just changed my old wifi card in my laptop, a fujitsu siemens amilo Li 1818.
The old card was a sis163u...
Replaced by a atheros chip, an ar5001.
But now, it's impossible for me to activate the card with the button of the computer.
So, the card is recognized by ubuntu, but no router found, no network...
Can you give me a solution to activate my new wifi card without to use the button?
Thx!

i can give you that:


> kkwete@kkwete-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
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
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
> kkwete@kkwete-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11bg  Mode:Monitor  Frequency:2.472 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
kkwete@kkwete-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```
```
kkwete@kkwete-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
kkwete@kkwete-laptop:~$ kkwete@kkwete-laptop:~$ lsusb
kkwete@kkwete-laptop:~$: command not found
kkwete@kkwete-laptop:~$ Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
kkwete@kkwete-laptop:~$ Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
kkwete@kkwete-laptop:~$ Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
kkwete@kkwete-laptop:~$ Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
kkwete@kkwete-laptop:~$ Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
```
```
kkwete@kkwete-laptop:~$ lspci -nn | grep -i net
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
06:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```
```
kkwete@kkwete-laptop:~$ sudo lshw -C network
[sudo] password for kkwete: 
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:16:cf:a3:38:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f7000000-f700ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:5a:06:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:2000(size=256) memory:b0300000-b03000ff
```
```
kkwete@kkwete-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_codec_si3054     4636  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
joydev                 10272  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1660  2 
snd_seq_dummy           2656  0 
ecb                     2524  2 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 124260  0 
iptable_filter          3100  0 
snd                    59204  17 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
mac80211              181076  1 ath5k
soundcore               7264  1 snd
x_tables               16544  1 ip_tables
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
led_class               4096  1 ath5k
lp                      8964  0 
psmouse                56500  0 
parport                35340  2 ppdev,lp
serio_raw               5280  0 
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
```
```
kkwete@kkwete-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```
kkwete@kkwete-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:5a:06:02  
          inet adr:192.168.1.3  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::203:dff:fe5a:602/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:31636 erreurs:0 :0 overruns:0 frame:0
          TX packets:30501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:27771244 (27.7 MB) Octets transmis:8518100 (8.5 MB)
          Interruption:16 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:8 erreurs:0 :0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480 (480.0 B) Octets transmis:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:a3:38:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-A3-38-D0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
```
```
kkwete@kkwete-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
```
```
kkwete@kkwete-laptop:~$ uname -r -m
2.6.31-16-generic i686
```
```
kkwete@kkwete-laptop:~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback
```
```
kkwete@kkwete-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:16:CF:A3:38:D0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:03:0D:5A:06:02

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

I've to say that normally, i can activate my sis163u by using a button, with a green led.
But after replacing my new atheros ar5001, I can't switch on the led...strange!
I tried my card in an other laptop, a acer aspire 7735zg, and there is no problem!!!
Czan you help me?
thx!

---

### Post by Some Penguin on 2009-12-27
Worry about the connection, not the LED.  Looks like it's detected fine -- it's even powered on.

You might find 'wicd' friendlier than the standard network manager.

---

### Post by kkwete on 2009-12-27
i tried aircrack-ng to see, and airodump-ng don't detect any router...
On the acer aspire, with my card, any problem to  find my router...!
Really, i don't understand!
U're thinking wicd can resolve my problem?

---

### Post by kkwete on 2009-12-28
same problem...
wicd does not see my wireless network...

---

### Post by keicie on 2010-04-14
I seem to have exactly the same problem on my Fujitsu Esprimo V6535 laptop: prior to the installation of Ubuntu 9.1, the LED for the WLAN was lit, but that is now gone. Also, I have tried to check network settings and found WLAN box being checked... but only initially, now the check box got greyed out without any attempt to change settings. Although a novice on Linux and Ubuntu, I am now at the end of my wisdom. Any chance that Ubuntu 10.x will support the AR5001?

---

### Post by su-37 on 2010-05-21
I have the ATHk AR5001 and it used to work under Karmic. Under Lynx on the other hand it doesnt even see it. best of luck finding a fix.

---


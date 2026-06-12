---
title: "Wireless issue on Asus Netbook."
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by uRock on 2010-02-21
I am having problems with Ubuntu wanting to stay connected with Karmic. My Asus has wireless-n which is supposed to be faster, yet when it connects it is slower than wireless-g. Is this a fixable issue?

Thanx.

[COLOR="DarkRed"][SIZE="5"]Searchers! See post #14 for the fix to this problem![/SIZE][/COLOR]

---

### Post by northd_tech on 2010-02-21
First, we need to find out what kind of hardware you are running (and the current status of your network setup).

Can you open a terminal window and post the results of these commands:

```
lspci

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig

nm-tool

sudo iwlist scan
```

---

### Post by uRock on 2010-02-21
```
ronnie@ronnie-laptop:~$ lsmod
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
joydev                 10240  0 
ecb                     2524  2 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 258744  0 
mac80211              181140  1 ath9k
led_class               4096  1 ath9k
ath                     8060  1 ath9k
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
cfg80211               93052  3 ath9k,mac80211,ath
atl1c                  30880  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
eeepc_laptop           13936  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221320  4 
drm                   159584  4 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

```
```
ronnie@ronnie-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
```
ronnie@ronnie-laptop:~$ uname -a
Linux ronnie-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux
ronnie@ronnie-laptop:~$ sudo lshw -C network
[sudo] password for ronnie: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:7c:2c:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.11 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:70:b6:3b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```
```
ronnie@ronnie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:70:b6:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:7c:2c:d0  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe7c:2cd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2301799 (2.3 MB)  TX bytes:271198 (271.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-7C-2C-D0-37-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ronnie@ronnie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"here"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:23:69:04:E1:5F   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=23/70  Signal level=-87 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ronnie@ronnie-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0  [Auto here] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        00:25:D3:7C:2C:D0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Ham-a-lot:       Infra, 00:25:9C:09:75:63, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA
    *here:           Infra, 00:23:69:04:E1:5F, Freq 2432 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Fire Flies:      Infra, 00:26:F2:C0:4E:FC, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    glider:          Infra, 00:14:BF:72:27:CE, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WEP

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.14

    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12
    DNS:             192.168.1.14


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        90:E6:BA:70:B6:3B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```Thanks for helping.:D

---

### Post by northd_tech on 2010-02-22
> **iRock said:**
>  **lsmod**
Module                  Size  Used by

**ath9k **                258744  0 
mac80211              181140  1 **ath9k**
led_class               4096  1 **ath9k**
ath                     8060  1 **ath9k**

cfg80211               93052  3 **ath9k**,mac80211,ath
atl1c                  30880  0 

**  lspci**
01:00.0 Ethernet controller: Attansic Technology Corp. **Atheros AR8132** / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: **Atheros** Communications Inc. **AR9285 Wireless** Network Adapter (PCI-Express) (rev 01)
  
**uname -a**
Linux ronnie-laptop **2.6.31-19-generic** #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 **i686** GNU/Linux
  
sudo lshw -C network
[sudo] password for ronnie: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:7c:2c:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=ath9k** ip=192.168.1.11 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:70:b6:3b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=atl1c** driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

**  ifconfig**
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:70:b6:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:7c:2c:d0  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
[COLOR=Indigo]**          inet6 addr: fe80::225:d3ff:fe7c:2cd0/64 Scope:Link**[/COLOR]
**          UP BROADCAST RUNNING** MULTICAST  MTU:1500  Metric:1
          RX packets:1900 **errors:0** dropped:0 overruns:0 frame:0
          TX packets:1438 **errors:0** dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:2301799 (2.3 MB)**  **TX bytes:271198 (271.1 KB)**

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-7C-2C-D0-37-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  **iwconfig**
wlan0     IEEE 802.11bgn  ESSID:"here"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:23:69:04:E1:5F   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=23/70  Signal level=-87 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ronnie@ronnie-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0  [Auto here] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        00:25:D3:7C:2C:D0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Ham-a-lot:       Infra, 00:25:9C:09:75:63, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA
    *here:           Infra, 00:23:69:04:E1:5F, Freq 2432 MHz, Rate 54 Mb/s, **Strength 32** WPA WPA2
    Fire Flies:      Infra, 00:26:F2:C0:4E:FC, Freq 2412 MHz, Rate 54 Mb/s, **Strength 100** WPA2
    glider:          Infra, 00:14:BF:72:27:CE, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WEP

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.14

    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12
    DNS:             192.168.1.14


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        90:E6:BA:70:B6:3B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

OK- I have bolded the important parts of those results.  That is an Atheros **AR9285 **wireless interface that looks to have the proper driver modules loaded (that "ath9k" stuff up top).

Your cabled ethernet network card is an Attansic **Atheros AR8132 **that doesn't appear to be plugged into anything right now.

I suspect the purple part above is why your 802.11n is so slow (I started looking for similar answers why my Broadcom "4328" 802.11n wireless has been so slow and the connection dropping out so often a couple of weeks ago).

Incidentally, your connection looks much weaker than another WiFi "radio" in your neighborhood (the one with the Strength 100 that I bolded above).  That one might be "walking" over your signal somewhat- you might want to change your router settings further away from 2412 MHz sometime down the road- you've got 4 wireless networks in pretty close proximity.

Can you go to this website for me and run both tests (the IPv4 one on the left and the IPv6 one on the right) and post what you find out?  You can actually do this from a Windows machine if you need to- it just tests your router/modem and ISP.

[http://www.ip6.me](http://www.ip6.me)

Also, can you post the results of this terminal command:

```
sudo iwlist scan
```edit:  Oh yeah. that's a 32-bit version running the **2.6.31-19-generic **kernel (which is one of the very newest), so you must be running Karmic Koala 9.10.

---

### Post by uRock on 2010-02-22
> **northd_tech said:**
> OK- I have bolded the important parts of those results.  That is an Atheros **AR9285 **wireless interface that looks to have the proper driver modules loaded (that "ath9k" stuff up top).

Your cabled ethernet network card is an Attansic **Atheros AR8132 **that doesn't appear to be plugged into anything right now.

I suspect the purple part above is why your 802.11n is so slow (I started looking for similar answers why my Broadcom "4328" 802.11n wireless has been so slow and the connection dropping out so often a couple of weeks ago).

Incidentally, your connection looks much weaker than another WiFi "radio" in your neighborhood (the one with the Strength 100 that I bolded above).  That one might be "walking" over your signal somewhat- you might want to change your router settings further away from 2412 MHz sometime down the road- you've got 4 wireless networks in pretty close proximity.

Can you go to this website for me and run both tests (the IPv4 one on the left and the IPv6 one on the right) and post what you find out?  You can actually do this from a Windows machine if you need to- it just tests your router/modem and ISP.

[http://www.ip6.me](http://www.ip6.me)

Also, can you post the results of this terminal command:

```
sudo iwlist scan
```edit:  Oh yeah. that's a 32-bit version running the **2.6.31-19-generic **kernel (which is one of the very newest), so you must be running Karmic Koala 9.10.
Yup, Karmic on this machine. The site shows IPv4 for my IP. No IPv6. I'll have to boot back to Ubuntu to run the code.

---

### Post by uRock on 2010-02-22
```
ronnie@ronnie-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:04:E1:5F
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=7/70  Signal level=-103 dBm  
                    Encryption key:on
                    ESSID:"here"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000016e5207160
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000468657265
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1605050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405050700000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A88000236904E15F1021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
          Cell 02 - Address: 00:14:BF:72:27:CE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption key:on
                    ESSID:"glider"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000119cd6bab1f
                    Extra: Last beacon: 532ms ago
                    IE: Unknown: 0006676C69646572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

ronnie@ronnie-laptop:~$ 
```

---

### Post by northd_tech on 2010-02-22
Well the good news- that really strong signal "Fire Flies" is now gone.  It looks to me like you are on the ESSID "radio station" that is running on Channel 5 and "glider" is running on Channel 1 (at the same 2.412 GHz) that the strong signal was on earlier.

You might want to change from Channel 5 to something higher (further away from 2.412 GHz) if you see those really strong signals in your neigborhood again (with **sudo iwlist scan** command) and if you need to go into your wireless router settings for some reason in the near future.

Why don't you use the speed testing links at my post #4 here:
[http://ubuntuforums.org/showpost.php?p=8849219&postcount=4](http://ubuntuforums.org/showpost.php?p=8849219&postcount=4)

to run some speed tests and take some "before" screenshots (that's in Applications > Accessories > Take Screenshot under ubuntu as I recall, but I'm in Vista babysitting file transfers for a while).

You might want to post the speed test screenshots here just to have a convenient record for the future to compare before to after.

These are some more of my "notes to self" on this project:

Incredibly Slow Wireless with Ubuntu
[http://ubuntuforums.org/showthread.php?t=1406817](http://ubuntuforums.org/showthread.php?t=1406817)

Slow Wireless Network [test results]
[http://ubuntuforums.org/showthread.php?t=1195755](http://ubuntuforums.org/showthread.php?t=1195755)

Also, let's keep a link to this thread too for future reference (I'm working on a similar speed problem in my ubuntu).

---

### Post by uRock on 2010-02-22
The Netbook came with Wireless-N which doesn't seem to be working well. I changed the router to G only and it seemed to make the connection go up a bit. I am currently 2 feet away from the router and getting a signal strength of less than 80 percent, which is bad. I went to speakeasy.net and ran their speed test, this is the result.

I am going to restart into XP and see if it is higher. It has been giving me high quality so far.

I have run the speed test in XP on the same machine and its ratings are 20232kbps down and 1971kbps up. The signal strength is reading 100% with XP.

---

### Post by uRock on 2010-02-22
Here is a screenshot from my wife's HP notebook, which has a 100% connect while sitting in the exact same spot as the Netbook was.

---

### Post by northd_tech on 2010-02-22
> **iRock said:**
> 
I have run the speed test in XP on the same machine and its ratings are 20232kbps down and 1971kbps up. The signal strength is reading 100% with XP.
Well the good news- you've got an XP baseline now, but **did you try any of that under ubuntu for the "before" case** (or if the test times out then that would be a "died during the race" I suppose ;) ).

Ummm, according the speakeasy speed test website in those screenshots, I just got 6.61 **M**bps down and 4.56 **M**bps upstream to Dallas, TX.  Dallas was the fastest, but Seattle, SanFran, Chicago, NYC, and LA were all in the 2-5 Mbps range (both up and down).  DC was the "pig" at 1.8 Mbps upload and 2.0 Mbps down.  For some reason Atlanta's test was a rock-solid even ~3.0 Mbps both up and down, where the other tests surged and jumped a lot.

This was under WIRELESS Ubuntu 9.04 on my Broadcom "4328" 802.11n just now at this website:

[http://speakeasy.net/speedtest/](http://speakeasy.net/speedtest/)

That actually is faster than the 100Mbps-cabled ethernet tests that I was  running from the same ISP last night.  We had trouble for months, and  Comcast finally convinced us to try/"lease" (for S&H) a new Netgear  WNR1000 wireless router.

Those "speakeasy" numbers were roughly 1/10 of what I saw earlier tonight using the Firefox "bandwidth tester" plugin (if that can be believed)- those speeds are on this thread:

[http://ubuntuforums.org/showpost.php?p=8868194&postcount=2](http://ubuntuforums.org/showpost.php?p=8868194&postcount=2)

Why don't you grab some "before" ubuntu numbers, and then we can work on "souping up" that WiFi, iRock?  :twisted:

---

### Post by uRock on 2010-02-22
Cool, I am installing Netbook first to see if it works any better I'll run the test wired and wireless. It is done installing , I just have to reboot and do a load of updates before it'll be ready.

---

### Post by coskierken on 2010-02-24
Did I miss something?  What are your setting in the router?  To connect at 300 (at least 270) I believe you should use wpa2 aes.  I get 270 connection with 2.4 ghz with a Rosewill RNX-N1 usb stick (only 2.4 GHZ) and a Netgear N router set to the same.  Of course, it does not transfer files at that speed over the network, but it is the fastest I can connect to the router.  I am only about 8 ft away from the router.

---

### Post by uRock on 2010-02-24
> **coskierken said:**
> Did I miss something?  What are your setting in the router?  To connect at 300 (at least 270) I believe you should use wpa2 aes.  I get 270 connection with 2.4 ghz with a Rosewill RNX-N1 usb stick (only 2.4 GHZ) and a Netgear N router set to the same.  Of course, it does not transfer files at that speed over the network, but it is the fastest I can connect to the router.  I am only about 8 ft away from the router.

The setting I changed on the router was to make it 802.11G only, which brought up the strength a little bit. The problem is within Ubuntu. The same Netbook when running XP gets about 30% higher connectivity. It must have something to do with the support for the wireless NIC, because when I tested the connectivity on my wife's HP laptop while running Ubuntu 9.10 it had the same connectivity as  my XP and her Windows 7 OSes.

I also admit that I am disgusted with my router. I paid extra to get a router with higher range than the basic Linksys, yet my neighbors' routers seem to be giving me higher connection percentages. Either way, I prefer to get my Ubuntu Netbook connecting better than it is.

---

### Post by uRock on 2010-02-24
Entering the following code into a terminal fixed my problem.```
sudo apt-get install linux-backports-modules-karmic
```
I found the fix here [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by northd_tech on 2010-02-25
Hi iRock- sorry I've been busy with work and family stuff.

Do you know if your system uses GRUB or GRUB2 (or LILO or ?? ) as a boot manager/loader?  I disabled my IPv6 in my GRUB configuration file with a kernel option (and blacklisted it elsewhere).

It might be easiest if you just post the results of this command (or attach it as a .TXT file to another post):

```
sudo cat /boot/grub/menu.lst
```

---

### Post by northd_tech on 2010-02-25
> **iRock said:**
> Entering the following code into a terminal fixed my problem.```
sudo apt-get install linux-backports-modules-**alsa**-karmic-generic
```I found the fix here [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Well... ALSA is a sound/microphone thing (not "officially" wireless networking), but some laptops/netbooks can be a little "funny" at times... 

[http://www.alsa-project.org](http://www.alsa-project.org)

The "backports" have been known to fix (and occasionally "break" ) many things, and they have been pretty mysterious from what I've seen so far.  :confused:

---

### Post by uRock on 2010-02-25
Crap, I copied the wrong command. Thanks for pointing that out. I'll go back and fix it. I guess I fixed the mic problem that I did know I had yet.

---

### Post by uRock on 2010-02-25
Using Grub1.97beta.

I ran the commend, it said no such file.

Thanx again for helping.

---


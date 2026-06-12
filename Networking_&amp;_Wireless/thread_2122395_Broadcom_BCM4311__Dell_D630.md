---
title: "Broadcom BCM4311 / Dell D630"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by akotobamfo on 2013-03-05
My wireless is connected to the internet network at work but i cannot access the internet. my colleagues who use windows are able to access the internet but i cannot. i use Ubuntu 12.10 on my Dell Latitude D630. please help:confused:

---

### Post by varunendra on 2013-03-05
Welcome to the forums akotobamfo!

Please follow the Wireless Script link in my signature, follow the instructions in the linked post and post back the contents of "netinfo.txt" file as mentioned there.

---

### Post by akotobamfo on 2013-03-05
I am pretty new to ubuntu. please explain

---

### Post by varunendra on 2013-03-05
Just follow this link : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Read it carefully (post no. 2) and do what it asks to do.

Post back if having any problem with any part of the linked post.

---

### Post by akotobamfo on 2013-03-05
```
*************** info trace ****************



**** uname -a ****


Linux edmund-Latitude-D630 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


**** lsusb ****


Bus 002 Device 003: ID 05dc:a761 Lexar Media, Inc. 
Bus 004 Device 002: ID 413c:8133 Dell Computer Corp. Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) Minicard GPS Port
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:"Lib_Conf"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
usb_storage            48839  1 
bnep                   18141  2 
rfcomm                 46620  0 
parport_pc             32689  0 
bluetooth             209249  10 bnep,rfcomm
ppdev                  17074  0 
joydev                 17458  0 
snd_hda_codec_idt      70210  1 
snd_hda_intel          33492  3 
nouveau               896008  3 
snd_hda_codec         134213  2 snd_hda_codec_idt,snd_hda_intel
arc4                   12530  2 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
ttm                    83596  1 nouveau
snd_seq_midi           13325  0 
b43                   369857  0 
snd_rawmidi            30513  1 snd_seq_midi
coretemp               13401  0 
snd_seq_midi_event     14900  1 snd_seq_midi
drm_kms_helper         49113  1 nouveau
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
drm                   288721  5 nouveau,ttm,drm_kms_helper
snd_timer              29426  2 snd_pcm,snd_seq
kvm                   414071  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              540032  1 b43
i2c_algo_bit           13414  1 nouveau
snd                    78921  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gpio_ich               13384  0 
dell_laptop            17370  0 
dell_wmi               12682  0 
soundcore              15048  1 snd
yenta_socket           31818  0 
mxm_wmi                13022  1 nouveau
dcdbas                 14439  1 dell_laptop
sparse_keymap          13891  1 dell_wmi
microcode              22804  0 
cfg80211              206797  2 b43,mac80211
psmouse                95595  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
pcmcia_rsrc            18289  1 yenta_socket
wmi                    19071  3 nouveau,dell_wmi,mxm_wmi
sierra                 18267  0 
mac_hid                13206  0 
pcmcia_core            22570  2 yenta_socket,pcmcia_rsrc
video                  19391  1 nouveau
option                 30096  0 
lp                     17760  0 
lpc_ich                17062  0 
usb_wwan               20099  1 option
usbserial              42356  3 sierra,option,usb_wwan
ssb_hcd                12870  0 
bcma                   35657  1 b43
serio_raw              13216  0 
parport                46346  3 parport_pc,ppdev,lp
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
tg3                   148781  0 
ssb                    52037  2 b43,ssb_hcd


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            option1
  State:             disconnected
  Default:           no

  Capabilities:


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Lib_Conf] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Incubator_Access:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA
    CBDWifi:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    CloudGhana-0202699110: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 29
    *Lib_Conf:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA

  IPv4 Settings:
    Address:         192.168.1.41
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

no-auto-default=<MAC address removed>,

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
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Lib_Conf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d06a0500
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 00084C69625F436F6E66
                    IE: Unknown: 010882848B963048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32030C1218
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Incubator_Access"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s
                    Mode:Master
                    Extra:tsf=0000000109fd3043
                    Extra: Last beacon: 972ms ago
                    IE: Unknown: 0010496E63756261746F725F416363657373
                    IE: Unknown: 010882848B963048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32030C1218
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"CBDWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c28b51d80
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 000743424457696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0F0800000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F0800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


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
#blacklist bcm43xx

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


[    2.282683] tg3.c:v3.123 (March 21, 2012)
[    2.292257] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    2.292275] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    2.292284] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    2.292293] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    2.292302] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    2.304192] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address <MAC address removed>
[    2.304198] tg3 0000:09:00.0: eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.304201] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.304204] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.356103] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   19.667763] wmi: Mapper loaded
[   20.349880] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   20.598341] Registered led device: b43-phy0::tx
[   20.598362] Registered led device: b43-phy0::rx
[   20.598384] Registered led device: b43-phy0::radio
[   21.864039] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   21.946507] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.946798] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.057868] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[   23.780354] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   23.780359] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   24.408527] wlan0: authenticate with <MAC address removed>
[   24.441224] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.443071] wlan0: authenticated
[   24.444146] wlan0: associate with <MAC address removed> (try 1/3)
[   24.446193] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   24.446611] wlan0: associated
[   24.447057] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.703433] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  364.128070] tg3 0000:09:00.0: eth0: Link is down
[  366.934854] dell_wmi: Unknown key e044 pressed
[  391.636743] wlan0: authenticate with <MAC address removed>
[  391.648568] wlan0: send auth to <MAC address removed> (try 1/3)
[  391.650979] wlan0: authenticated
[  391.652323] wlan0: associate with <MAC address removed> (try 1/3)
[  391.654727] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  391.655360] wlan0: associated


**************** done ********************
```

---

### Post by varunendra on 2013-03-05
> **akotobamfo said:**
> ```

**** iwconfig ****

wlan0     IEEE 802.11bg  ESSID:"Lib_Conf"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          **Bit Rate=[COLOR="#000080"]48 Mb/s[/COLOR]**   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=66/70**  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0

..
..
- Device: wlan0  [Lib_Conf] ----------------------------------------------------
  **Type:              802.11 WiFi**
  Driver:            b43
 ** State:             [COLOR="#000080"]connected[/COLOR]**
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    **Speed:           [COLOR="#000080"]48 Mb/s[/COLOR]**
..
..

**** dmesg ****
..
..
[  391.636743] wlan0: authenticate with <MAC address removed>
[  391.648568] wlan0: send auth to <MAC address removed> (try 1/3)
[  391.650979] wlan0: **[COLOR="#000080"]authenticated[/COLOR]**
[  391.652323] wlan0: associate with <MAC address removed> (try 1/3)
[  391.654727] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[  391.655360] **wlan0: [COLOR="#000080"]associated[/COLOR]**


**************** done ********************
```
I can't see any issues in the connectivity. As per the above outputs you are already connected with a nice 48 Mb/s speed.

What is the output of -
```
ping -c4 192.168.1.1
ping -c4 google.com
```

And please use 'Code' tags while posting outputs. I have edited your above post to do that for you. Follow the 'Code tags example' link in my signature to see how to do that yourself.

Thanks.

---

### Post by prodigy_ on 2013-03-05
> **varunendra said:**
> I can't see any issues in the connectivity. As per the above outputs you are already connected with a nice 48 Mb/s speed.

What is the output of -
```
ping -c4 192.168.1.1
ping -c4 google.com
```

And please use 'Code' tags while posting outputs. I have edited your above post to do that for you. Follow the 'Code tags example' link in my signature to see how to do that yourself.

Thanks.

The OP said it's a Wi-Fi network at work so I'd expect any combination of the following:
1) Firewall. Even if ping fails, this doesn't necessarily mean TCP traffic is blocked.
2) Some kind of id check (whether the workstation is a company asset or not).
3) (Additional) browser-based auth.
4) Proxy.

---

### Post by akotobamfo on 2013-03-05
this is the result of both > edmund@edmund-Latitude-D630:~$ ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.964 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=1.04 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.03 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=1.07 ms
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 0.964/1.029/1.076/0.046 ms
edmund@edmund-Latitude-D630:~$ ^C
edmund@edmund-Latitude-D630:~$ ping -c4 google.com
PING google.com (74.125.138.102) 56(84) bytes of data.
64 bytes from dn-in-f102.1e100.net (74.125.138.102): icmp_req=1 ttl=46 time=578 ms
64 bytes from dn-in-f102.1e100.net (74.125.138.102): icmp_req=2 ttl=46 time=428 ms
64 bytes from dn-in-f102.1e100.net (74.125.138.102): icmp_req=3 ttl=46 time=546 ms
64 bytes from dn-in-f102.1e100.net (74.125.138.102): icmp_req=4 ttl=46 time=496 ms
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 428.904/512.841/578.953/56.683 ms
edmund@edmund-Latitude-D630:~$ 

---

### Post by prodigy_ on 2013-03-05
Well, if with this you still can't open websites, consider contacting your IT help-desk. Best case: they'll help you. Worst case: depends on your corporate IT policy. :)

---

### Post by varunendra on 2013-03-05
> **akotobamfo said:**
> this is the result of both

Means you are perfectly able to reach google.com. Can you open it in your browser?

If not, make sure your browser is not set to use a proxy (or the configuration is correct if it is using a proxy).

Among a very few reasons why you can't open a web page is what prodigy_ mentioned above - that is - maybe the firewall in your workplace is configured to NOT allow you to access internet (by blocking certain protocols like http/https). In that case, contact the IT support in your office.

---


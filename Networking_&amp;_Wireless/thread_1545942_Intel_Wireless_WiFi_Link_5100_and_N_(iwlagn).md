---
title: "Intel Wireless WiFi Link 5100 and N (iwlagn)"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by nfo on 2010-08-04
Hello, 

i don t get the Intel WiFi Link 5100 working with my N network.
In mixed mode i get arround 54 Mbits, in only N mode the connection went from 5 MB/sec to 0 MB/sec and stuck there.


**Hardware**
Client[INDENT]02:00.0 Network controller [0280]: 
Intel Corporation Wireless WiFi Link 5100 [8086:4232]

[/INDENT]Router[INDENT]Netgear WNDR 3700
[/INDENT]**Software**
Client[INDENT]Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic i686
iw version 0.9.19
iwlagn version 1.3.27k
[/INDENT]Router[INDENT]DD Wrt build 14311
Stock firmware 1.0.4.68
[/INDENT]Some more info

lshw

```

  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:a5:e3:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.116 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:f4200000-f4201fff

```dmesg

```

[   21.596770] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   21.596774] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   21.596846] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.596856] iwlagn 0000:02:00.0: setting latency timer to 64
[   21.596894] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   21.644588] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.644676] iwlagn 0000:02:00.0: irq 32 for MSI/MSI-X
[   21.772469] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   21.803059] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   68.271155] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:3f:0e:78:39:0a tid = 0
[   22.188598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.427733] wlan0: deauthenticating from 00:3f:0e:78:39:0a by local choice (reason=3)
[   39.427784] wlan0: direct probe to AP 00:3f:0e:78:39:0a (try 1)
[   39.432696] wlan0: direct probe responded
[   39.432701] wlan0: authenticate with AP 00:3f:0e:78:39:0a (try 1)
[   39.434469] wlan0: authenticated
[   39.434488] wlan0: associate with AP 00:3f:0e:78:39:0a (try 1)
[   39.438834] wlan0: RX AssocResp from 00:3f:0e:78:39:0a (capab=0x531 status=0 aid=1)
[   39.438838] wlan0: associated
[   39.442548] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.456036] wlan0: no IPv6 routers present


```iw wlan0 link

```

Connected to 00:3f:0e:78:39:0a (on wlan0)
    SSID: codejungle.org
    freq: 2437
    RX: 136940305 bytes (413206 packets)
    TX: 9998266 bytes (54638 packets)
    signal: -68 dBm
    tx bitrate: 65.0 MBit/s MCS 7

```iwconfig wlan0

```

wlan0     IEEE 802.11abgn  ESSID:"codejungle.org"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:3F:0E:78:39:0A   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by SaintDanBert on 2010-08-11
My iwlagn crashes randomly.  So far I'm not getting any help.

[Off topic question] How did you get the red text inside the code-block?
I didn't know that would work?  Is it simply

code-start
text ... text
color-start
blah ... blah
color-end
text ... text
code-end

Cheers,
~~~ 0;-Dan

---


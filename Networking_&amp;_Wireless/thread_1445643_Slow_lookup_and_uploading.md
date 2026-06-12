---
title: "Slow lookup and uploading"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by b0arer753 on 2010-04-02
I've been having slow load times which I have been attributing to [this bug]("http://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757"), but within this past few weeks, any time I try to upload anything to megaupload, mediafire, zshare, etc. my upload speed is betwen 1kb/s - 30kb/s when it used to upload around 2mb/s.

I'm starting to think I might have something else going on (as well?).

Here's my specs:

> Gateway MD7818u laptop with Ubuntu 9.1 running GNOME 2.28.1

kernel:
2.6.31-20-generic x86_64


> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
07:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)
07:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)

> IEEE 802.11abgn  ESSID:"JUICEMAN"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:21:63:E7:B4:F3   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> iwlagn                124896  0 
iwlcore               133600  1 iwlagn
mac80211              210040  2 iwlagn,iwlcore
cfg80211              109144  3 iwlagn,iwlcore,mac80211


> [   15.833395] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.833398] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.834142] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.834152] iwlagn 0000:02:00.0: setting latency timer to 64
[   15.834237] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.871788] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.871870] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   94.805563] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   94.974122] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12

>  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:28:68:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.134 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:fd:c9:a3
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0700000-f0703fff ioport:4000(size=256) memory:b8000000-b801ffff(prefetchable)


> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:63:E7:B4:F3
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"JUICEMAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000682ee1ae5
                    Extra: Last beacon: 1991650ms ago
                    IE: Unknown: 00084A554943454D414E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C


> sudo /etc/init.d/networking restart
sudo: unable to resolve host sexxysexxybaby2
 * Reconfiguring network interfaces...                                   [ OK ] 

---

### Post by b0arer753 on 2010-04-03
Anyone have any ideas or need any other info?

---

### Post by Martje_001 on 2010-04-03
What's your ISP? Some ISP's use a technique called [Traffic Shaping]("http://en.wikipedia.org/wiki/Traffic_shaping") on their networks, which could explain the behavior you're seeing.

Try uploading something with a secure connection, so your ISP can't see what you're doing and won't apply any traffic control.

---

### Post by b0arer753 on 2010-04-03
I have Verizon Fios.

I signed up for dropbox (I've been looking for something like this.. thanks!) and uploaded there over https and it's still going around 11kb/s

edit: I did a verizon speedtest and it showed my down being 16mb/s and my up being **.054mb/s**!!!

---

### Post by Martje_001 on 2010-04-03
Dropbox limits itself when uploading (see preferences). Or did you upload a file using the web interface?

---

### Post by b0arer753 on 2010-04-03
I tried both. 

I also did a speed test which came back with my upload being .05mb/s when it should be at least 10mb/s (I have 25/25 fios)

---

### Post by Martje_001 on 2010-04-03
Strange. Have you tried to call Verzion about it?

Edit: Oh wait a minute, you're using a wireless connection. Have you tried testing your Internet connection speed with a cable attached?

---


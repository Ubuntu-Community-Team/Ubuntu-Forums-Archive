---
title: "Regular package loss with 9.10 wifi"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by sorenmogensen on 2009-11-25
After upgrading to 9.10 I have noticed that my network connection seemed to freeze intermittently. Initially I thought it was my network connection but have narrowed it down to only happening under 9.10.

If I execute a ping to my router and let it run for an hour - there will be sections like the following:
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=845 ttl=64 time=1.18 ms
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=846 ttl=64 time=1.19 ms
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=882 ttl=64 time=1990 ms
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=883 ttl=64 time=988 ms
-- and --
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=2706 ttl=64 time=1.18 ms
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=2707 ttl=64 time=1.17 ms
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=2743 ttl=64 time=1000 ms
64 bytes from dsldevice.config (192.168.1.254): icmp_seq=2744 ttl=64 time=1.33 ms

I.e. intervals with total package loss of 36 pings; averaging to a roughly 3% package loss over an hour.

There are no statements in /var/log/syslog during the time of the test run.

If I boot my laptop with a 9.04 live CD and execute the same test it completes with 0% package loss. The intermittent drops have a huge impact on streaming and gaming, and I am debating going back to 9.04 - but would prefer if someone on here knows of a solution that allows me to stay with 9.10.

I have tried replacing the network manager with WICD but this had no impact on the test results. The issue has been around ever since the upgrade to 9.10.

All the data from the wifi post guide:=================================
**Machine Brand and Model:** Dell XPS 16 laptop
**Wireless Brand, Model and Wireless Chipset:** Intel Corporation Wireless WiFi Link 5100 [8086:4232]
** check interface:** wlan0     IEEE 802.11abgn  ESSID:"MYSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:77:59:4F   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
**Check for modules: **iwlagn                124832  0 
iwlcore               133248  1 iwlagn
mac80211              210104  2 iwlagn,iwlcore
cfg80211              109144  3 iwlagn,iwlcore,mac80211
**Kernel boot messages:** (attached)
**Network configuration:**   *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:e6:c1:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.66 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:da:2b:30
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:fc000000-fc00ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
** Scan for networks:**
wlan0     Scan completed :
          Cell 01 - Address: 00:11:F5:77:59:4F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"MYSID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005536c09186
                    Extra: Last beacon: 115210ms ago
                    IE: Unknown: 00054631335448
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD060010180200F0
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
**Ubuntu Version:** Ubuntu 9.10
**Kernel/architecture (including 32 vs. 64 bit):** 2.6.31-15-generic x86_64
**Restarting the network:  *** Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

---

### Post by sorenmogensen on 2009-11-25
I have tried using the 9.10 live CD to re-run the test in order to eliminate any personal configuration. This test fails with the same package drops; thus this issue appears to be inherent to 9.10.

---

### Post by sorenmogensen on 2009-11-29
Found a workaround by changing from WPA2 to WPA. Now I get no package drops under 9.10.

---


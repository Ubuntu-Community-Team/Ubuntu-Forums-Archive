---
title: "Wireless repeatedly stops working on HP Pavillion/Intel 4965AG/Karmic"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by SparkyUSN on 2010-02-09
Wise crowd, I need help.  I am running 9.10 and am a loyal Ubuntu user though thin on the knowledge.  I am willing to learn and I appreciate the help in advance.

My wireless LAN connection on this machine occasionally stops working.  The network traffic bar shows periodic very small transmissions but the failure of all network dependent applications (Firefox, package manager, etc.) indicates to me that the machine is no longer talking to the net.  I can fix it by reselecting my home network in nm-applet from the drop-down list.  This causes the machine to disconect, reconnect and all is well for some random period of time thereafter.  Here's some data:

I'm running an HP Pavillion laptop.

```
~$ lspci | grep Wireless
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```
```

~$ lsmod | grep iwl
iwlagn                124768  0 
iwlcore               134820  1 iwlagn
mac80211              243496  2 iwlagn,iwlcore
led_class               5256  2 iwlcore,sdhci
cfg80211              152616  3 iwlagn,iwlcore,mac80211
```

```
~$ dmesg | grep iwl
[   13.684647] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.684650] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.686866] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.686877] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.686927] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.730418] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.730502] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   14.055584] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.322907] iwlagn 0000:02:00.0: firmware: requesting lbm-iwlwifi-4965-2.ucode
[   15.516599] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   15.733229] Registered led device: iwl-phy0::radio
[   15.733260] Registered led device: iwl-phy0::assoc
[   15.733288] Registered led device: iwl-phy0::RX
[   15.733326] Registered led device: iwl-phy0::TX
```

```
~$ sudo lshw -C network
[sudo] password for smiths: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:2d:0d:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f4000000-f4001fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:2d:59:84
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:c000(size=256) memory:f8000000-f8000fff memory:c0000000-c001ffff(prefetchable)
```

```

~$ iwlist scan 

wlan0     Scan completed :
          Cell 01 - Address: 00:40:F4:E7:C0:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Forge"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a9637508d
                    Extra: Last beacon: 17230ms ago
                    IE: Unknown: 0005466F726765
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

~$ lsb_release -d
Description:	Ubuntu 9.10

~$ uname -mr
2.6.31-19-generic x86_64

~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface wlan0=wlan0.
                        

```

I don't know if this is related or not, but a couple of months ago I unsuccessfully attempted to share a hotel's wired Internet connection over my wireless card.  I may have hosed some settings or it could be unrelated.

The "unknown interface" portion of the restart attempt is interesting but I don't know enough to fix it.

Thanks again.  I look forward to learning something.

---

### Post by chili555 on 2010-02-10
Would you please try this and give us your results?

[http://ubuntuforums.org/showpost.php?p=8804591&postcount=2](http://ubuntuforums.org/showpost.php?p=8804591&postcount=2)

---


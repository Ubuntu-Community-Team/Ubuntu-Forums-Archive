---
title: "My Maverick PC will intermittently kill my Wifi network"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by mwshook on 2010-11-15
This week I did a fresh install of Ubuntu 10.10 on a newly assembled PC. The hardware I am using is below.

My wife has a Macbook with built-in Wifi connected to our Linksys router. Previously, the connection would drop 0-2 times a day. She would turn off Wifi on her Macbook, turn it back on, and it would reconnect immediately.

Since getting my Ubuntu PC, these disconnections have become more frequent, every 30-90 minutes. They effect both computers simultaneously. And now, I MUST turn off Wifi on my Ubuntu box to regain the connection.
Switching it off and on with the Mac doesn't help. Unplugging the router doesn't help. I have to run upstairs and uncheck "Enable Wireless" on the Ubuntu Network Manager outlet.

The connection doesn't seem to drop if the Ubuntu PC is sitting idle. But it can happen with web surfing, Samba file transfers, or torrent downloading.

I noticed that Encore has a linux driver for my card called RT2860. It looks very difficult to install. Ubuntu automatically uses RT2800. So I don't know if this could be a driver issue. Also, shouldn't my bit rate be more than 1Mb/s? Both the router and the card are 802.11n. Are the dmesg errors something to be concerned about?



**Machine Brand and Model (PC/Laptop):** Self-built Desktop. AMD Phenom, Gigabyte motherboard
**Router Brand and Model**: Linksys Wireless-N Broadband Router	WRT160Nv2. (I already updated the firmware to the most recent version)


**Wireless Brand, Model and Wireless Chipset:** ENCORE ENLWI-N
lspci output "Network controller: RaLink RT2800 802.11n PCI"

**ifconfig output**:
```
wlan0     Link encap:Ethernet  HWaddr 00:18:e7:7b:24:04  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe7b:2404/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5397579 (5.3 MB)  TX bytes:1166358 (1.1 MB)

```

```
wlan0     IEEE 802.11bgn  ESSID:"maps"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:69:12:9F:11   
          Bit Rate=1 Mb/s   Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**lsmod output** (I think these are the relevant lines):
```
rt2860sta             559618  0 
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  2 rt2860sta,rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci

```

**dmesg output:** (could this point to the problem?)
```
[    3.536044] rt2800pci 0000:03:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.579558] Registered led device: rt2800pci-phy0::radio
[    3.579568] Registered led device: rt2800pci-phy0::assoc
[    3.579580] Registered led device: rt2800pci-phy0::quality
[    3.580252] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    3.890547] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[    3.891117] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[    3.891625] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[    3.911947] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[    4.021099] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

**lshw -C network output: **(I omitted the stuff about eth0, I'm not using it.)
```
  *-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 00
       serial: 00:18:e7:7b:24:04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.103 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fdce0000-fdceffff
```

**ifwlist output:**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:12:9F:11
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=41 dBm  
                    Encryption key:on
                    ESSID:"maps"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000023681014d
                    Extra: Last beacon: 3750ms ago
                    IE: Unknown: 00046D617073
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000700000000000000000000000000000000000000
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
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000700000000000000000000000000000000000000
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A880002369129F111021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3033104200033030371054000800060050F2040001101100114C696E6B737973205752543136304E763210080002008C103C000101]
```

**Ubuntu Version: 10.10**

**Kernel/architecture**: 2.6.35-22-generic x86_64

**etc/init.d/networking restart output:**

```

 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
```

---

### Post by galvatron408 on 2010-11-15
I have the same wifi card and HAD the same broken linksys router. I bought a netgear router to test out and everything worked really well. Perhaps, you should try another brand wireless router.

---


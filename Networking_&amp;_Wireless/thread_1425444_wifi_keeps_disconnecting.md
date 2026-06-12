---
title: "wifi keeps disconnecting"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2010-03-09
Hi,

Wifi seems to disconnect fairly requently, sometimes reconnecting automatically and sometimes requiring me to re-enter the wep password.

I would like to make it so it stays connected.

The router is not very close, but I think it's close enough. I even moved it closer. Other devices (such as my N900 mobile phone) hold the connection without issue.

One complication is that there are several devices all with the same SSID, though there should be one which is clearly stonger.

My searches have turned up several references to such problems, but no clear solutions.

Help appreciated.

Details below.

Thanks,

Max.

1 ) Machine Brand and Model (PC/Laptop):
```
Lenovo T61
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1111
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at df2fe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```

3 ) check interface:
```
wlan0     IEEE 802.11abgn  ESSID:"NRPN"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:18:F8:32:C2:EC   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:72:3c:17  
          inet addr:192.89.6.97  Bcast:192.89.6.127  Mask:255.255.255.128
          inet6 addr: 2001:2060:40:2:21f:3bff:fe72:3c17/64 Scope:Global
          inet6 addr: fe80::21f:3bff:fe72:3c17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135685 (135.6 KB)  TX bytes:10025 (10.0 KB)
```

4 ) Check for modules:
```
iwlagn                109084  0 
iwlcore               112796  1 iwlagn
mac80211              181140  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211
```

5 ) Kernel boot messages
```
[   15.650267] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   15.650271] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.650373] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.650412] iwlagn 0000:03:00.0: setting latency timer to 64
[   15.650470] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   15.704945] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   15.705097] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   16.666710] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   16.751002] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[  817.585520] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  817.868162] iwlagn 0000:03:00.0: index 0 already used in uCode key table.
[ 1507.414667] iwlagn 0000:03:00.0: PCI INT A disabled
[ 1532.764694] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 1532.764697] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 1532.764806] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1532.764841] iwlagn 0000:03:00.0: setting latency timer to 64
[ 1532.764909] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[ 1532.818142] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[ 1532.818259] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[ 1532.840432] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[ 1532.849220] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
```

6 ) Network configuration
```
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:72:3c:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.89.6.97 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:df2fe000-df2fffff
```

7 ) Scan for networks:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:32:C2:EC
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NRPN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000007130918a
                    Extra: Last beacon: 27456ms ago
                    IE: Unknown: 00044E52504E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020504
```

8 ) Ubuntu Version: 
```
Description:	Ubuntu 9.10
```

9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
2.6.31-20-generic i686
```

10 ) Restarting the network:
```
 * Reconfiguring network interfaces...                                                                                                                                             Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0.

```

---

### Post by davidmaxwaterman on 2010-03-11
No one has any idea, or did I miss some vital info?

I saw some post about installing linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic, so I tried that but it didn't make any difference.

Any clues welcome...

---

### Post by random12345 on 2010-03-11
> [  817.585520] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
Try to look in thread [_iwlagn: Microcode SW error detected. Restarting 0x82000000_]("http://ubuntuforums.org/showthread.php?t=1142917") or try to [search]("http://ubuntuforums.org/search.php?searchid=70848804") for "0x82000000", since there are more threads reporting this error.

---

### Post by davidmaxwaterman on 2010-03-12
> **random12345 said:**
> Try to look in thread [_iwlagn: Microcode SW error detected. Restarting 0x82000000_]("http://ubuntuforums.org/showthread.php?t=1142917") or try to [search]("http://ubuntuforums.org/search.php?searchid=70848804") for "0x82000000", since there are more threads reporting this error.

ok, thanks. lots of stuff, for sure. nothing's worked so far, but I'll keep looking...

most of the things I found from the above thread(s) don't seem to even apply on my system. for example :

```
$ sudo iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

and...

```
ls /sys/bus/pci/drivers/iwlagn/0000\:03\:00.0/power_level
ls: cannot access /sys/bus/pci/drivers/iwlagn/0000:03:00.0/power_level: No such file or directory

```

I have a /sys/bus/pci/drivers/iwlagn/0000\:03\:00.0/tx_power, but that just contains '15', and nothing like they give as expected contents (so I figure it's not the same thing)

and, for the microcode upgrade...

```
$ grep \"^FIRMWARE_DIR\" /etc/hotplug/firmware.agent
grep: /etc/hotplug/firmware.agent: No such file or directory

```

and I'm not that keen to get involved with customer kernels.

...but I'll keep looking, now that I know what to look for.

Thanks,

Max.

---

### Post by Braveheart1980 on 2010-11-18
Any news on this?

I also get the 0x820000 error..

---

### Post by uncaspi on 2010-11-18
I saw you had txpower. Try to increase it to 16 17 until you get an error. Also try to change the channel.
sudo iwconfig wlan0 txpower 16  channel 1

try to connect again.

---


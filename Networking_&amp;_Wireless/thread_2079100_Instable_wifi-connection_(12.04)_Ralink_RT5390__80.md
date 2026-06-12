---
title: "Instable wifi-connection (12.04): Ralink RT5390  802.11n randomly disconnects"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by MartinMichaelBetz on 2012-11-01
Hello,

I have a very annoying wifi instability. My card disconnects again and again - sometimes it helps to restart Ubuntu, sometimes I just have to wait.

Here is the logs, that might help.

$ uname -mr
```
3.5.0-17-generic x86_64
```$ lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
```$ dmesg # when wifi is disconnecting
```
[12814.053619] cfg80211: Disabling freq 2484 MHz
[12814.053625] cfg80211: Regulatory domain changed to country: DE
[12814.053628] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[12814.053632] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[12814.053636] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[12814.053640] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[12814.053644] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[13968.732427] cfg80211: All devices are disconnected, going to restore regulatory settings
```$ dmesg # 2nd failing
```

[ 1960.708379] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1960.708381] cfg80211: World regulatory domain updated:
[ 1960.708382] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1960.708383] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1960.708385] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1960.708386] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1960.708387] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1960.708389] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1961.843763] wlan0: authenticate with 1c:c6:3c:8d:5e:30
[ 1961.858883] wlan0: send auth to 1c:c6:3c:8d:5e:30 (try 1/3)
[ 1961.870615] wlan0: authenticated
[ 1961.879092] wlan0: associating with AP with corrupt beacon
[ 1961.882461] wlan0: associate with 1c:c6:3c:8d:5e:30 (try 1/3)
[ 1962.086348] wlan0: associate with 1c:c6:3c:8d:5e:30 (try 2/3)
[ 1962.290214] wlan0: associate with 1c:c6:3c:8d:5e:30 (try 3/3)
[ 1962.494137] wlan0: association with 1c:c6:3c:8d:5e:30 timed out
[ 1963.710784] wlan0: authenticate with 1c:c6:3c:8d:5e:30
[ 1963.726196] wlan0: direct probe to 1c:c6:3c:8d:5e:30 (try 1/3)
[ 1963.929361] wlan0: direct probe to 1c:c6:3c:8d:5e:30 (try 2/3)
[ 1964.133265] wlan0: direct probe to 1c:c6:3c:8d:5e:30 (try 3/3)
[ 1964.337192] wlan0: authentication with 1c:c6:3c:8d:5e:30 timed out
[ 1976.046935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```$ lsmod
```
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
i915                  520519  4 
cfg80211              206566  2 rt2x00lib,mac80211
microcode              22803  0 
eeprom_93cx6           13302  1 rt2800pci
lpc_ich                17061  0 
drm_kms_helper         46784  1 i915
drm                   275528  5 i915,drm_kms_helper
```$ iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"XYZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:C6:3C:8D:5E:30   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:16   Missed beacon:0
```$ sudo lshw -C network
```
  *-network        
       Beschreibung: Kabellose Verbindung
       Produkt: RT5390 Wireless 802.11n 1T/1R PCIe
       Hersteller: Ralink corp.
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: wlan0
       Version: 00
       Seriennummer: 08:ed:b9:6a:56:62
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=rt2800pci driverversion=3.5.0-17-generic firmware=0.34 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       Ressourcen: irq:17 memory:de800000-de80ffff
```I'm obviously based in Germany.


Do you have any advice how to get my connection more stable from these logs?

Thanks
Martin

---

### Post by chili555 on 2012-11-01
The first thing I'd look at is this:> wlan0     IEEE 802.11bgn  ESSID:"XYZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:C6:3C:8D:5E:30   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR="Red"]Link Quality=43/70[/COLOR]  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:16   Missed beacon:0Is there a setting in the router to increase transmit power? Is a different channel better? Often there is interference with other wireless devices, dimmers, etc. I have the best luck with channels 1 and 11.

Next, I'd update the driver:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.4-1-snpc.tar.bz2
cd compat-wireless-3.5.4-1-snpc
./scripts/driver-select rt2x00
make
sudo make install
```Reboot and let us have your report.

---

### Post by MartinMichaelBetz on 2012-11-01
Thank you very much for the analysis. I tried out all channels, but could not improve the quality. Also, sending power was already at 100%. I now moved the router and it is works better with one machine now - but the other one in the room next by went significantly worse. 

I think it is a combination of a not good enough router and decade old walls. I already ordered a new router, and I hope this will help.

I will keep you updated, and thanks again for the help thus far.

---


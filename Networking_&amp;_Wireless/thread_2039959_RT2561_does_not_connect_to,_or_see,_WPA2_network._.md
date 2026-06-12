---
title: "RT2561 does not connect to, or see, WPA2 network. wpa_supplicant?"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by repaxan on 2012-08-09
Heya, I've put a rt2651-chipset PCI card into my (32-bit) 12.04 Server machine so I could hide it in a corner without dragging a cable all the way across the room. It took a while to get driver issues sorted out, and now I still can't figure out why it won't connect to, or detect when scanning, my WPA2-PSK network (that uses AES, not TKIP). It does seem to see my neighbors' WEP networks just fine though.

Before, I had my wpa_supplicant use the wext driver, and it worked intermittently, bringing up the ioctl[SIOCSIWENCODEEXT] error. So I switched to using nl80211, which elsewhere online is said to work. I've seen another thread on this forum about the RT2651 chipset, but in that case they were at least able to scan.

Here's the output of a few commands, run in this order, and cropped for relevance.

**ifup -v wlan0**
```
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211 -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "theRightSSID" -- OK
wpa_supplicant: wpa-bssid 90:4c:e5:4e:3b:7f -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP -- OK
wpa_supplicant: wpa-group CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases -1 wlan0
Failed to bring up wlan0.
```

**iwlist scan**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:90:BF:20:B0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm
                    Encryption key:on
                    ESSID:"0VJ26"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b6a6141c0
                    Extra: Last beacon: 3472ms ago
                    IE: Unknown: 000530564A3236
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 02 - Address: 00:1F:90:BF:5A:68
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm
                    Encryption key:on
                    ESSID:"AZB66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002b6a670a25
                    Extra: Last beacon: 2832ms ago
                    IE: Unknown: 0005415A423636
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
```

**lspci -v**
```
02:01.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
        Subsystem: Ralink corp. EW-7108PCg
        Flags: bus master, slow devsel, latency 32, IRQ 22
        Memory at feac8000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci
```

**lshw**
```
           *-network:0
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: Ralink corp.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: wlan0
                version: 00
                serial: 48:02:2a:f0:4c:70
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci driverversion=3.2.0-27-generic-pae firmware=0.8 latency=32 link=no multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:feac8000-feacffff
```

**ifconfig**
```
wlan0     Link encap:Ethernet  HWaddr 48:02:2a:f0:4c:70
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**iwconfig**
```
wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

**dmesg** (the first line shows up every time wlan0 tries to go up, and the last four repeat)
```
[83228.609627] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[83230.813340] wlan0: direct probe to 90:4c:e5:4e:3b:7f (try 1/3)
[83231.012038] wlan0: direct probe to 90:4c:e5:4e:3b:7f (try 2/3)
[83231.212021] wlan0: direct probe to 90:4c:e5:4e:3b:7f (try 3/3)
[83231.412020] wlan0: direct probe to 90:4c:e5:4e:3b:7f timed out
```

**ifdown wlan0 -v**
```
ifdown: interface wlan0 not configured
```

---

### Post by bakegoodz on 2012-08-12
I think your issue is configuration problem. I suspect your not using the GUI Network Manager, since your talking about wpa_supplicant
Here is example configuration that works:
> 
# /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver nl80211
wpa-conf /etc/wpa_supplicant.conf
Generate wpa_supplicant.conf
```
wpa_passphrase YourSSID YourPassword > /etc/wpa_supplicant.conf
```

---

### Post by repaxan on 2012-08-12
I just commented out the wpa- sections in my /etc/network/interfaces and tried that out, to no discernible effect.

Here's what it was before, since I apparently forgot to include it.

```
auto wlan0
iface wlan0 inet dhcp
#iface wlan0 inet static
wpa-driver nl80211
wpa-ssid herp
wpa-bssid 90:4c:e5:4e:3b:7f
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk derpherp
##pre-up wpa_supplicant -Dnl80211 -B -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
##post-down pkill wpa_supplicant
#address 192.168.0.14
#netmask 255.255.255.0
#network 192.168.0.0
#broadcast 192.168.0.255
#gateway 192.168.0.1
#dns-nameservers 4.2.2.3 8.8.4.4
```

---

### Post by bakegoodz on 2012-08-12
Interesting problem. Let's see more of dmesg and see if the firmware files are there.
```

ls -lh /lib/firmware/rt25*
dmesg | tail -n 60
```

---

### Post by repaxan on 2012-08-12
Firmware:
```
-rw-r--r-- 1 root root 8.0K Feb 23 11:07 /lib/firmware/rt2561.bin
-rw-r--r-- 1 root root 8.0K Feb 23 11:07 /lib/firmware/rt2561s.bin
```

I went ahead and rebooted the box so dmesg wasn't just full of "direct probe timed out".
```
[    9.716811] cfg80211: Calling CRDA to update world regulatory domain
... (nouveau driver)
[   10.930015] intel8x0_measure_ac97_clock: measured 65202 usecs (3140 samples)
[   10.930020] intel8x0: clocking to 48000
[   11.051675] cfg80211: World regulatory domain updated:
[   11.051683] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.051688] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.051692] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.051697] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.051701] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.051705] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.079156] No connectors reported connected with modes
[   11.079169] [drm] Cannot find any crtc or sizes - going 1024x768
[   11.079974] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x49000, bo eb97e600
[   11.080496] fbcon: nouveaufb (fb0) is primary device
[   11.081621] Console: switching to colour frame buffer device 128x48
[   11.082743] fb0: nouveaufb frame buffer device
[   11.082746] drm: registered panic notifier
[   11.082764] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   11.124616] rt61pci 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.132593] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.132601] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132605] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.132610] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132614] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.132618] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132622] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.132626] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132630] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.132634] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132637] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.132642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132645] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.132650] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132654] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.132659] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132663] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.132667] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132670] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.132674] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132677] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.132681] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.132685] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   11.132689] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.132692] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   11.132696] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.132699] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   11.132704] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.198084] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.199826] Registered led device: rt61pci-phy0::radio
[   11.199992] Registered led device: rt61pci-phy0::assoc
[   11.485591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by bakegoodz on 2012-08-13
I have to admit that I pretty much lost on your problem. I did notice that CRDA does restrict you to 20 MHZ channels, which pretty normal, but maybe your router is set to use 40 Mhz channels (which is 2 standard channels)
Here is my routers settings.
[IMG]http://i50.tinypic.com/2hqsawi.jpg[/IMG]

---

### Post by repaxan on 2012-08-13
My router doesn't support 802.11n, so that can't be the problem.

Anyhow, thanks for helping. Could this be a hardware issue? I'm thinking probably not, since it did sporadically work with the wext driver.

---


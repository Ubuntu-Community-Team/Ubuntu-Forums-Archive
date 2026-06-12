---
title: "Wireless Netwrok stopped after upgrad from 10.10 to 11.04"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by mytinytown on 2011-05-10
I did the lspci -v and got:
```

02:00.0 Network controller: Ralink corp. Wireless PCI Adapter RT2400 / RT2460
            Subsystem: Accton Technology Corporation Device ee07
            Flags: bus master, slow devsel, latency 64, IRQ 9
            Memory at 24000000 (32-bit, non-prefetchable) [size=8K]
            Capabilities: [40] Power Management version 2
            Kernel driver in use: rt2400pci
            Kernel modules: rt2400pci

```

ifconfig shows:
```

eth0      Link encap:Ethernet  HWaddr 08:00:46:59:80:c0
          inet addr:192.168.2.40  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe59:80c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:348783 (348.7 KB)  TX bytes:65288 (65.2 KB)
          Interrupt:10 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:04:e2:d6:f7:2c
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:04:e2:d6:f7:2c
          inet addr:169.254.10.3  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```iwconfig:
```

wlan0     IEEE 802.11b  ESSID:""E******P""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:*******
          Power Management:off

```Wired Network works fine, but in the Desktop under Wireless Networks it  shows "device not managed". I am using a SMC EZ Connect model SMC2635W  and the Link/Act light is on.

Worked perfectly with Ubuntu 10.10, when I  did the "do-release-upgrade" when it rebooted after being finished  Wireless was dead.

---

### Post by Erik-Jan on 2011-05-10
My wireless worked perfectly on 10.10, but after I upgrade to Natty my wireless stopped working. All the rest is fine (and better!). I am using a Dell Latitude E6510 and the 32-bit Desktop version of Natty.

Here's the relevant output of lspci -v:

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Dell Device 0010
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f4100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-c4-ff-ff-0c-68-a3
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, brcm80211

Any ideas?

---

### Post by mytinytown on 2011-05-10
OK This is silly.

My issue was I had some information in the /etc/network/interface file and once I removed all that, only having the auto lo info, it cleared up all issues with the wireless.

---

### Post by josephmills on 2011-05-10
> **Erik-Jan said:**
> My wireless worked perfectly on 10.10, but after I upgrade to Natty my wireless stopped working. All the rest is fine (and better!). I am using a Dell Latitude E6510 and the 32-bit Desktop version of Natty.

Here's the relevant output of lspci -v:

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Dell Device 0010
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f4100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-c4-ff-ff-0c-68-a3
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, brcm80211

Any ideas?

please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5) hope this helps

---


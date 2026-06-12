---
title: "Wirelss Connection fails in Ubuntu 12.04 (after last few updates)"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by Nirmalya on 2012-12-09
Hello all,

This is quite a common problem, it seems from the number of posts on the topic on here in this forum and elsewhere. To cut a long story short, 

[LIST]
[*]My Ubuntu 12.04-based laptop has stopped recognising the Belkin N150 router, all of sudden a couple of weeks back.
[*]My wife's netbook works with the same router unchanged.  So, it is unlikely to be a problem with the router.
[*]I have been using 'wicd' without any trouble for almost an year now. However, now 'wicd' catches signals from the routers of my neighbours :), but is blissfully unaware of the router in my residence.
[*]I searched and experimented (spent an awful number of hours) with advices given on a number of such posts but of no avail.
[/LIST]
Being used to wireless networking on Ubuntu and then, having to live without it is a great source of irritation and impatience. Can someone please point me out to the right direction? What mistake I am making?

Here are the necessary information (anything else  needed, please let me know):

**My Machine**: Samsung Laptop RV 409
[B]My Env:
[/B]([COLOR=Blue]*uname -a*[/COLOR]):  
Linux Solomon 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:49:02 UTC 2012 i686 i686 i386 GNU/Linux
*([COLOR=Blue]lsb_modules -a[/COLOR])*:  
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

**Contents of */etc/network/interfaces***:

```

auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

auto eth0
iface eth0 inet manual

```[B]

Output of *ifconfig*[/B] (right now):

```

eth0      Link encap:Ethernet  HWaddr e8:11:32:48:26:d5  
          inet6 addr: fe80::ea11:32ff:fe48:26d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15094642 (15.0 MB)  TX bytes:2806957 (2.8 MB)
          Interrupt:41 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr b4:74:9f:83:b5:94  
          inet6 addr: fe80::b674:9fff:fe83:b594/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:13670
          TX packets:0 errors:26 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18218 (18.2 KB)  TX bytes:18218 (18.2 KB)

```**Output of *lshw -C network***:

```
 *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: b4:74:9f:83:b5:94
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fc500000-fc503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:48:26:d5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:fc900000-fc900fff memory:fca04000-fca07fff

```**Output of *lsmod*** ***| grep b43***:
```
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43

```** Output of *lspci -nn | grep 0280***:
```

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```**Output of *rfkill list all***:
```

0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```**Contents of */etc/wpa_supplicant.conf***:

```

ap_scan=1
network={
            ssid=<Name given by me>
             psk=<Password given by me>
}

```**Output of *nm-tool***:
```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        E8:11:32:48:26:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        B4:74:9F:83:B5:94

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    <XXXXXX1>: Infra, 00:24:82:26:59:68, Freq 2412 MHz, Rate 0 Mb/s, Strength 29
    <XXXXXX2>:      Infra, 00:25:9C:18:6B:0C, Freq 2422 MHz, Rate 0 Mb/s, Strength 12 WPA WPA2
    <XXXXX3>:           Infra, B8:A3:86:2E:8E:5E, Freq 2462 MHz, Rate 0 Mb/s, Strength 25 WPA WPA2


```

Please note: _None_ of the above-mentioned XXXXX9 values contains the_ SSID name_ that I  had set in '/etc/wpa_supplicant.conf' file, referred to before in this post.



**Output of *iwconfig***:
```

ppp0      no wireless extensions.

lo        no wireless extensions.

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:72 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```**Output of *iwspy***:

```

ppp0      Interface doesn't support wireless statistic collection

lo        Interface doesn't support wireless statistic collection

eth1      No statistics to collect

eth0      Interface doesn't support wireless statistic collection


```Not sure if this is going to be useful, but just in case -->

**Output of '*cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55*'**:

```

Dec 10 07:47:57 Solomon vnstatd[1695]: Monitoring: eth1 eth0 
Dec 10 07:47:57 Solomon vnstatd[1695]: Error: Unable to get interface "eth1" statistics.
Dec 10 07:47:57 Solomon vnstatd[1695]: Interface "eth1" not available, disabling.
Dec 10 07:52:31 Solomon kernel: [   21.645520] wl: module license 'MIXED/Proprietary' taints kernel.
Dec 10 07:52:31 Solomon kernel: [   21.654366] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 10 07:52:31 Solomon kernel: [   21.654375] wl 0000:02:00.0: setting latency timer to 64
Dec 10 07:52:31 Solomon kernel: [   21.798201] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): using WEXT for WiFi device control
Dec 10 07:52:32 Solomon NetworkManager[924]: <error> [1355106152.46792] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): now managed
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): bringing up device.
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): preparing device.
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): deactivating device (reason 'managed') [2]
Dec 10 07:52:32 Solomon dbus[886]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 10 07:52:32 Solomon dbus[886]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> wpa_supplicant started
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): supplicant interface state: starting -> ready
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 10 07:52:32 Solomon NetworkManager[924]: <info> (eth1): supplicant interface state: ready -> inactive
Dec 10 07:52:35 Solomon vnstatd[1661]: Monitoring: eth1 eth0 
Dec 10 07:52:40 Solomon vnstatd[1661]: Interface "eth1" enabled.
Dec 10 08:02:18 Solomon kernel: [   21.414315] wl: module license 'MIXED/Proprietary' taints kernel.
Dec 10 08:02:18 Solomon kernel: [   21.429825] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 10 08:02:18 Solomon kernel: [   21.429836] wl 0000:02:00.0: setting latency timer to 64
Dec 10 08:02:18 Solomon kernel: [   21.543937] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38
Dec 10 08:02:18 Solomon NetworkManager[970]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth1, iface: eth1)
Dec 10 08:02:18 Solomon NetworkManager[970]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 10 08:02:18 Solomon NetworkManager[970]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 10 08:02:18 Solomon NetworkManager[970]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth1/rfkill0) (driver (unknown))
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): using WEXT for WiFi device control
Dec 10 08:02:19 Solomon NetworkManager[970]: <error> [1355106739.13015] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): now managed
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): bringing up device.
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): preparing device.
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): deactivating device (reason 'managed') [2]
Dec 10 08:02:19 Solomon dbus[917]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 10 08:02:19 Solomon dbus[917]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> wpa_supplicant started
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): supplicant interface state: starting -> ready
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 10 08:02:19 Solomon NetworkManager[970]: <info> (eth1): supplicant interface state: ready -> inactive
Dec 10 08:02:20 Solomon avahi-daemon[981]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::b674:9fff:fe83:b594.
Dec 10 08:02:20 Solomon avahi-daemon[981]: New relevant interface eth1.IPv6 for mDNS.
Dec 10 08:02:20 Solomon avahi-daemon[981]: Registering new address record for fe80::b674:9fff:fe83:b594 on eth1.*.
Dec 10 08:02:21 Solomon vnstatd[1692]: Monitoring: eth1 eth0


```I had installed '**b43fwcutter**' through  synaptic.

I tried to install 'firmware-b43-lpphy' too, but was left with a reassurance:
**Output of *apt-get install firmware-b43-lpphy-installer***:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-lpphy-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```Any other information, I am just a mail away.

Any help will be appreciated wholeheartedly. I am quite OK with linux command line tools. So, feel free to ask me to run any command and I will share the output, if that helps you.

Let us nail this problem down. This is causing a lot of heartburn around in the Ubuntu circles. We can't possibly ask anyone to keep working with wired connection till this is solved. This is caused by a recent update for sure, and we will have to provide a fix ASAP.  The world isn't going to wait for us. :sad:

---


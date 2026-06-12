---
title: "Cannot Get Wireless Access"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by Existing_Account on 2011-04-11
Just installed Ubuntu 10.10 on my Vostro 1520, replacing a non-functional Vista OS.

I'm currently connected via ethernet cable but would really prefer not to have to be.

My Network Manager Applet 0.8.1 when moused over displays "networking disabled". Left-click yields "No network devices are available". Right-clicking shows the option to enable networking but it's blacked out.

lshw -c net yields the following:

> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:d7:79:10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.17 latency=0 multicast=yes
       resources: irq:46 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:82:9e:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A multicast=yes wireless=IEEE 802.11bgSometimes wlan0 comes up with:
> *-network DISABLEDbut currently my network light is on and appears to be active. This is not for any explainable reason (no, I haven't disabled it with a Dell key combination or manual switch). Regardless, I cannot enable wireless networking.

I have used system>admin>Additional Drivers and downloaded Broadcom B43 wireless driver which is specifically for my BCM4312 (with Low-Power aka LP-PHY).

In network tools, my wireless interface information shows state as active.

I have downloaded the WiFi Radar application. It, when the wireless light is on, can see my home network with four bars. Attempts to connect to this result in my staring endlessly at a window reading "Acquiring IP Address (DHCP)". No data transmission shows with the wireless device in the network tools window.

I downloaded a package giving me "Indicator Applet 0.4.6". See below:

[[IMG]http://img827.imageshack.us/img827/7755/screenshotwoo.png[/IMG]]("http://img827.imageshack.us/i/screenshotwoo.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

This is the weird one, possibly wherein my problem lies. In response to nm-tool, my terminal gives me:

> ** (process:2624): WARNING **: _nm_object_get_property: Error getting 'WirelessHardwareEnabled' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (process:2624): WARNING **: _nm_object_get_property: Error getting 'WwanHardwareEnabled' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (process:2624): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



NetworkManager Tool


** (process:2624): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


State: unknown


** (process:2624): WARNING **: error: could not connect to NetworkManager
Hope I've included the important detail. Any assistance will be appreciated, moreso if soon and helpful. :)

---

### Post by Existing_Account on 2011-04-12
Upon removal of the package for the indicator applet (indicator-network), my wireless light goes off but access to network manager is restored. Thus, nm-tool responds:

> NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:D7:79:10

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:26:5E:82:9E:D5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


---

### Post by Existing_Account on 2011-04-12
Network Manager Applet now looks like this:

[[IMG]http://img191.imageshack.us/img191/2020/screenshot0js.png[/IMG]]("http://img191.imageshack.us/i/screenshot0js.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

And lshw -c net once again gives:

> ...

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:82:9e:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg


---

### Post by Existing_Account on 2011-04-12
I'm now attempting to establish connection both with the broadcom device and with a Netgear USB device I found under my desk. Regardless of whether deemed enabled/disabled or active/inactive, network manager still insists that wireless is disabled and "Enable Wireless" remains blacked out.

---

### Post by mettlewk on 2011-04-13
my problem resolved

---


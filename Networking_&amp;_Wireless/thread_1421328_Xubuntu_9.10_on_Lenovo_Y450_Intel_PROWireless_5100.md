---
title: "Xubuntu 9.10 on Lenovo Y450 Intel PRO/Wireless 5100 AGN wireless disabled"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by flaregunhobo on 2010-03-04
I have turned on the wlan on the bios, no light on the wireless indicator and NetworkManager says that wireless is disabled. My wireless interface name is wlan0. Kernel version 2.6.31-19-generic i686

Here are my wireless info:

```

$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 00
       serial: 00:26:c6:66:1f:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f4100000-f4101fff

```
```

$ lspci | grep Network
06:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

``````

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:80:93:91  
          inet addr:192.168.22.11  Bcast:192.168.22.255  Mask:255.255.255.0
          inet6 addr: 2001:da8:207:f010:226:9eff:fe80:9391/64 Scope:Global
          inet6 addr: fe80::226:9eff:fe80:9391/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24541 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27620747 (27.6 MB)  TX bytes:3037723 (3.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2982237 (2.9 MB)  TX bytes:2982237 (2.9 MB)

``````

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:c6:66:1f:b8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B

``````

$ lsmod | grep "iwlagn"
iwlagn                109052  0 
iwlcore               112796  1 iwlagn
mac80211              181140  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211

``````

$ dmesg | grep iwlagn
[   13.569362] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.569365] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.569468] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.569529] iwlagn 0000:06:00.0: setting latency timer to 64
[   13.569586] iwlagn 0000:06:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.708028] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.708111] iwlagn 0000:06:00.0: irq 34 for MSI/MSI-X

``````

$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

``````

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 1240
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:26:c6:66:1f:b8
Sending on   LPF/wlan0/00:26:c6:66:1f:b8
Sending on   Socket/fallback
Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Unknown error 132
SIOCSIFFLAGS: Unknown error 132
Listening on LPF/wlan0/00:26:c6:66:1f:b8
Sending on   LPF/wlan0/00:26:c6:66:1f:b8
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
send_packet: Network is down
^C

``````

$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```Sorry for a long wall of code. I cannot access another OS and Xubuntu is my only option. Thanks

---

### Post by Fire_Chief on 2010-03-04
There's a hardware switch on the front of your Lenovo for enabling the wireless and bluetooth (if equipped) functions. Make sure it is switched to the on position (to the right I think).

Cheers!

---

### Post by flaregunhobo on 2010-03-04
i forgot to mention the switch was on haha

---

### Post by Mizzery85 on 2010-11-15
I have an HP 2540p that im having the same issue with, but I have the Intel Advanced-N 6200 AGN. I have the power switch on, but its still saying its powered off.

Any help would be awesome.

---

### Post by jeslinmx on 2010-12-07
it seems that when you flick the switch to off it shuts the wifi down on 2 levels. turning the switch back to on fails to wake the wifi because it turns on one of these levels. it seems that the only thing that can enable the second level is lenovo's own power management program, which is windows only. so until someone comes up with a linux utility which can duplicate this behavior, you have to switch to windows and turn on the wifi everytime you change the switch to on.

---

### Post by jeslinmx on 2010-12-07
btw, i will be interested to know if lenovo energy management works on wine or vbox.

---

### Post by NexusN on 2011-01-06
Try to reset the BIOS and this should be fixed.
This is a known issue on this laptop( no idea for other devices), 
when you have an OS without power management installed, 
you will forever shutdown the wireless device by turning off the hard switch of wireless device on the front and restarting the machine.
Resetting BIOS saved me.

If still not working, you will need a power management installed vista/7 to enable the wireless device.

---


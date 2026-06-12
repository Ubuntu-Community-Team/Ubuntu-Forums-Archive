---
title: "Intel pro/wireless 2200bg internet/ping problem"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by tacer on 2013-03-12
Hello,
I become Ubuntu member just 2 days ago, and discover problem with wireless connection
First I google  for it,but didn't find a solution
Situation is: I can connect to my hidden  WIFI with WPA2 personal, got IP and then stuck-I even can't ping router!!!
so here is my terminal

```
igor@ubuntu:~$ nm-tool
NetworkManager Tool
State: connected (global)
- Device: eth1  [Igor_kv36]----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        00:0E:35:80:D5:E4
  Capabilities:
    Speed:           54 Mb/s
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = currentAP)
    sous:            Infra,10:BF:48:91:64:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
**    *Igor_kv36:      Infra,50:46:5D:0D:AA:24, Freq 2417 MHz, Rate 54 Mb/s, Strength 94 WPA2 my network**
    M2ob:            Infra,00:15:6D:10:60:56, Freq 0 MHz, Rate 54 Mb/s, Strength 49
    ZyXEL:           Infra,50:67:F0:17:7D:3E, Freq 0 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Ludmila_kv27:    Infra,64:70:02:65:54:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ASUS:            Infra,F4:6D:04:8D:00:5C, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA2
  IPv4 Settings:
    Address:         192.168.12.205
    Prefix:          24(255.255.255.0)
    Gateway:         192.168.12.1
    DNS:             192.168.12.1
- Device: eth0-----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unmanaged
  Default:           no
  HW Address:        00:0B:5D:51:52:A5
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
  Wired Properties
    Carrier:         onState:connected (global)
- Device: eth1  [Igor_kv36]----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        00:0E:35:80:D5:E4
  Capabilities:
    Speed:           54 Mb/s
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = currentAP)
    sous:            Infra,10:BF:48:91:64:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
***    *Igor_kv36:      Infra,50:46:5D:0D:AA:24, Freq 2417 MHz, Rate 54 Mb/s, Strength 94 WPA2***
    M2ob:            Infra,00:15:6D:10:60:56, Freq 0 MHz, Rate 54 Mb/s, Strength 49
    ZyXEL:           Infra,50:67:F0:17:7D:3E, Freq 0 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Ludmila_kv27:    Infra,64:70:02:65:54:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ASUS:            Infra,F4:6D:04:8D:00:5C, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA2
  IPv4 Settings:
    Address:         192.168.12.205
    Prefix:          24(255.255.255.0)
    Gateway:         192.168.12.1
    DNS:             192.168.12.1
- Device: eth0-----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unmanaged
  Default:           no
  HW Address:        00:0B:5D:51:52:A5
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
  Wired Properties
    Carrier:         on
```

```
igor@ubuntu:~$ ^C
igor@ubuntu:~$ 

igor@ubuntu:~$ sudo modprobe ipw2200
[sudo] password for igor: 

igor@ubuntu:~$ sudo su
root@ubuntu:/home/igor# echo ipw2200 
ipw2200
\root@ubuntu:/home/igor# /etc/modules
bash: /etc/modules: Permission denied
root@ubuntu:/home/igor# exit
exit
```

```
igor@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
igor@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek SemiconductorCo., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:0b:5d:51:52:a5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_mastercap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fdautonegotiation
       configuration:autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28duplex=half ip=192.168.12.220 latency=64 link=no maxlatency=64mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11ioport:3000(size=256) memory:d0200000-d02000ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG[Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:80:d5:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_mastercap_list ethernet physical wireless
       configuration: broadcast=yesdriver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 122007) ip=192.168.12.205 latency=64 link=yes maxlatency=24 mingnt=3multicast=yes wireless=IEEE 802.11bg
       resources: irq:11memory:d0201000-d0201fff
```
 
```
igor@ubuntu:~$ lspci -nn | grep 2200
01:0d.0 Network controller [0280]:Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection[8086:4220] (rev 05)
```

```
igor@ubuntu:~$ ls -al /lib/firmware |grep ipw
-rw-r--r--  1 root root  209190 Jul 20 2012 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Jul 20 2012 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Jul 20 2012 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Jul 20 2012 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Jul 20 2012 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Jul 20 2012 ipw2200-sniffer.fw
```

```
igor@ubuntu:~$ dmesg | grep ipw
[   26.118686] libipw: 802.11data/management/control stack, git-1.1.13
[   26.118694] libipw: Copyright (C)2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.227324] ipw2200: Intel(R)PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.227333] ipw2200: Copyright(c)2003-2006 Intel Corporation
[   26.227501] ipw2200 0000:01:0d.0:PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   26.227533] ipw2200: Detected IntelPRO/Wireless 2200BG Network Connection
[   27.221856] ipw2200: Radio FrequencyKill Switch is On:
[   27.259470] ipw2200: Detectedgeography ZZM (11 802.11bg channels, 0 802.11a channels)
[   30.588041] ipw2200: Failed to sendPOWER_MODE: Command timed out.
[   34.716050] ipw2200: Failed to sendPOWER_MODE: Command timed out.
[ 3846.231259] ipw2200: Firmware errordetected.  Restarting.
[ 4870.656065] ipw2200: Failed to sendPOWER_MODE: Command timed out.
[ 5788.260196] ipw2200: Failed to sendCARD_DISABLE: Command timed out.
```

```
igor@ubuntu:~$ nm-tool
NetworkManager Tool
State: connected (global)
- Device: eth1  [Igor_kv36]----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        00:0E:35:80:D5:E4
  Capabilities:
    Speed:           54 Mb/s
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = currentAP)
    sous:            Infra,10:BF:48:91:64:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    *Igor_kv36:      Infra,50:46:5D:0D:AA:24, Freq 2417 MHz, Rate 54 Mb/s, Strength 84 WPA2
    Ludmila_kv27:    Infra,64:70:02:65:54:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    M2ob:            Infra,00:15:6D:10:60:56, Freq 0 MHz, Rate 54 Mb/s, Strength 49
    ASUS:            Infra,F4:6D:04:8D:00:5C, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA2
  IPv4 Settings:
    Address:         192.168.12.205
    Prefix:          24(255.255.255.0)
    Gateway:         192.168.12.1
    DNS:             192.168.12.1
- Device: eth0-----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unmanaged
  Default:           no
  HW Address:        00:0B:5D:51:52:A5
  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s
  Wired Properties
    Carrier:         off
```

---


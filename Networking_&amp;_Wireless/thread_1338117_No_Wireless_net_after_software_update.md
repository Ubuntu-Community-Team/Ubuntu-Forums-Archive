---
title: "No Wireless net after software update"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by barneystroud on 2009-11-26
Hi,

I had Karmic working quite well until today; I got a software update for ubuntu and after restarting I have no wireless internet connection. 

I've already re-istalled ubuntu 9.10 five times because of this; does anybody know what's going on?

Why is 9.10 so bad?

---

### Post by coffeeaddict22 on 2009-11-26
Hi Barney,
Sounds like a driver issue possibly.  Sometimes they get upgraded, and there can be problems.  Were you using ndiswrapper previously?
Can you post the output of ```
lshw -C network
nm-tool
``` (2 separate commands); that should help localise the problem a little.

---

### Post by barneystroud on 2009-11-26
mark@mark-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8f:11:1f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.7 latency=0 multicast=yes
       resources: irq:58 ioport:4000(size=256) memory:d0500000-d0500fff memory:d0200000-d020ffff(prefetchable) memory:d0220000-d023ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:f1:f6:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.5 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:59 memory:d0400000-d0401fff
mark@mark-laptop:~$

---

### Post by barneystroud on 2009-11-26
mark@mark-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:90:F5:8F:11:1F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: wlan0  [Auto Belkin_N_ADSL_7B8527] -----------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           no
  HW Address:        00:16:EA:F1:F6:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Belkin_N_ADSL_7B8527: Infra, 00:22:75:7B:85:27, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    DLINK:           Infra, 00:1B:11:3F:E4:30, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA2
    BigPond6017:     Infra, 00:1E:C7:AF:CA:F1, Freq 2412 MHz, Rate 54 Mb/s, Strength 58 WPA

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


mark@mark-laptop:~$

---

### Post by barneystroud on 2009-11-26
Hey Coffee, is that right mate?

---

### Post by xifer on 2009-11-26
Which do you want to use to connect to the internet wireless or wired?

They are both on the same subnet, both with the same gateway so your system is confused.  

Pull the wire and restart xserver.  If you want to use both wired AND wireless at the same time maybe set a wired manual config in /etc/network/interfaces and leave wireless config
to the networkmanager.

That's how I have my setup - xp box with autowireless runs an xserver.
Connects by cable to my linux box which also has autowireless

both have manual wired config on a DIFFERENT subnet.  Then I can ssh from xp to unix
and have open internet access while my xp box is vpn'd to my office network.

---


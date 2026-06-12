---
title: "Wireless Blues"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by nanabead on 2010-05-12
Hi all, just after downloading Ubuntu onto my ageing laptop and my wireless internet will not switch on. Followed some links on here and used info to get this from my laptop.

colin@ubuntu:~$ nm
nm: 'a.out': No such file
colin@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:16:D4:33:36:59

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:14:A5:B4:4A:9D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


colin@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:16:d4:33:36:59
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5788-v3.26 latency=64 mingnt=64 multicast=yes
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0010000-d0011fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:b4:4a:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
colin@ubuntu:~$ 

Can somebody pont me in he right direction as to how I can activate my wireless card in my laptop?

I look forward to your replies. :)

---

### Post by chili555 on 2010-05-12
Can you walk that aging laptop over to the router and hook up the ethernet cable and get a connection and then go to System > Administration > Hardware Drivers and install the Broadcom wireless driver? After a reboot, you will not have to sing those down and dirty wireless blues.

---

### Post by nanabead on 2010-05-12
ty for your reply Chilli,

I had just come across the two drivers after posting my problem and after rebooting my wireless is up and running.......whoooopeee :)

once again ty for your reply.


CJC

---


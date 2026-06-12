---
title: "My network stopped working - NetworkManager disappeared"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by corujask8 on 2010-10-28
Hello, I have a notebook Dell Vostro 1000 dual boot with Ubuntu 10.04 and it was running ok on my machine until a forced shutdown, after that, the NetworkManager icon does not appear and the computer doesn't connect anymore. Searching the settings, I found the command that the system uses to start the NM and typed in the terminal and it shows:

Code:

```
eutiquio@eutiquio-laptop:~$ nm-applet --sm-disable
Uma instância do nm-applet já está em execução. ((means that An instance of nm-applet is already running))

** (nm-applet:2306): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```


Anyone knows who is this "D-Bus manager"?
Since I was posting, also took lshw and the nm-tool, here they are:

Code:
```
eutiquio@eutiquio-laptop:~$ sudo lshw -C network
[sudo] password for eutiquio: 
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth2
       version: 01
       serial: 00:1c:26:3a:f6:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:b0200000-b0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:9d:d4:c2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:b0300000-b0301fff
```

And:

```
eutiquio@eutiquio-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:1C:26:3A:F6:50

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ChorinhoPraEle:  Infra, 00:21:04:11:84:9F, Freq 2437 MHz, Rate 0 Mb/s, Strength 100 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unmanaged
  Default:           no
  HW Address:        00:1C:23:9D:D4:C2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on
```

If anyone can help me, I thank very much, because XP already was damaged and I'm accessing from a live cd of a 9.10 edition ;I'm suffering! ;-)

---

### Post by dineshs on 2010-10-28
Updates may cause NM icon to disappear.Try this
Right click on the top panel-click add to panel-select [COLOR="Blue"]notification area[/COLOR] -click add
Other links
[http://ubuntuforums.org/showthread.php?t=1545744](http://ubuntuforums.org/showthread.php?t=1545744) 
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217) 
(post #3 try [COLOR="Blue"]sudo[/COLOR] before commands)
[http://ubuntuforums.org/showthread.php?p=9631393#post9631393](http://ubuntuforums.org/showthread.php?p=9631393#post9631393)

---

### Post by corujask8 on 2010-10-31
Thanks, but I've had tried all that methods before, but nothing happens... If someone have any more ideas, please, tell me :)

---


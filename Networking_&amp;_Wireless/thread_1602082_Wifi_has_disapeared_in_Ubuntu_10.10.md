---
title: "Wifi has disapeared in Ubuntu 10.10"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by kliffs on 2010-10-21
hello, 
I did a fresh install of Ubuntu 10.10 this weekend and it worked great. But yesterday night i flipped on my laptop and could not get on to wifi. When i right click there is no Enable wireless option. It is as if Ubuntu doesn't even know that i have wireless. Why would it stop working after a few days?

Either way I am at a complete loss at where to begin fixing this. I would be willing to do a new install but the live CD has the same problem now however it didn't the first time i instaled it:confused::confused::confused::confused::confused::confused:. When i boot into my vista partition it works fine so it isn't a hardware problem.

I appreciate any help i can get at this point.

Thanks

---

### Post by Julie Caroline on 2010-10-21
Hi Kliffs,

I was about to post the same problem. I'm not able to activate wifi via ubuntu pannel (it's activate on my laptop through the wifi button) : 
[IMG]http://chili.ssji.net/photos/screenShots/bm4312-1010.png[/IMG]

It doesn't work with live 10.10 either. It worked fine with 10.04 and 9.10.

Here some info : 

hardware : vostro 1720, wifi card BCM*4312, bios A02.

juw@biggeorges:~$ sudo getSystemId
```
Libsmbios version:      2.2.26
Product Name:           Vostro 1720
Vendor:                 Dell Inc.
BIOS Version:           A02
System ID:              0x02C0
Service Tag:            CX3PPK1
Express Service Code:   28123010209
Asset Tag:              
Property Ownership Tag: 
```

juw@biggeorges:~$ uname -r -m
```
2.6.35-22-generic x86_64
```
juw@biggeorges:~$ lspci | grep -i net
```
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```
juw@biggeorges:~$ sudo lshw -C network
 ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:d6:95:bc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.109 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:47 ioport:4000(size=256) memory:fe004000-fe004fff memory:fe000000-fe003fff memory:fe020000-fe03ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth2
       version: 01
       serial: 00:26:5e:82:7f:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f6000000-f6003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

juw@biggeorges:~$ iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.
```
juw@biggeorges:~$ nm-tool 
```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:D6:95:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.109
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.2

    DNS:             212.27.40.241
    DNS:             212.27.40.240


- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        00:26:5E:82:7F:42

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```



BTW, I m using a classic RJ45 to be connected, waiting for more info and trying everything I could.

---

### Post by MrHighTech on 2010-11-17
Good news people

Upgrade the bios to A08 and the problem is fixed :)
Drop me a line if you need help upgrading the bios.

*happy on wireless*

---

### Post by MaikoID on 2011-01-15
Hi i`ve the same issue but i`ve the [HP Pavilion dv2715nr Entertainment Notebook PC]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&softwareitem=ob-52936-1&os=2093&product=3646852&sw_lang=&") but i don`t now how to update my bios. Can you help me with that ? i've tried everything that I found on google =|

bye

---

### Post by pretty_whistle on 2011-01-16
Interesting and weird.  I 'had' the same thing as the 1st person here but it was solved by updating Ubuntu.  I have Ubuntu 10.10 btw.

Although I have a new wifi issue which I've posted elsewhere so I'll not hijack this thread for it.

Just thought I'd let you know about updating solving that issue for me.  Hope that helps ya.

---

### Post by Sef on 2011-01-16
Press F2. Had a similar problem. For some reason, my wireless was cut off, and that was the solution for me.

---


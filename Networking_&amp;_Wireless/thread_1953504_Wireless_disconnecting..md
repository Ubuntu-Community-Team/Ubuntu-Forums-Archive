---
title: "Wireless disconnecting."
date: 2012-04-06
forum: Networking &amp; Wireless
---

### Post by olakunle on 2012-04-06
Hi all,

I'm pretty new to Ubuntu and just decided to use it for my school project. After formatting my Windows OS and installing Ubuntu (latest version), I am having problems with the wireless.

I am using a Broadcom BCM4322 in-built wireless card. When I connect to other wireless networks outside it works fine... but when I connect to the one at my home, the connection breaks all the time.

I installed wicd but it just didnt connect as it kept saying "Bad Password" when I tried connecting (This same netowrk key and network security "WPA" worked perfectly on Network manager). I'm back to Network Manager but the connection still keeps breaking.

What do I do?
PS: I have tried all solutions I could find from your forums..

Output from nm-tool

```

State: connected (global)

- Device: eth2  [SKY40D7B] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:21:00:73:94:4F

  Capabilities:
    Speed:           78 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Thomson018BA0-Tesco Broadband: Infra, 00:26:4D:01:8B:A0, Freq 2462 MHz, Rate 0 Mb/s, Strength 19 WPA WPA2
    *SKY40D7B:       Infra, F8:D1:11:AA:05:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    SKY40D7B:        Infra, C8:CD:72:94:0D:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:23:8B:5D:0A:A2

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```

Output from sudo lshw -C network 
```

*-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:73:94:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.4 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:91100000-91103fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:5d:0a:a2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:91010000-91010fff memory:91000000-9100ffff memory:91020000-9102ffff

```

---

### Post by Moople on 2012-04-06
Do you have any media that your Ubuntu install files are stored on?

It's simple to do if you have that..

1. Open up your Terminal and Media.
2. In the media go to /pool/main/
3. Go to the /p/patch/ directory.
4. Type in the terminal (keep it open!) sudo dpkg -i *deb file in the dir here*
5. Then do 2 again, and for 3 go to the d directory and dkms.
6. Do 4 again with the package in that dir.
7. Do 5 again but with the directory /f/fakeroot/
8. Do 6 with the package in THAT dir.
9. Do 2 but go to /pool/restricted/b/bcmwl/
10. Install the package there with 4.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I got that from there! That's how I'm on Ubuntu currently!

Go to the STA - Offline section.

Restart your computer! Bingo! No need for wicd..

---

### Post by olakunle on 2012-04-07
thanks a lot, tried that...

When I restarted I had to stop shorewall cos it doesnt allow me connect to the Internet, after that I started Google Chrome and the connection was still breaking.

After I closed that, I decided to use Mozilla and this is about 30 mins after and no loss in connection.

Any idea why this may be happening?

---

### Post by Moople on 2012-04-10
Shorewall is the problem here. Funnily, my connection works fine without breaking at all on Google Chrome or Mozilla.

Try the following:

1. Reset the wireless connection.
2. Uninstall shorewall.
3. Install EVERYTHING I told you to install.
4. Tell me what type of computer you have.

---


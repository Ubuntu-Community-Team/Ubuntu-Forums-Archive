---
title: "NM-connects, no icon, no choice of wireless"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by kolibri on 2010-09-15
I'm having a lot of problems connecting an ancient Toshiba Protege 3500 to my wireless.

First- clean installation of Ubuntu 10.04, with default network manager installed, I had a taskbar icon, and it could see the available wireless networks, could not connect to them, even the ones with no security.

Purged all network manager files suggested in various threads here, Installed wicd- it could see all available networks, could connect to unsecured networks, but not to my own secured network.   Password was correct in the wicd/configurations file.

Removed wicd, and reinstalled network manager from synaptic.  I have to network manager applet.  When I try to add it to the notification area with alt-f2, applet-nm, I get a brief flash of something in the notification area, but no applet.

System=>Preferences=>network connections shows no wireless connections, but I'm obviously connected to something (probably my neighbors unsecured network) since I"m reaching this webpage.

I tried to run sudo  wpa_cli from the terminal  to see what network the computer is connected to,  and it gives me this error:
> Could not connect to wpa_supplicant - re-trying

wpa supplicant is installed according to synaptic

Various troubleshooting output:

> 
owl@owl:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:08:0D:A0:CD:64

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             unmanaged
  Default:           no
  HW Address:        00:02:2D:B3:7D:40

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 

owl@owl

> 
owl@owl:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82551QM Ethernet Controller
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:a0:cd:64
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:11 memory:f7eff000-f7efffff ioport:eec0(size=64) memory:f7ec0000-f7edffff
  *-network
       description: Wireless LAN Card
       product: Version 01.01
       vendor: TOSHIBA
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:b3:7d:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 ip=192.168.1.113 link=yes multicast=yes wireless=IEEE 802.11b

I'd really like to get the wireless working on this laptop- the only things I need to be able to run on it are motion and the wireless, and a webcam, so I can set up a emote animal-watching security system ;)

Any advice???  Relying on my neighbors wireless isn't an option.  Network manager works on all my other computers.

---

### Post by kolibri on 2010-09-15
I got the network manager applet to show up in the notification bar using the instructions from another thread- but now my computer won't connect to anything, not even to the mysterious network it was automatically connecting to before..  When I tell it to connect to my secured network it just repeatedly asks for my password, and when I try to connect to the unsecured network it just cycles for a while and then fails to connect.

[http://ubuntuforums.org/showthread.php?t=1328631](http://ubuntuforums.org/showthread.php?t=1328631)

> **dineshs said:**
> I think NM has issues when
1)nm-system-settings.conf says *managed=false*
To solve this
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set
```
managed=true
```OR
2)/etc/network/interfaces contain anything other than
```
auto lo
iface lo inet loopback

```To solve this comment other lines(or backup the file and edit it so that it contains only those lines)
Should restart the machine after doing this
Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
Note :Always backup files before editing

---

### Post by measekite on 2010-11-21
> **kolibri said:**
> I got the network manager applet to show up in the notification bar using the instructions from another thread- but now my computer won't connect to anything, not even to the mysterious network it was automatically connecting to before..  When I tell it to connect to my secured network it just repeatedly asks for my password, and when I try to connect to the unsecured network it just cycles for a while and then fails to connect.

[http://ubuntuforums.org/showthread.php?t=1328631](http://ubuntuforums.org/showthread.php?t=1328631)

Try this:

I cannot connect automatically and do not see my network name in NM either so:

click the network icon.  
choose connect to hidden network
click the drop down if it says new
choose the name of your network
click the connect button

if you have WEP security you may have to click another connect button.

This is how I am able to connect after I had to Blacklist my prism driver.

If anybody reads this and know how I can auto connect let me know.  I already have the auto connect box checked.

---


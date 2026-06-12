---
title: "Problems with wireless connection in Ubuntu 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by sussa on 2010-04-30
Hello friends,

Since I've updated from 9.10 to 10.04, I'm having some difficulties to use the internet. Even though I can connect to my home wireless network, the connection is really slow.

I've got a Dell Inspiron 1545, and here comes the configuration:

```

sussa@sussa-laptop:~$ sudo lshw -C network
[sudo] password for sussa: 
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:2f:92:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:61:db:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)

```

```
wlan0     Link encap:Ethernet  HWaddr 00:24:d6:2f:92:72  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe2f:9272/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2678782 (2.6 MB)  TX bytes:500042 (500.0 KB)

```

```
sussa@sussa-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

```


Any help would be appreciated :)

Sussa



p.s.: Apart from that, I must say that Ubuntu 10.04 is fantastic. Easy to use, elegantly designed and working perfectly on my PC :)

---

### Post by sussa on 2010-04-30
ideas, anyone? :confused:

---

### Post by Tamalin on 2010-04-30
Yes, I have been experiencing the same problem as well.  The wireless says the connection is held at about 67%, but it is very sluggish.  What is the output of nm-tool?

---

### Post by chili555 on 2010-05-01
I am surprised it works at all, frankly. Notice you have two IP addresses, x.100 for wireless and x.102 for wired. Please detach the wire and reboot and let us have your report. If it is still slow, post:```
iwconfig
nm-tool wlan0
```Thanks.

---

### Post by Tamalin on 2010-05-01
I have now plugged in an ethernet cable, and the connection seems to be running a lot faster now.  Now that I have enough access, here is some of my info:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Vulcan"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:63:76:5C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```

$ nm-tool
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:C0:9F:F7:1D:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0  [Auto Vulcan] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           no
  HW Address:        00:14:A4:6B:D5:DA

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    fishhouse:       Infra, 00:22:75:4C:A9:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *Vulcan:       Infra, 00:1B:2F:63:76:5C, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            sierra
  State:             disconnected
  Default:           no

  Capabilities:




```

and...

```

$ sudo lshw -C network
[sudo] password for tamalin: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:c0:9f:f7:1d:5c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751m-v3.46a ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:a0100000-a010ffff
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a4:6b:d5:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.8 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:a7f00000-a7f0ffff

```

---

### Post by chili555 on 2010-05-01
Maybe we didn't understand each other. I said:> Please detach the wire And then you said:> I have now plugged in an ethernet cable,For the second time, either use the wired *OR *the wireless, but not both. Network Manager is designed *NOT* to allow both, but somehow, you have been able to use both and complain that your wireless is problematic. No wonder.> Type:              Wired
  Driver:            tg3
  State:             connected


---

### Post by Michaelsheldon on 2010-05-01
this may or may not be of use but could be worth a try.

On the last 2 releases (9.04 and 9.10) i had a problem with wireless connection cutting out or not connecting at all. I changed the network manager to wicd and it nearly wiped he problem out compleatly, save for the _Very _odd occasion.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I have not encountered the same problem yet since upgrading to lucid though.

Best of luck.

---

### Post by Tamalin on 2010-05-01
Well, the wireless the only connection I had before, and it was sluggish.  I couldn't even post the output of the commands.  When I plugged in the ethernet cable, and used the wired connection, it was fast enough to post the info.  I will now unplug the cable and see what happens.  I was running 8.04 before, but I downloaded 10.04, burned it to disk, and did a clean wipe and install.  Here is the output of the commands:

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Vulcan"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:63:76:5C   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```

$ nm-tool
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:C0:9F:F7:1D:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto Vulcan] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        00:14:A4:6B:D5:DA

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Checkers:       Infra, 00:1B:2F:63:76:5C, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            sierra
  State:             disconnected
  Default:           no

  Capabilities:




```

```

$ lshw -C network
[sudo] password for tamalin: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:c0:9f:f7:1d:5c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751m-v3.46a latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:a0100000-a010ffff
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a4:6b:d5:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.8 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:a7f00000-a7f0ffff

```

I am just wondering now, I seem to have noticed that ath5k's version is listed as 0.6.0 (EXPIRAMENTAL).  I think this may be the source of the problem, does anyone know what driver I had in 8.04?  My card is Atheros AR5212.

---

### Post by chili555 on 2010-05-01
Please try:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```Can you reconnect? Is the connection more stable? If so, we will need to build a short file to make it permanent.

Also, I notice there is a newer version of ath5k in linux-backports-modules. Do you have this installed? Sometimes this module works better with backports and sometimes without; please try both ways.

---

### Post by sussa on 2010-05-01
chili555 and Tamalin, thanks for the help. Here's what I got:

```
sussa@sussa-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"newnet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:5A:2B:E3:82   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


```
sussa@sussa-laptop:~$ nm-tool wlan0

NetworkManager Tool

State: connected

- Device: wlan0  [Auto newnet] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:24:D6:2F:92:72

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Mario Mori:      Infra, 00:19:E0:79:F3:3E, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WEP
    afonso:          Infra, 00:14:BF:7C:08:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA
    Machado:         Infra, 00:25:86:D6:6D:3E, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    dlink:           Infra, 00:22:B0:47:2B:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    MARILIA:         Infra, 00:1D:0F:E7:D0:A0, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Andrea:          Infra, 00:14:6C:06:E6:EC, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    Nina:            Infra, 00:21:04:10:25:B7, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
    *newnet:         Infra, 00:26:5A:2B:E3:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    SuperDanDan:     Infra, 00:1A:70:6E:8D:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    FerreiraMoreno&Ruiz: Infra, 00:24:B2:28:58:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA
    Tra-Ca-Tra:      Infra, 00:27:19:C1:DA:74, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Jair_Lari:       Infra, 00:1D:0F:E9:D4:F4, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
    kraepelin:       Infra, 00:1B:11:FF:6D:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    GPMALBA:         Infra, 00:27:19:CA:60:5A, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:25:64:61:DB:A7

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

and also....

```
sussa@sussa-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:2f:92:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:61:db:a7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)

```

My connection was working for about half an hour.... and then it has become sluggish again. Back to wired internet :(

Do you friends have any idea on how to solve this?

Once again, thank you so much for your help! :)

Sussa

---

### Post by chili555 on 2010-05-01
> wlan0     IEEE 802.11abgn  ESSID:"newnet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:5A:2B:E3:82   
          [COLOR="Red"]Bit Rate=0 kb/s[/COLOR]  You might try:```
sudo iwconfig wlan0 rate 54M
```

---

### Post by Tamalin on 2010-05-01
> **chili555 said:**
> Please try:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```Can you reconnect? Is the connection more stable? If so, we will need to build a short file to make it permanent.

Also, I notice there is a newer version of ath5k in linux-backports-modules. Do you have this installed? Sometimes this module works better with backports and sometimes without; please try both ways.


Well, I ran the commands.  The wireless successfully disconnected and reconnected without any problems.  However, it was no more "stable".  Also, I have installed the linux-backports-modules-wireless-lucid-generic and linux-backports-modules-wireless-2.6.32-21-generic packages.  I didn't see any improvement, and a quick modinfo ath5k revealed the ath5k version still at 0.6.0.  Was there something else I was supposed to do?

---

### Post by chili555 on 2010-05-01
> Was there something else I was supposed to do?Nope. You could file a bug report on Launchpad; you could re-install 9.10, you could buy a different wireless card and you could Google for a solution. I am out of ideas.

---

### Post by Tamalin on 2010-05-01
Ok, well, I am trying to install madwifi, but I am having some difficulties.  It depends on ath_hal, but I am trying to install that, and having dependancy issues.  Package dbus-1 is reported missing...  I checked, and there is not "dbus-1" package, just "dbus"?  What am I supposed to do?

---

### Post by chili555 on 2010-05-01
You might try libdbus1 and libdbus1-dev.

---

### Post by Tamalin on 2010-05-01
Thank you.  Is there a step by step instruction manual for migrating from ath5k to madwifi?  I haven't found much via Google.

---

### Post by chili555 on 2010-05-01
Can you give me a link to where you downloaded it?

---

### Post by sussa on 2010-05-01
> **chili555 said:**
> You might try:```
sudo iwconfig wlan0 rate 54M
```

chili555, thank you so much for your help. Apparently, now everything is alright, my connection is working the way it should.

The Ubuntu community is great because of people like you.

Thanks,

Sussa

---

### Post by ve3tru on 2010-05-02
I got the same laptop and same wireless card.
You need to download and install the Broadcom STA Wireless driver its in Synaptic (hard wire to the Internet for this and use "IVP6 settings leave on ignore lvp4 auto")
It's Proprietary so its not included with the OS. It's the only one that works, it was included in 8.04 which was cool. It asked you if you wanted to install a  Proprietary driver, this changed in 9.04. They make you think there is an open source driver that works but they don't, I tried them all. (F2 turns on and off your wireless, and this takes time to come back so sometimes you think its broke but its not)  My thinking it should be included in the OS, a wireless card is not an option on a laptop, why did they take it out. If I was a newbe Id be giving up on Ubuntu right there. I have, and you will have another problem a flickering screen, didn't have it on 9.04 but its there in 10.04. It's Something to do with your intel mobile chip there is a work around (turning off power save) but I don't like it. Your laptop works harder your fan stays on and it eats power, I  hope they come up with a fix soon. (don't count on it) Id rather wait for the fix tho
 I Just set up my printer/scanner what a nightmare scrips code and two days wasted, guess it all depends on the printer you have. Linux sure makes it hard for a newbe is all I can say.
Hope this helps
Peter

---

### Post by chili555 on 2010-05-02
> You need to download and install the Broadcom STA Wireless driver For his Intel card??> *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation


---

### Post by amudman on 2010-05-02
Well, I'm stuck in the wireless no-connect. It has worked great , without problems, for several updates.  I upgraded with a positive attitude, but I told myself I should wait until others have found and fixed the early problems.  I should have waited and I should not have been baited.

The problem is this: I am an not really capable of doing and understanding all the jargon and implementing the wonderful help offered. It often leaves out the info I need to fully follow the suggestions. You, the experts, assume I know all the info you do. Big mistake, but I really try and I really like Ubuntu.

The lack of wireless connectivity(wired works) on my laptop does not seems well understood by all. So, unless someone can help with a fix I propose the best solution for me is to re-install Ubuntu 9.10. I am downloading the file now. What a waste. I am willing to try and follow anything you offer, if you have the patience.

Thanks, you all are great to help.

---

### Post by chili555 on 2010-05-02
I will be glad to help. Please start a new thread and open a terminal and post:```
lspci -nn
lsusb
iwconfig
```I am confident we can get you going.

---

### Post by Tamalin on 2010-05-02
I downloaded the madwifi package from [http://madwifi-project.org]("http://madwifi-project.org").  The website states:

> 
In case you use kernel 2.6.25 or newer, you need to get this snapshot of the madwifi-0.9.4 branch instead of the v0.9.4 release! That snapshot is basically v0.9.4 plus compilation fixes for recent kernels.


I selected that link.

---

### Post by chili555 on 2010-05-02
It builds a driver called ath_pci. If you do:```
ls /etc/modprobe.d
```You will see there is a blacklist-ath-pci.conf file. For your information, it says:> # For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pciIn order to use the madwifi driver, you will need to blacklist ath5k and remove /etc/modprobe.d/blacklist-ath_pci.conf. You could simply move it to your home directory in case you need it again:```
sudo mv /etc/modprobe.d/blacklist-ath_pci.conf ~
```ath_pci should load automatically after that; if not:```
sudo su
echo ath_pci >> /etc/modules
modprobe ath_pci
exit
```Follow the INSTALL directions carefully and post back if you get stuck.

---

### Post by sussa on 2010-05-02
Updating:

Once more, my connection is not working properly. Although I can use the internet at a good speed, sometimes my connection just goes down to "0 Kbps". It does not disconnect, it simply 'stops' every 5 or 10 minutes with no apparent reason.

Sorry for bothering you guys once again, but I'm still having some problems. Setting up a good internet connection in Ubuntu 10.40 has been such an uneasy task for me :(

Thanks again for your help,

Sussa

---

### Post by ve3tru on 2010-05-03
Sorry guys 
I looked at your model 1545 I assumed you have the same hardware as me, stands to reason same make model, but no.
my mistake weird tho??

---

### Post by chili555 on 2010-05-03
> **sussa said:**
> Updating:

Once more, my connection is not working properly. Although I can use the internet at a good speed, sometimes my connection just goes down to "0 Kbps". It does not disconnect, it simply 'stops' every 5 or 10 minutes with no apparent reason.

Sorry for bothering you guys once again, but I'm still having some problems. Setting up a good internet connection in Ubuntu 10.40 has been such an uneasy task for me :(

Thanks again for your help,

SussaI believe you are using the driver iwlagn. You might try a driver parameter:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn swcrypto=1
```If this has no effect, try:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn disable_hw_scan=1
```If either works, we can make a file to make it permanent:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn your_option=1
```Proofread, save and close gedit. Of course, substitute the option that worked for you.

---

### Post by peppot on 2010-05-05
swcrypto=1 seems to have solved my connection drop problems, at least (Sony Vaio VGN-FW21M laptop).

---

### Post by Tamalin on 2010-05-06
This problem was quickly resolved by installing Madwifi.  Thanks for the Help!

---

### Post by garvint on 2010-05-10
chili555, I have the same problem with wireless connection being unstable in 10.04, previously this never took so long to connect.

my "lspci -nn" shows this:


laptop@laptop-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
0f:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0f:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0f:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0f:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
laptop@laptop-laptop:~$ 


my "lsusb" shows this:


laptop@laptop-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


my "iwconfig" shows this:


laptop@laptop-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BTHomeHub"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:68:7C:18:F1   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.


as you can see I have a Broadcom Corporation BCM4311 802.11b/g WLAN.

When connecting to a WEP network takes 2 -5 minutes.

Can you help? I don't want to go back to a previous ubuntu version.

---

### Post by chili555 on 2010-05-10
> as you can see I have a Broadcom Corporation BCM4311 802.11b/g WLAN.

When connecting to a WEP network takes 2 -5 minutes.

Can you help?The original poster of this thread hsa an Atheros card; you have a Broadcom. Please start a new thread. If I don't catch it pretty quickly, send me a private message. I notice this:> wlan0 IEEE 802.11bg ESSID:"BTHomeHub"
Mode:Managed Frequency:2.412 GHz Access Point: 00:1D:68:7C:18:F1
Bit Rate=54 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
[COLOR="Red"]Link Quality=37/70[/COLOR] Signal level=-73 dBm Are you really far from the router? Does the router have an option to increase the transmit power? Do you need a bigger antenna on it?

---

### Post by sussa on 2010-05-10
> **chili555 said:**
> You might try:```
sudo iwconfig wlan0 rate 54M
```

I tried, and I have indeed improved my connection speed. However, this option is not saved (I don't know why), and every time I boot my PC, I need to type that command again. Is there any way to save it definitely?

Secondly, although the speed is getting better, my connection is not that good. To be precise, it has a fair average speed, but the websites take a long time to start loading (on Firefox, "Looking for..." and "Connecting to..." take forever). When the browser connects to the websites, it's fast as usual.

Thanks for all your help,

Sussa

---

### Post by chili555 on 2010-05-10
You might add it to /etc/rc.local:```
sudo gedit /etc/rc.local
```Add a single line above 'exit 0':```
iwconfig wlan0 rate 54M
```Proofread, save and close gedit.

Right-click the Network Manager icon, Edit Connections, select Wireless and make sure IPv6 is set to ignore.

Also, in the Address Bar of Firefox, type *about:config* and press Enter. Search for ipv6 and set:

network.dns.disableIPv6;       **true**

See if these steps help.

---

### Post by sussa on 2010-05-14
chili555, thanks for your help. I've been using your fix for a couple of days and, apparently, everything is now working fine, with my connection stable and at a good average speed.

Thanks once again for your tips,

Sussa

---

### Post by pradeepthundiyil on 2010-05-14
Hi........


I was using Gnome-PPP to connect my datacard in Ubuntu 9.10. But I have problem in using the same method in Ubuntu 10.04. Kindly provide help those who have resolved it.. Thank you. I 'm pasting the Dialer Log here..


******************************************************************************************************
*                                                                   **Dialer Log**                                                                                 *
******************************************************************************************************

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
CONNECT 230400
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Fri May 14 06:32:00 2010
--> Pid of pppd: 1592
--> Disconnecting at Fri May 14 06:32:00 2010
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

---

### Post by Simon741 on 2010-05-14
I'm having mostly the same problem (after upgrading from 9.10 to 10.04 the wireless connection is very unstable) but with a different configuration:

```
simon@simon-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 140M [10de:0429] (rev a1)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
```

```
simon@simon-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 04f9:01f3 Brother Industries, Ltd 
Bus 004 Device 004: ID 046d:c047 Logitech, Inc. Laser Mouse
Bus 004 Device 003: ID 05ac:0205 Apple, Inc. Extended Keyboard [Mitsumi]
Bus 004 Device 002: ID 05ac:1002 Apple, Inc. Extended Keyboard Hub [Mitsumi]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
simon@simon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Saferplanet"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:23:A3:81:3B:30   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Since it seams to be the same problem, I thought it would be best to post it here although it is a different hardware configuration. However, I'm a bit afraid to just proceed as explained above.

---

### Post by 14quartz on 2010-05-14
[FONT=Comic Sans MS][SIZE=3]I am using Reliance Netconnect I had used that in Ubuntu 9.10 and 9.04  successfully.I have not switched to 10.04(Lucid Lynx).So i want to know  whether Netconnect is working in 10.04? or Is 10.04 supports  netconnect?.
Even though i used that one(Netconnect) in ubuntu 9.10 and 9.04 i had  the question how to change the speed ie. between broadband,hybrid,1x
Thanks in Advance.[/SIZE][/FONT]

---

### Post by sympton on 2010-05-14
> **chili555 said:**
> Maybe we didn't understand each other. I said:And then you said:For the second time, either use the wired *OR *the wireless, but not both. Network Manager is designed *NOT* to allow both, but somehow, you have been able to use both and complain that your wireless is problematic. No wonder.

Little offtopic, but are you saying here that you cannot share your wireless connection to wired ?)

---

### Post by Dellsworth on 2010-05-14
I apologize for butting into this thread with yet another problem, but am hoping someone can help me.
 
I am a newbie to Linux and am running Ubuntu 10.04 with the 2.6.32-21-generic kernel on a new Dell laptop (Centrino vPro).  I cannot change my Wireless Network status from "Disabled" because the option is greyed out.  I have searched several blogs but nothing I've tried seems to work.  I am using (or trying to use) an Intel 5300 AGN Wireless card.  The driver (iwlagn) appears to be loaded.  According to **dmesg**, the wireless card is recognized.
 
**lshw -C network** shows that wlan0 is disabled.  I've tried **sudo ifconfig wlan0 up**, but get **SIOCSIFFLAGS: Unknown error 132**.  I tried several things posted for this error, including **rfkill list**, but nothing is working.  I have to admit, I don't really know what I am doing since this is the first time I have used Linux. :(
 
**nm-tool wlan0** produces Type 802.11 WiFi, Driver=iwlagn, State=[COLOR=red]Unavailable[/COLOR], Default=no, HW Addr=00:21:6A:68:5C:2C.  Any ideas, or can you direct me to someone who can help?  Thanks.

---

### Post by chili555 on 2010-05-14
> **pradeepthundiyil said:**
> Hi........


I was using Gnome-PPP to connect my datacard in Ubuntu 9.10. But I have problem in using the same method in Ubuntu 10.04. Kindly provide help those who have resolved it.. Thank you. I 'm pasting the Dialer Log here..This has nothing to do with wireless or the original poster's Atheros card. Please post a new thread.

---

### Post by chili555 on 2010-05-14
> **Dellsworth said:**
> I apologize for butting into this thread with yet another problem, but am hoping someone can help me.
 
I am a newbie to Linux and am running Ubuntu 10.04 with the 2.6.32-21-generic kernel on a new Dell laptop (Centrino vPro).  I cannot change my Wireless Network status from "Disabled" because the option is greyed out.  I have searched several blogs but nothing I've tried seems to work.  I am using (or trying to use) an Intel 5300 AGN Wireless card.  The driver (iwlagn) appears to be loaded.  According to **dmesg**, the wireless card is recognized.
 
**lshw -C network** shows that wlan0 is disabled.  I've tried **sudo ifconfig wlan0 up**, but get **SIOCSIFFLAGS: Unknown error 132**.  I tried several things posted for this error, including **rfkill list**, but nothing is working.  I have to admit, I don't really know what I am doing since this is the first time I have used Linux. :(
 
**nm-tool wlan0** produces Type 802.11 WiFi, Driver=iwlagn, State=[COLOR=red]Unavailable[/COLOR], Default=no, HW Addr=00:21:6A:68:5C:2C.  Any ideas, or can you direct me to someone who can help?  Thanks.Please start a new thread and actually post:```
sudo lshw -C netwrok
rfkill list 
iwconfig
```Thanks.

---

### Post by JohnDoe365 on 2010-05-18
Hi guys, as I am (actually my wife) going absolutely mad on the current issues of WiFi connection speed problems in Ubuntu 10.04 I found at least for my connectins problems the temporal fix: Disable wireless ... enable wirells. For some varying time speed is back to normal then suddenly drops of again.

See also [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

---

### Post by sussa on 2010-06-04
Unfortunately, here I am with another wireless problem. My connection was working fine until two days ago, when it has suddenly become sluggish. In fact, when I connect everything is ok; about 2 or 3 minutes later, my speed goes to zero (although I'm still connected to my wireless network). And it happens every time I reconnect too. Any suggestions?

Thank you for your attention,

Sussa



p.s.: I'm thinking about reinstalling Ubuntu 9.10, which used to work flawlessly in my notebook. There are so many people complaining about wireless problems (including myself), that perhaps downgrading to 9.10 and skip this version would not be a bad idea. I'll wait for 10.10 :(

---

### Post by sussa on 2010-06-04
Well, I reinstalled 9.10 last night, and all my wireless problems are now gone. The internet connection is working properly, with no interruption nor sluggishness. I'll stick with the old Ubuntu version for a while, and change it only to try 10.10. Thank you all for the help! :)

---


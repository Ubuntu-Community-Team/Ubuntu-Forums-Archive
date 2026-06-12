---
title: "Can't find any wireless networks (aka, can't get my wireless working/installed)"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by fivestones on 2010-05-25
Hi everybody!
I've been using linux for about 3 days now, since I installed ubuntu the other day, and i've learned a lot but still don't know a lot. Sorry if I ask obvious things...I've tried to look things up before posting.


I'm trying to get my wireless to work. I started with an old US Robotics usb card I had laying around (USR5421) but couldn't get that to work (tried installing with ndiswrapper, looked like it installed a driver successfully, but it wouldn't see my access point).

So I went a bought a cheep airlink 101 (AWLH3028v2) PCI card and put that in my comptuer. I installed drivers with ndiswrapper, Wireless Network Drivers program says hardware is present for net8185, so that all looks good. But when I look for wireless accesspoints, none are found. I tried installing WICD and that doesn't find any either ("No wireless networks found"). I tried installing madwifi-tools but couldn't figure out how to get it installed--it doesn't seem to be in any repository I could find. If tried parts of lots of different tutorials on getting wireless working, and who knows, maybe I've messed something up along the way. But I thought I'd ask and see if anyone could help me out or point me in the right direction...

Here's some info from terminal if it can help:

```

david@media-server:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

david@media-server:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:11:0a:63:6e
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=10.0.0.129 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:fe9e0000-fe9fffff ioport:ac00(size=32)
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 20
       serial: ff:ff:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.55+Realtek,09/04/2009,5.1113.9 latency=32 link=yes maxlatency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 ioport:b800(size=256) memory:fea00000-fea001ff
david@media-server:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

audo wlan0
iface wlan0 inet static
david@media-server:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"gfopveopufhqlyyzwahbbeajtpuogryj"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:5/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@media-server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         DD-WRT          0.0.0.0         UG    0      0        0 eth0
david@media-server:~$ 


```I just noticed the essid listed for wlan0: gfopveopufhqlyyzwahbbeajtpuogryj. Random. i have no idea what that is. My unprotected accesspoint should be called "dd". There are probably 10-15 ssids in the area that I can see from my windows computer. I'm not sure what else to add that would be helpful.

Thanks in advance!

---

### Post by fivestones on 2010-05-25
I should add I'm using ubuntu 10.04.

Thanks!

---

### Post by purelinuxuser on 2010-05-25
Try posting the output of:```
lspci
```
It might not be necessary though, as I already know what wireless card you have.  I will look into this...

---

### Post by purelinuxuser on 2010-05-25
A quick Google search reveals that there is a native Linux driver already available for your card.  Did wireless work out of the box when you first installed Ubuntu 10.04?

You may try uninstalling ndiswrapper, un-blacklisting any wireless drivers, and posting the output of the following commands again:
```
iwconfig
lshw -c network
sudo iwlist wlan0 scan
```Best of luck ;)

---

### Post by fivestones on 2010-05-25
In case it's still needed:

```
david@media-server:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
03:03.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 04)
david@media-server:~$ C

```

I'll work on your other suggestions. Thanks!
When I first installed ubuntu 10.04, with the US robotics wireless usb adapter, it looked like it was kind of working, because it listed one wireless network, but not mine, and not any of the ones that I normally can see from my windows computer. That's when i started messing around with ndiswrapper and eventually trying a different network card completely.

I'll be back with that other info after uninstalling ndiswrapper etc.

Thanks again!

---

### Post by purelinuxuser on 2010-05-25
> **fivestones said:**
> In case it's still needed:

```
david@media-server:~$ lspci
...

```

My bad, that should have been lsusb to catch your USR stick.

Anyway, I'm going to be working with the US Robotics wireless card, not the Airlink.  Just so we're clear :P

---

### Post by fivestones on 2010-05-25
Ok, output for lsusb is:

```
david@media-server:~$ lsusb
Bus 005 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a33 Dexon Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0baf:011b U.S. Robotics Wireless MAXg Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
david@media-server:~$ lsusb -vv

```And I don't know if it's helpful or not, but here's the part of the output for the USR adapter from lsusb -vv:

```
Bus 001 Device 005: ID 0baf:011b U.S. Robotics Wireless MAXg Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0baf U.S. Robotics
  idProduct          0x011b Wireless MAXg Adapter
  bcdDevice            0.06
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           48
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```I uninstalled ndiswrapper, un-blacklisted wireless drivers (...I think--I just deleted everything that was in the file /etc/modprobe.d/blacklist, which wasn't much), and here's some new output for you--I'm not sure what it means, but the islist scan came up with something for once...

```
david@media-server:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dd"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 02:1D:7E:4D:F7:F2   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/100  Signal level=64/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@media-server:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:11:0a:63:6e
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=10.0.0.129 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:fe9e0000-fe9fffff ioport:ac00(size=32)
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64
       resources: ioport:b800(size=256) memory:fea00000-fea001ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:c1:16:40:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320b usb-0000:00:1d.7-7 ip=10.0.0.125 link=yes multicast=yes wireless=IEEE 802.11bg
david@media-server:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 02:1D:7E:4D:F7:F2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/100  Signal level=70/100  
                    Encryption key:off
                    ESSID:"dd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000259e12de5
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00026464
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1D:7E:4D:F7:F1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/100  Signal level=65/100  
                    Encryption key:on
                    ESSID:"Salomir"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000027030f9a4
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000753616C6F6D6972
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 34:EF:44:44:B3:01
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=50/100  Signal level=50/100  
                    Encryption key:on
                    ESSID:"2WIRE235"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005e500b742b
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00083257495245323335
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030109
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303530303931393036363233351021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3530303931393036363233351054000800060050F20400011011000A686F6D65706F7274616C10080002008E

david@media-server:~$ 

```by the way, before doing this, I plugged back in the usb US Robotics card, but the Airlink 101 PCI card is still in the computer--should I pull it out? Or will it not matter?

Thanks some more :-)

---

### Post by fivestones on 2010-05-25
Ooooooh dang...It's WORKing! :-)

I think it must have just be uninstalling ndiswrapper and unblackilisting things, and then rebooting...not sure.

But I'm online, and my wired ethernet cable is unplugged :-)

I should be ok to remove the PCI airlink card so I can return it to the store, right?

Thanks!

---

### Post by purelinuxuser on 2010-05-25
> **fivestones said:**
> by the way, before doing this, I plugged back in the usb US Robotics card, but the Airlink 101 PCI card is still in the computer--should I pull it out? Or will it not matter?

Doesn't matter.

> **fivestones said:**
> ```
wlan0     IEEE 802.11bg  ESSID:"dd"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 02:1D:7E:4D:F7:F2   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/100  Signal level=64/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

That's it!  You're connected!  See if you can get online. :)

> **fivestones said:**
> ```
wlan0     Scan completed :
          Cell 01 - Address: 02:1D:7E:4D:F7:F2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/100  Signal level=70/100  
                    Encryption key:off
                    ESSID:"dd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000259e12de5
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00026464
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

It shows up on the scans too!  Enjoy your wireless :guitar:

Anyway, I think the problem was ndiswrapper.  It should only be last resort, as some things don't work properly with ndiswrapper (some forms of WPA/WPA2, scanning, Monitor/Master modes, etc).

[I]Edit: Darn, beat me by a few seconds!  And yes, removing the PCI card would be fine... it's not like it's going to cause the computer to self-destruct or anything...right? ;)
[/I]

---

### Post by purelinuxuser on 2010-05-25
[B]BTW, don't forget to mark this thread [SOLVED].
[/B]

---

### Post by fivestones on 2010-05-25
There's just a bit more--

Everything was going well, until I started trying to access my samba shares that are on the ubuntu machine from my windows machine. They didn't work any more. In windows I tried connecting by ip address instead of by the computer name, and that worked. Why should this be? Is there a way I can connect by computer name again?

Then...
I rebooted the ubuntu machine. When it finished booting up, there was no wireless connection connected. When I viewed wireless networks, there was 1, then 3 networks, none of them mine. I thought maybe somehow the stuff you had me do in terminal had gotten it to see my network so I went back to terminal, typed iwconfig. When I did this, a new window popped up (not sure if it was related to iwconfig at all) saying something about how my password hadn't been entered for my keyring or something like that. I put my password in that box, and immediately, the little wireless network icon started doing its thing that said it was connecting, and then I was connected to my own wireless network.

What happened here? Why did it not connect at first? I'm guessing that when I first installed ubuntu, this was also what happened, and why I couldn't see my network, and if I had just done a iwconfig and/or put my password in where ever that window was that asked for it, I would have been able to connect, out of the box. How do I make it connect automatically without doing any of this when I boot up?

Thanks so much for your help!

---

### Post by linuxonbute on 2010-05-25
> **fivestones said:**
> There's just a bit more--

Everything was going well, until I started trying to access my samba shares that are on the ubuntu machine from my windows machine. They didn't work any more. In windows I tried connecting by ip address instead of by the computer name, and that worked. Why should this be? Is there a way I can connect by computer name again?


I guess that you now have a different IP address or name for your samba box so Windows doesn't relate the name with the IP address.
> 
Then...
I rebooted the ubuntu machine. When it finished booting up, there was no wireless connection connected. When I viewed wireless networks, there was 1, then 3 networks, none of them mine. I thought maybe somehow the stuff you had me do in terminal had gotten it to see my network so I went back to terminal, typed iwconfig. When I did this, a new window popped up (not sure if it was related to iwconfig at all) saying something about how my password hadn't been entered for my keyring or something like that. I put my password in that box, and immediately, the little wireless network icon started doing its thing that said it was connecting, and then I was connected to my own wireless network.

What happened here? Why did it not connect at first? I'm guessing that when I first installed ubuntu, this was also what happened, and why I couldn't see my network, and if I had just done a iwconfig and/or put my password in where ever that window was that asked for it, I would have been able to connect, out of the box. How do I make it connect automatically without doing any of this when I boot up?

Thanks so much for your help!

AFAIK Usually when it asks for your keyring password you click on a button to allow it once or always. If you click always  it should not ask for it again ( Cannot remember exact phrase but it should be easy when you know what to look for)

---


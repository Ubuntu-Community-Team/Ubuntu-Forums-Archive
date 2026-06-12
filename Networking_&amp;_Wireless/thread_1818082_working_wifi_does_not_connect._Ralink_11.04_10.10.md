---
title: "working wifi does not connect. Ralink 11.04 10.10"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by errarel on 2011-08-04
I have new emachine 1401 and I can't get it to connect to wireless.
It does detect networks but when connecting keeps asking for password over and over and never connects.

I don't have wired connection at all and the wifi router is not managed by me, so I'm retyping output through my windows xp samsung netbook which works over the same wireless network...

I have tries some other solutions I found around here (install bcmwl-kernel-source, rt3090-dkms_2.4.0.4, blacklist rt2800pci...) so it's not original configuration but behaves exactly the same.
Can anybody please enlighten me?:)

```

uname:
2.6.38-8-generic #42-Ubuntu i686 athlon i386 GNU/Linux

lspci:
04:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

ifconfig:
ra0 Link encap:Ethernet HWaddr somehex
    inet6 addr: somehex/64 Scope:Link
    UP BROADCAST MULTICAST MTU:1500 Metric:1
    RX all zeroes
    TX all zeroes
    collisions:0 txqueuelen:1000
    RX bytes:522KB TX bytes:0
    Interrupt:18

iwconfig:
ra0 Ralink STA ESSID:"" Nichname:"RT2860STA"
    Mode:Auto Frequency=2.462GHz Access Point: Not-Associated
    Bit Rate:1 Mb/s
    RTS thr:off Fragment thr:off
    Link Quality=70/100 Signal level:-74dBm Noise level:-74 dBm
    Rx all zeroes
    Tz all zeroes

lshw -C network:
    description: Wireless interface
    product: RT3090 Wireless 802.11n 1T/1R PCIe
    vendor: Ralink corp.
    physical id: 0
    bus info: pci@0000:04:00.0
    logical name: ra0
    version: 00
    serial: somehex
    width: 32 bits
    clock 33MHz
    capabilities: bus_master cap_list ethernet physical_wireless
    configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.4 latency=0 multicast=yes wireless=Ralink STA
    resources: irq:18 memory:fdsomething

```

---

### Post by loolooyyyy on 2011-08-04
> **errarel said:**
> I have new emachine 1401 and I can't get it to connect to wireless.
It does detect networks but when connecting keeps asking for password over and over and never connects.

I don't have wired connection at all and the wifi router is not managed by me, so I'm retyping output through my windows xp samsung netbook which works over the same wireless network...

I have tries some other solutions I found around here (install bcmwl-kernel-source, rt3090-dkms_2.4.0.4, blacklist rt2800pci...) so it's not original configuration but behaves exactly the same.
Can anybody please enlighten me?:)


have you blacklisted all rt2x00lib,rt2800pci,rt2x00usb,rt2x00pci,rt3390sta ?
if so, have a look at:
[http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090)

---

### Post by errarel on 2011-08-04
ehh

in step 7 the the document says:
> 
After you issue the previous command you should see the Desktop top panel wireless icon come to life as it tries to connect. You will be prompted for a WPA password. Give it a little while and it should connect.

Not sure this command is necessary but you can use if the Wireless isn’t started automatically.
sudo ifconfig wlan0 up

Step 8
Okay at this point you have made a lot of progress and should be happily surfing.


in MY case, no network showed up.
sudo ifconfig ra0 up --> No such device
sudo ifconfig wlan0 up --> No such device

so it's actuall worse than it was:(
I used to see networks but couldn't connect to them. Now I can't see any:(

---


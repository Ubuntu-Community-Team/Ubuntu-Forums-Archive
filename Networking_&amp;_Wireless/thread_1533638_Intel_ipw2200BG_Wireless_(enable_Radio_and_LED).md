---
title: "Intel ipw2200BG Wireless (enable Radio and LED)"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by skozzy on 2010-07-18
Previously I was using Ubuntu 9.04 and my wireless worked, after upgrading to 9.10 it stopped working, recently I formatted and installed Ubuntu 10.04 LTS and I am back to square 1 with the wireless radio turned off and previous instructions for 9.04 don't work. So I am in need of help again.

The BIOS options are DISABLE and LAST STATE, on the laptop (Medion MD97600) there is a button (not a switch) that on Windows you just press and it turns on the LED and the wireless starts. I used to refer to it as an Acer Hotkey from the help in the past.

Previous attempt with earlier Ubuntu's was just getting the LED to turn on which seems to also enable the wireless. Back when I had Ubuntu 8.04 I was also able to use the button with **acerhk**, but in 9.04 I couldn't get the button to work and only needed a small script to turn on the wireless.

Hope someone has the time to help, this seems such a common problem for all of us who aren't too linux savvy.

Sorry about the smiley's in the post, that's a new default on the site I take it, can't see how to turn it off.

Here is the network part of lshw
>         *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:3000(size=4096) memory:b8000000-b80fffff
           *-network:0 DISABLED
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@0000:06:05.0
                logical name: eth1
                version: 05
                serial: 00:15:00:02:e7:47
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
                resources: irq:19 memory:b8000000-b8000fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:bc:4e:f3
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.20 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:18 ioport:3000(size=256) memory:b8001000-b80010ff

This is from iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---


---
title: "problems to install wireless connection"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by Uncle_Wim on 2010-03-05
[SIZE=4]I want to install my wireless internet connection but don't know how to do so. I'm new with ubuntu, always worked with windows.
These things are colored red amongst my hardware:
[/SIZE]
id:communication
                description: Modem              product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller              vendor: Intel Corporation              physical id: 1e.3
              bus info: pci@0000:00:1e.3
              version: 03              width: 32 bits              clock: 33MHz              capabilities: pm cap_list               configuration: latency=0              resources: ioport:3400(size=256) ioport:3800(size=128)

id:network:1
                   description: Ethernet controller                 product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)                 vendor: Linksys, A Division of Cisco Systems                 physical id: 2
                 bus info: pci@0000:0a:02.0
                 version: 00                 width: 32 bits                 clock: 33MHz                 capabilities: pm bus_master cap_list                  configuration: latency=32 maxlatency=32 mingnt=32                 resources: ioport:5000(size=32) memory:c8215000-c821501f memory:c8214800-c8214fff

[SIZE=4]This is also red but doesn't have anything to do with wireless, but how fix this?

[/SIZE]id:serial
                description: SMBus              product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller              vendor: Intel Corporation              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 03              width: 32 bits              clock: 33MHz              configuration: latency=0              resources: ioport:3c20(size=32)

---

### Post by chili555 on 2010-03-05
Let's take each part in order. The modem is probably shown red because it has no driver associated with it. Unless you are going to use it for dialup telephone line networking, you can safely ignore it.

Second, the INPROCOMM IPN 2220 Wireless LAN Adapter is also probably red because it lacks a driver. It is relatively rare, so I am not at all sure that a native Linux driver is available. Everything I have been able to read suggests this only works with ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It requires the Windows XP driver, usually the .inf and .sys files. Do you have the original driver disc? You might have success with these I have attached.

Last, the serial device is also in red because it lacks a driver. As far as I know, it works perfectly fine without it. There are not many serial devices around now.

---


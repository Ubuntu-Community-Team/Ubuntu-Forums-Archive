---
title: "Belkin F5D7050A Wi-Fi USB not working"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by Lightsider on 2010-08-07
I have a Belkin F5D7050A USB Wi-Fi adapter and I can't get it to work in my Mythbuntu install (Mythbuntu 10.04.1). I plugged it into my machine (a desktop I built myself), and nothing happened. I found it in lsusb:

lsusb:
```
Bus 002 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
```But there is no "wireless connection active" icon in the status bar (only my ethernet connection is displayed). 

I then right-clicked on the status bar and selected "Edit Connections", created a new wireless connection (there was none previously), and set the parameters. Again, nothing happened, and iwconfig shows that they didn't seem to "take"

iwconfig:
```
wlan0      IEEE 802.11bg    ESSID:off/any
Mode:Managed   Access Point: Not-Associated    Tx-Power=12 dBm
Retry long limit:7   RTS thr:off   Fragment thr:off
Power Management:on
```I then set my ESSID manually usingg iwconfig, which caused it to show up in iwconfig but again no connection was shown in the status bar:

iwconfig:
```
wlan0      IEEE 802.11bg    ESSID:"Concordia"
Mode:Managed   Access Point: Not-Associated    Tx-Power=12 dBm
Retry long limit:7   RTS thr:off   Fragment thr:off
Power Management:on
```According to [http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html), and from checking the files on the Windows install CD, I should be using an RT73 driver.

lsmod:
```

Module      Size      Used by
rt73usb     22434    0
```I looked through my dmesg output, but I'm not really sure what to look for. There was no mention of "Belkin" or "RT73", but I did find a whole plethora of error messages pertaining to "rt2x00usb", I don't know if they're relevant:

```

phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c4 with error -71
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x30c0 with error -71

```Repeating many, many times, with slowly increasing values for "offset". 

My network connection info seems to indicate that something, at least, was detected:

lshw:

```

*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: xxxxx (my MAC address)
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```Trying to scan my network yields:

sudo iwlist scan
```

wlan0    Failed to read scan data: Resource temporarily unavailable

```Being a newbie I'm not sure where to start debugging. Is my card even being recognised? Is the driver correctly installed? Or is the problem further downstream, in my network configuration? 

Thanks very much in advance for any pointers! :)

---


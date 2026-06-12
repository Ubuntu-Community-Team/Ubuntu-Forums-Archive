---
title: "WiFi on Linux still problematic?"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2011-02-26
It seems to me that wifi operation is still a problem area on Linux, and I'm not sure where the blame lies.

Two years ago my Netgear WG111 USB dongle would not work, while my SafeCom worked great (i.e. signal level, quality & rate were all good).

During 2009 a kernel update/upgrade changed the SafeCom operation such that the highest signal/quality level was limited to 35% (the driver produces the same data for quality & signal on this device).

During the last 12 months the Netgear WG111 has started to work on Linux, and reports a nice high signal level and quality, but the bit rate is generally only 1 to 11Mb/s.

I think these kind of problems are generally due to the device drivers, which are either poor or no longer compatible with the current kernel. Changes to the kernel/Ubuntu occur too frequently for the drivers to be properly maintained. Also the drivers do not appear to report data such as signal, noise & quality in a consistent way.

The attached illustrations show graphical representations of the kind of data you can obtain using iwconfig.

DellWifi.png is from my trusty (if rather old) Dell 500m which has an ipw2100 driver. This appears to work well, with max bitrate maintained as long as the signal & quality are reasonably high.

Netgear.png is for a WG111 54Mbps wifi dongle (driver rtl8187) attached to a Compaq D510. This seems to be OK on the basis of signal & quality, but the bitrate is poor and never really achieves its full capability.

SafeCom.png is for a 54Mbps wifi dongle (driver zd1211rw) attached to a Compaq D510. Quality & signal appear to be the same parameter, and never exceed 35% (even when just a few inches from AP). But the rate is much higher than the Netgear.

Black54.png is a 54Mbps black body dongle from Amazon (it is un-branded), which out-performs everything else. The driver is reported as "usb".

In addition, I've tested a CompaqMini netbook (driver ath9k). This mostly runs OK but every few minutes the rate seems to drop from 54 to 1Mbps for a few seconds, before returning back to 54Mbps.

---

### Post by eltomate on 2011-02-28
Not sure what you're looking for with this post, but I'll reply with what little I know of wifi and linux.

"During 2009 a kernel update/upgrade changed the SafeCom operation such that the highest signal/quality level was limited to 35% (the driver produces the same data for quality & signal on this device)."

Knowing what changed would be necessary to explain this.  Possibly a new driver took over your hardware after the upgrade. Maybe it's just being reported differently (e.g. maybe it was always at 35% but they old driver couldn't detect signal levels correctly).

"During the last 12 months the Netgear WG111 has started to work on Linux, and reports a nice high signal level and quality, but the bit rate is generally only 1 to 11Mb/s."

I have one of those.  It's 1Mb/s on USB 1, and (for me) 18Mb/s on USB2. According to iwconfig, at least.

"Changes to the kernel/Ubuntu occur too frequently for the drivers to be properly maintained."

I have found consistent improvement over the kernel updates.  For instance, today I dug out a bunch of old wireless wifi dongles to see if they work natively now. They do, when not terribly long ago they required ndiswrapper to only occasionally work.  I'm not sure what kind of break down in maintenance you're seeing based on this post, so there's bound to be some kind of misunderstanding here.

"Also the drivers do not appear to report data such as signal, noise & quality in a consistent way."

Actually, hardware doesn't report it in a consistent way, as I understand it.  Windows may normalize it somewhat, but Linux generally just shows exactly what the hardware says.  Personally, I prefer it that way, though I can understand why some may want it standardized.


That said, Linux is still absolutely a work in progress.  I use it because I have need for some of the advanced features, but it's still too rough around the edges for most computer users I know.

---

### Post by SteveDee on 2011-03-04
> **eltomate said:**
> Not sure what you're looking for with this post...

Thanks for your input. This post was just personal comment, but if it promotes debate and leads to better understanding (by me at least) then I guess it serves a purpose. It does at least show the variability in performance for a small selection of wifi devices.

Just how you choose a wifi dongle for Linux, I'm not sure. Many of the low cost devices currently available at stores like Amazon are "mature" designs, some don't even appear to support WPA. But would buying more expensive devices be a guarantee of good performance?

During 2009 I could not find any evidence of changes to the zd1211rw driver used by the SafeCom device, so my assumption at the time was that it was one of the many kernel changes that caused the dramatic change in reported performance. And things have certainly improved for the Netgear device, but it should give 54Mbps when presented with a reasonably strong signal (I see you suffer a similar limitation).

I think I'm right in saying that the wifi parameter commonly used by both Windows and Linux wifi applets is "quality" not signal strength (as is commonly thought to be the case). And quality is calculated with regard to corrupted or dropped packets. Windows drivers are normally supplied by the dongle manufacturer, while Linux drivers originate from a variety of sources, mostly 3rd party.

My results for 2 of the wifi hardware types show that wifi can work well with Linux, so maybe its better to buy a WiFi dongle based upon the driver that it uses, rather than the product make & model?

Although I work with MS Windows, at home I have been using Linux exclusively for almost 3 years, so I'm not about to jump ship.

---


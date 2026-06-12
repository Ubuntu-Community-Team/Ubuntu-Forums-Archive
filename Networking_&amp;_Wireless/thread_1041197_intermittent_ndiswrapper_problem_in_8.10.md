---
title: "intermittent ndiswrapper problem in 8.10"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by murlig on 2009-01-16
Hi all,

I recently upgraded from 7.10 to 8.10 and I have been having intermittent problems with wireless connectivity. (I also did a clean install and the problem remains).

After reading multiple reports and trying both network manager and WICD, I have determined that the problem is with **ndiswrapper not configuring my wlan0 interface correctly at bootup intermittently.**. Meaning, wlan0 is configured at times, not at other times.

In the same box, I have PCLOS07 and have never had a problem with wlanX detection. Neither was it a problem with 7.10.

Here's a snippet from dmesg | grep -e ndis -e wlan from 8.10 when things work.
[   17.144249] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.937566] ndiswrapper: driver mrv8335 (eHome,08/22/2005,3.2.1.3) loaded
[   17.938328] ndiswrapper 0000:01:0d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.950048] ndiswrapper: using IRQ 17
[   18.409210] wlan0: ethernet device 00:19:5b:03:6b:de using NDIS driver: mrv8335, version: 0x3020002, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   18.409258] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.414494] usbcore: registered new interface driver ndiswrapper
[   38.698615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.582462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.522431] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.412065] wlan0: no IPv6 routers present

Now here are the messages when they dont work , again with 8.10
[   17.651001] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   18.348266] ndiswrapper: driver mrv8335 (eHome,08/22/2005,3.2.1.3) loaded
[   18.349032] ndiswrapper 0000:01:0d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.360772] ndiswrapper: using IRQ 17
[   18.646140] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   18.646162] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   18.646203] ndiswrapper (mp_halt:262): device dd010480 is not initialized - not halting
[   18.646211] ndiswrapper: device eth%d removed
[   18.646276] ndiswrapper 0000:01:0d.0: PCI INT A disabled
[   18.646315] ndiswrapper: probe of 0000:01:0d.0 failed with error -22
[   18.651493] usbcore: registered new interface driver ndiswrapper

Here's the same message from PCLOS07 (working)
ndiswrapper version 1.48 loaded (smp=yes, preempt=no)
ndiswrapper: driver mrv8335 (eHome,08/22/2005,3.2.1.3) loaded
ndiswrapper: using IRQ 18
wlan0: ethernet device 00:19:5b:03:6b:de using NDIS driver: mrv8335, version: 0x3020002, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
usbcore: registered new driver ndiswrapper
ADDRCONF(NETDEV_UP): wlan0: link is not ready
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present

I am also attching complete dmesg output from PCLOS07 when it works and Ubuntu 8.10 when wlanX is not configured.

I would be happy to provide any more information.  Gets real frustrating when the driver is initialized at times and not at times!

thanks

---


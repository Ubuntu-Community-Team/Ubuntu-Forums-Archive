---
title: "D-Link Wireless USB - no networks found..."
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Victormd on 2010-02-21
Found very similar threads but none apply to my USB dongle so... My USB dongle is recognized but it won't find any networks. Here's what I've done so far (this is on *_Mythbuntu_*):
**lsusb**
> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00f9 Microsoft Corp.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 07d1:3c10 D-Link System
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 2304:0225 Pinnacle Systems, Inc. [hex]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**iwconfig**
Quote:
> lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11abgn ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=26 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
I've set: **sudo iwconfig wlan0 txpower** to 26 (the max before getting an error) and this is the result from **sudo iwlist wlan0 scan**
> wlan0 No scan results
**dmesg|grep ar91**
> [ 8.231284] usb 2-6: firmware: requesting ar9170.fw
[ 9.184136] Registered led device: ar9170-phy0::tx
[ 9.184148] Registered led device: ar9170-phy0::assoc
[ 9.184167] usbcore: registered new interface driver ar9170usb

I was able to connect at one point but then lost the connection and haven't been able to get a list of networks or any connection since... Suggestions??

---

### Post by chili555 on 2010-02-21
What do these tell us:```
dmesg | grep wlan
dmesg | grep firmware
```Thanks.

---

### Post by Victormd on 2010-02-21
Sorry for the delay... had to step out for a sec.
Not sure what happened - after about 4 days without wireless, it misteriously came back... the same way it went away, I didn't do anything other than setup some channels in mythtv and I highly doubt that it has anything to do with it... Go figure... Nontheless, here are the outputs:
**dmesg | grep wlan**
> [   11.806128] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.951264] wlan0: authenticate with AP 00:1c:df:d9:5c:07
[   28.953037] wlan0: authenticated
[   28.953041] wlan0: associate with AP 00:1c:df:d9:5c:07
[   28.955409] wlan0: RX AssocResp from 00:1c:df:d9:5c:07 (capab=0x431 status=0 aid=1)
[   28.955412] wlan0: associated
[   28.960597] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.210030] wlan0: no IPv6 routers present
**dmesg | grep firmware**
> [    7.631324] cx18 0000:03:0a.0: firmware: requesting v4l-cx23418-cpu.fw
[    8.148411] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[    8.170051] usb 2-6: firmware: requesting ar9170.fw
[    8.183825] cx18 0000:03:0a.0: firmware: requesting v4l-cx23418-apu.fw
[    8.430705] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[    8.651295] cx18 0000:03:0a.0: firmware: requesting v4l-cx23418-cpu.fw
[    8.848634] cx18 0000:03:0a.0: firmware: requesting v4l-cx23418-apu.fw
[    9.211789] cx18 0000:03:0a.0: firmware: requesting v4l-cx23418-dig.fw
[    9.544095] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[    9.574905] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)


---

### Post by chili555 on 2010-02-21
> [ 28.955412] wlan0: associatedLooks like you are golden. Enjoy!

---

### Post by Minzor on 2010-02-28
Sorry for highjacking this Thread.

I googled around but could get no further Information.

I have a TP-Link WN821N USB Dongle which also uses the ar9170 Chipset, it is running ok since 2.6.32 Kernel Drivers. The Dongle runs stable about several hours with WPA or WPA2. My Router is a Netgear WNR3500L wich i tested with stock and dd-wrt Rom.

Now to my Question.

Which transferrates do you get with your ar9170 driven USB Dongles?

I tested transferrates with netio and get very low transferrates.

from windows to Linux:

NETIO - Network Throughput Benchmark, Version 1.26
(C) 1997-2005 Kai Uwe Rommel

TCP connection established.
Packet size  1k bytes:  494 KByte/s Tx,  71 KByte/s Rx.
Packet size  2k bytes:  524 KByte/s Tx,  72287 Byte/s Rx.
Packet size  4k bytes:  729 KByte/s Tx,  71953 Byte/s Rx.
Packet size  8k bytes:  695 KByte/s Tx,  79 KByte/s Rx.
Packet size 16k bytes:  709 KByte/s Tx,  70 KByte/s Rx.
Packet size 32k bytes:  750 KByte/s Tx,  81 KByte/s Rx.
Done.

Did someone experienced better transferrates, and if yes, how?

P.S: Under Windows XP i get about 7-8 MB/s.

cu

---


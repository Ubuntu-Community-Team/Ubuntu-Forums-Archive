---
title: "Cannot get DHCP IP assigned - Belkin F5D7050 ver. 4000 USB wireless adapter."
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by fnordcircle on 2008-12-06
I've been struggling with this for a while now, hopefully someone can help.

I've got a Ubuntu 8.10 box with a Belkin zd1211-based USB adapter in it. I've tried with 8.04 and upgraded to 8.10 because it wasn't working and because I planned on doing so anyways.

On boot up the driver sees the device:
[ 22.294101] zd1211rw 3-1:1.0: phy0
[ 22.294157] usbcore: registered new interface driver zd1211rw
[ 27.619682] zd1211rw 3-1:1.0: firmware version 4725
[ 27.644008] zd1211rw 3-1:1.0: zd1211b chip 050d:705c v4810 high 00-1c-df AL2230_RF pa0 g--N-

It sees the AP:
wlan0 IEEE 802.11g ESSID:"fnord"
Mode:Managed Frequency:2.437 GHz Access Point: 00:19:5B:D5:F5:59
Bit Rate=24 Mb/s Tx-Power=0 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Encryption key:3735-3239-3137-3334-3530
Link Quality=100/100 Signal level=56/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

It fails to get a dhcp address, though. I've checked the WEP key I'm using a ton of times and I don't see any discrepancy. I've entered the key as I have it recorded on other laptops and had no issues getting an IP.

The router logs show that it is seeing the host but there is no dhcp address being given out:

[INFO] Thu Jul 03 05:23:40 2008 Wireless system with MAC address 001CDFDD2E08 associated

I've got plenty of IPs and I'm not getting any messages on the router about failed authentication or anything. Right now I have it set to Open Key authentication.

Anyone have any suggestions? This is a Belkin F5D7050 running in an iBook G4. I feel like I'm so close, I just can't get an IP. Manually assigning an IP still doesn't let it converse with other hosts on the subnet.

This is my /etc/network/interfaces relevant to this interface:

auto wlan0
iface wlan0 inet dhcp
wireless-essid fnord
wireless-key s:7529173450

I've read several 'just use this GUI tool' guides online but I'm running the server edition here so no GUI.

Any help would be greatly appreciated.

---

### Post by MaindotC on 2009-02-05
I also use this and I cannot get the device to operate under a personal WEP or WPA.  However, I used this on my campus that uses WPA2-Enterprise (or some variant of it) and I didn't have any problems connecting.  It's so odd - I was living in the dorms on campus connecting to the school's WPA2 access points and it worked fine - now I live off campus and all I'm trying to do is lock down our wireless network but I can't because the Belkin F5D7050 doesn't accept, and won't even find, WPA.

I have a WUSB600N that when I plug in it can see WPA networks unlike the F5D7050.

---


---
title: "Cannot connect to AirPort Express WAP"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by srclakejake on 2009-10-03
Hello,
I just installed Linux for the first time. I'm running Ubuntu 8.10 Intrepid Ibex. I have not been able to connect to our wireless network, which uses an Apple AirPort Express as its WAP. I have looked through the forums here, and done some searches via google, butI haven't been able to find any posts that address my problem. Apologies if I missed such an entry here.

I am connected from two other machines on our network - one a Windows XP box, one running OS X. I have been able to connect from the ubuntu box to other wireless networks in range (was able to browse to cnn.com), but they are extremely slow, and i don't want to use my neighbor's connections permanently. 

The linux box seems to see our network, but when i try connecting to it, i just eventually get a pop-up message that says 'The network connection has been disconnected'. 

I ran lshw. Here is the info for the Wireless NIC:

*-network
description: Wireless Interface
product: RT2600 802.11 MIMO
vendor: RaLink
physical id: 7
bus info: pci@0000:02:07.0
logical name: wmaster0
version: 00
serial: 00:16:b6:5d:5d:16
width: 32 bits
clock: 33 MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless

I also ran iwconfig (no args). Here is the output:

lo                no wireless extensions

wmaster0     no wireless extensions

wlan0          IEEE 802.11bg ESSID:"<shows network name>"
                  Mode:Managed Frequency:2.412 GHz  Access Point: Not-Associated
                  Tx-Power=13 dBm
                  Retry min limit:7   RTS thr= off  Fragment thr=2352 B
                  Power management: off
                  Link quality:0  Signal level:0  Noise level:0
                  Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
                  Tx excessive retries:0  Invalid misc:0  Missed beacon:0

pan0           No wireless extensions


Does anyone know how to fix this? Any help is greatly appreciated.

Thanks

---

### Post by srclakejake on 2009-10-04
After some more troubleshooting, i found the problem to be with the Airport Express. I replaced it with a linksys router, and all is working fine now.

---


---
title: "Wireless networking problem with NetComm NP545"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by capnjim on 2009-02-01
Hi. I have just set up a box running Ubuntu Studio 8.10 (32-bit) and am having major problems getting my NetComm NP545 USB wireless stick to work.

On my Mandriva 2009.0 (KDE) box the stick is recognised and works no problems, so the hardware is not faulty.

Having no out-of-the-box success with Ubuntu, I have installed ndiswrapper and followed the sticky help in this forum, which has been very useful. I have done everything except compile my own binaries.

Where it is at is the stick is recognised and appears to be configured. Here is the output of ndiswrapper -l:

james@soundbox:~$ ndiswrapper -l
rt73 : driver installed
	device (148F:2573) present (alternate driver: rt73usb)

Checking dmesg gives this:

james@soundbox:~$ dmesg | grep -e ndis -e wlan
[   18.564683] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.320966] ndiswrapper: driver rt73 (NetComm,01/12/2006, 1.00.04.0000) loaded
[   19.921289] wlan0: ethernet device 00:60:64:1e:b4:31 using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 148F:2573.F.conf
[   19.921899] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.921998] usbcore: registered new interface driver ndiswrapper
[   39.604047] wlan0: no IPv6 routers present

And finally, ifconfig gives:

wlan0     Link encap:Ethernet  HWaddr 00:60:64:1e:b4:31  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:64ff:fe1e:b431/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10163 (10.1 KB)  TX bytes:3846 (3.8 KB)

I have turned off encryption on my router to eliminate it as a possible problem.

The stick shows up, my router shows it as being attached, lights flash etc, but I have no comms, cannot even ping.

If anyone can throw me some advice I would be most grateful.

---

### Post by Hemal on 2009-07-24
Hi there,

Did you get this USB stick going after all?

Thanks

---


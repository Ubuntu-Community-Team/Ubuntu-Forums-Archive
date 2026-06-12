---
title: "TP-LINK tl-wn7200nd very slow and not connect on G or N mode..."
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by zokratez on 2011-06-28
Hi all!

I have a tl-wn7200nd USB wireless antena that use RT3070 driver...

Also I have a original wireless card, realteck that use RTL8187B driver...

The prblem is that I cannot connect to my router on G or N mode, and the connection is very low...

Here is thedmesg | grep -e rt2 -e rt3

[HTML]
[   31.989544] Registered led device: rt2800usb-phy0::radio
[   31.989602] Registered led device: rt2800usb-phy0::assoc
[   31.989632] Registered led device: rt2800usb-phy0::quality
[   31.989998] usbcore: registered new interface driver rt2800usb
[   31.991866] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   32.000373] usbcore: registered new interface driver rt2870
[14025.889847] Registered led device: rt2800usb-phy2::radio
[14025.889925] Registered led device: rt2800usb-phy2::assoc
[14025.889993] Registered led device: rt2800usb-phy2::quality
[19213.864638] Registered led device: rt2800usb-phy3::radio
[19213.864721] Registered led device: rt2800usb-phy3::assoc
[19213.864793] Registered led device: rt2800usb-phy3::quality
[/HTML]

And lsusb:

[HTML]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 005: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/HTML]

So the iwconfig:

[HTML]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:"Centauro"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:AB:D4:A0   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:97  Invalid misc:120   Missed beacon:0
[/HTML]

How you can see my wlan3 support 802.11bgn and the router to... Wath could be?

Thaks in advance!

---

### Post by zokratez on 2011-06-29
Nothing?

---


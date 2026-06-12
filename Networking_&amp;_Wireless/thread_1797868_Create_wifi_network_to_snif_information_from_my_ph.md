---
title: "Create wifi network to snif information from my phone"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by raffaele181188 on 2011-07-05
I want to monitor my Android phone's network traffic over WiFi.
More specifically, I'm interested in which servers are queried (possibly silently) while my phone is connected. How can I accmplish it?

I have installed Wireshark on my box, and have a working usb adapter. How can I make my Ubuntu act like a router, so I will be able to snif packets through Wireshark?

---

### Post by jmoorse on 2011-07-12
Due to the broadcast nature of Wifi connecting your phone to your existing wifi network will allow a box connected to the same network to see the traffic through a sniffer.

---

### Post by raffaele181188 on 2011-07-12
Even if wifi is encrypted (WPA2)? How can I snif all trafic coming from specific IP?

---

### Post by jmoorse on 2011-07-12
Yes, if you are joined to the network you have the encryption key.  I have only done this with WEP back in the day but the principle _should_ be the same.  I know that WPA does per-packet-encryption...  Give it a shot and let us know.

In wireshark you can use the display filter format:

ip.src == 10.10.10.10
ip.dst == [ip] is also valid.

To break down by a given IP src or dst.

---

### Post by raffaele181188 on 2011-07-12
Do I need put my adapter in some special mode?

---

### Post by raffaele181188 on 2011-07-12
I see no traffic from 192.168.1.7 (which is my phone IP)
Do I need some special configuration?

---

### Post by Grenage on 2011-07-12
I believe you may require the wifi client to be in promiscuous mode, otherwise it won't process data not intended for it.  Not all wifi devices have that mode, but most decent ones have it.

---

### Post by raffaele181188 on 2011-07-12
I already checked that option in Wireshark.
Maybe my card doesn't support promiscuous mode? How can I test it?

---

### Post by Grenage on 2011-07-12
It's possible; unfortunately I'm not aware of how to check for support from the system itself.  If possible, check the adapter on-line for mode support - it might be listed as *monitor* mode.

---

### Post by raffaele181188 on 2011-07-12
If I try to put my card in monitor mode by hand it says "unsupported mode"
So I won't be able to snif traffic with this card

---

### Post by Grenage on 2011-07-12
It looks that way.  I have (somewhere) a USB Ralink adapter and 'cantenna'; I had to get the external adapter because my HP's in-built device did not support promiscuous mode.

If you can get hold of any other adapter for the duration of your testing, you might be in luck.  I was actually thinking of doing the same thing as you, with my iphone.

---


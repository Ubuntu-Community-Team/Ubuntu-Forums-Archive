---
title: "wlan usb stick"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by Wildflower11 on 2009-02-04
hy everyone.

i bought a wlan usb stick and i would like to use it :). if i plug it in, and type "iwconfig", it says:

```

lo        	no wireless extensions.

eth0    	IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          	Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid
          	Bit Rate=1 Mb/s
          	Link Quality:0  Signal level:0  Noise level:0
	        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          	Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```

unfortunately i don't understand any of these. should this thing be working now? or how can i make it work?

thank you

---

### Post by icheyne on 2009-02-05
Which USB wifi stick is it? Many are incompatible with Ubuntu.

---

### Post by xopher_mc on 2009-02-05
in terminal run the command 

lsusb

That will give you the device number ect. and you can find compatibility.

---


---
title: "Problem connecting R8187 card to wireless"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by guedesav on 2009-01-21
I've got a Cisco Linksys WRT110 router working here at home, and it is doing it's job very good regarding wired connections on Windows and Linux equally, and also wireless on Vista. But for some unknown reason, I can't seem to connect my laptop to the network wirelessly using Ubuntu.

My wireless card is a Realtek 8187b, using a downloaded and compiled driver found here in this same forum(r8187 + iee80211 drivers, the same showed in [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)). The driver seems to work okay, but there's no way I can make it connect to the network. I've tried wicd and network-manager, with no result. I've tried WPA2, WPA, WEP and even no encryption at all, and, oddly, the connection can't be stablished. Also, wpa_supplicant says the accespoint has "no WPA/RSN IE", even when it is working with WPA2 security.

Unfortunately, I can't provide log messages now, for I'm posting from Windows Vista, but I can provide any information that's needed by request.

Thanks in advance.

---

### Post by ajmorris on 2009-01-22
hi there,
(i am assuming that you are using a USB card - your thread is confusing, as in the title you say R8187 and in your post you say rtl8187b - rtl8187b is USB, so i am assuming you have a usb card?)
as of the linux 2.6.27 kernel, the rtl8187 usb driver is in the kernel, and you do not need that patch. Beware, it is experimental, and can break your hardware, if you are using a 32bit system, it may be more beneficial to use the ndiswrapper driver (there is no 64bit xp driver for that chipset, and vista is not supported in ndiswrapper /yet/)

However, if you're sticking with the experimental driver, check to make sure that you can pick up your access point broadcast, via:
```
sudo iwlist scanning
```
also, what is the output of:
```
sudo ifconfig && sudo iwconfig
```

Also, via my own personal experience with that chipset, i found NetworkManager to be the best one for it, however, it was fiddly. on startup, i had to start the NetworkManager daemon, and then start the dhcdbd daemon, as this was the only dhcp client that i could get to work with the card. once those 2 daemons were started, it connected to my network quite easily. However, this driver is often a pain, and i really do recommend ndiswrapper for it, if you have a 32bit OS.


AJ

---

### Post by guedesav on 2009-01-22
Okay, thanks for the answer, but I now found out how to connect to the wireless: I changed to WEP. I'll tell why.

First, the driver is r8187, I'm using kernel 2.6.22 , and really afraid to upgrade by now(really, what I don't need is to struggle to make my system recognize more hardware than I already had to). It is a USB card, indeed. Here is lsusb's output:

```

Bus 003 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8189 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer_Realtek
  iProduct                2 RTL8187B_WLAN_Adapter
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  [...]

```

...and there it goes. Anyway, the card is working fine. Very fine. There were two problems, though.

First, the router wasn't being detected as WPA2. Here's a piece of the output I've got for trying to connect to it via wpa_supplicant(the essid is "basement"): 

```

Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=0): [NULL]
Trying to get current scan results first without requesting a new scan to speed up initia
l association
Received 189 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:21:29:e9:c2:39 ssid='basement' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:21:29:e9:c2:39 ssid='basement' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - non-WPA network not allowed
No suitable AP found.

```

WICD and NetworkManager also detected its encryption as being WEP, for reasons I can't understand. I saw in some discussion list it has to do with the WPA IE not being sent with the beacon, but I couldn't find where on the router's configuration interface.

Second: NetworkManager wasn't able to use WPA2 encryption. No, really. I installed it, and it featured only three kinds of WEP and LEAP. Tried to install the newet version from SVN and... it was a mess. In the end, apt-get almost removed my entire system, and I wasn't even able to install libglade2(required for the newest version of the applet). And it didn't work.

By then I had already tried to connect using the former version(0.6) or NM, but only with WEP. So I simply set my router to WEP, using a Hex key, and with MAC filtering. I don't even need NetworkManager or WICD to make the connection, just the good old "ifup". And here I am, on the internet!

So, sorry for the confusing thread(r8187 is the name that appears in lsmod), but the problem was mainly in the router, and not in the card, it turns out. I even found a thread here(one that I can't seem to find again) complaining about this same router, WRT110, so it seems it's not only with me.

But, in the end, the problem is solved. Thanks a lot, and sorry for all the mess. I rest my case.

---

### Post by TeflonTrout on 2009-04-18
Your NOT alone, seems like the WRT110 is being a beast for everyone who buys it.  If your solution works for me too I'll...I dunno, I probably will just be grateful.  Maybe enough to tie your shoes for you once, if you asked.:D

---


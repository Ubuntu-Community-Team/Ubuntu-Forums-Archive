---
title: "Philips PTA01 WiFi dongle"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by venturax on 2012-11-15
I'm trying to connect this dongle to my PC, so i can use it as a WiFi.

My raspberry pi, shows the exact same behavior, so I'm using this as my dev environment.

According to [http://wikidevi.com/wiki/Philips_PTA01](http://wikidevi.com/wiki/Philips_PTA01), it uses the ath9k_htc driver

I can see my syslog detects the Dongle

```

raspbmc kernel: [  162.024209] usb 1-1.2: new high-speed USB device number 5 using dwc_otg
raspbmc kernel: [  162.172250] usb 1-1.2: New USB device found, idVendor=0471, idProduct=209e
raspbmc kernel: [  162.172279] usb 1-1.2: New USB device strings: Mfr=16, Product=32, SerialNumber=48
raspbmc kernel: [  162.172294] usb 1-1.2: Product: PTA-01
raspbmc kernel: [  162.172304] usb 1-1.2: Manufacturer: PHILIPS TV
raspbmc kernel: [  162.172315] usb 1-1.2: SerialNumber: 10

```

As the ath driver doesnt know the idVendor and idProduct, thus not loading the firmware, i patched the driver with the correct information.

This results in the dongle getting modprobed and firmware is loaded

```

raspbmc kernel: [  164.402403] cfg80211: Calling CRDA to update world regulatory domain
raspbmc kernel: [  167.030904] cfg80211: World regulatory domain updated:
raspbmc kernel: [  167.030935] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
raspbmc kernel: [  167.030956] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
raspbmc kernel: [  167.030973] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
raspbmc kernel: [  167.030989] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
raspbmc kernel: [  167.031004] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
raspbmc kernel: [  167.031020] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
raspbmc kernel: [  168.569983] usb 1-1.2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
raspbmc kernel: [  169.608383] ath9k_htc 1-1.2:1.0: ath9k_htc: Target is unresponsive
raspbmc kernel: [  169.608423] Failed to initialize the device
raspbmc kernel: [  169.609104] ath9k_htc: probe of 1-1.2:1.0 failed with error -22
raspbmc kernel: [  169.743582] usbcore: registered new interface driver ath9k_htc

```

also lsusb provides the following:

```
Bus 001 Device 005: ID 0471:209e Philips (or NXP) PTA01 Wireless Adapter
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1

  bcdUSB               2.00                                                                                                                                                                           [73/1855]
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0471 Philips (or NXP)
  idProduct          0x209e PTA01 Wireless Adapter
  bcdDevice            1.08
  iManufacturer          16 
  iProduct               32 
  iSerial                48 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           60
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

Any ideas what to do next? As the dongle works with my philips tv, there must some linux support, but i havent been able to locate it.

One next step could be to ask Philips for the kernel source for my tv, which they should provide..

Any ideas appriciated

---

### Post by chili555 on 2012-11-15
I hate to answer when I don't have an answer, but only a couple of ideas. First, we recently patched ath9k to recognize a new usb.id and it needed to be done in three places, not just one. Here is the thread: [http://ubuntuforums.org/showpost.php?p=12201881&postcount=35](http://ubuntuforums.org/showpost.php?p=12201881&postcount=35)

I don't know how you patched the ath9k_htc driver, but you may need to look at more than one file.

Second, I notice modinfo ath9k_htc mentions two firmware files. I suggest you make sure both are present in /lib/firmware.> modinfo ath9k_htc
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
[COLOR="Red"]firmware:       htc_9271.fw
firmware:       htc_7010.fw[/COLOR]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
<snip>

---

### Post by m86 on 2012-11-15
Your log states that **ath9k_htc** is trying to load **htc_7010.fw**. This is not the correct firmware for this device (AR9271 devices use **htc_9271.fw**). The most obvious explanation for this would be that, when you added the USB ID, you flagged the device as an AR7010 device.

If you did indeed edit the source to include the new USB ID, it should look like the following...
```
{ USB_DEVICE(0x0471, 0x209e) },
```
... whereas devices using AR7010 + (AR9280 / AR9287) will be included as...
```
{ USB_DEVICE(0x0471, 0x209e),
	  .driver_info = AR9280_USB },
```
or
```
{ USB_DEVICE(0x0471, 0x209e),
	  .driver_info = AR9287_USB },
```

---

### Post by venturax on 2012-11-16
> **m86 said:**
> Your log states that **ath9k_htc** is trying to load **htc_7010.fw**. This is not the correct firmware for this device (AR9271 devices use **htc_9271.fw**). The most obvious explanation for this would be that, when you added the USB ID, you flagged the device as an AR7010 device.

If you did indeed edit the source to include the new USB ID, it should look like the following...
```
{ USB_DEVICE(0x0471, 0x209e) },
```
... whereas devices using AR7010 + (AR9280 / AR9287) will be included as...
```
{ USB_DEVICE(0x0471, 0x209e),
	  .driver_info = AR9280_USB },
```
or
```
{ USB_DEVICE(0x0471, 0x209e),
	  .driver_info = AR9287_USB },
```

What i forgot to mention, was that I've already tried to load both firmwares. Initially, if I dont add the .driver_info, it automatically picks the **htc_9271.fw**, as expected. However the result is the same, that it cant initialise the device.

The file I've changed is hif_usb.c, but as chili555 mentions, there might be more changes needed
```
diff --git a/drivers/net/wireless/ath/ath9k/hif_usb.c b/drivers/net/wireless/ath/ath9k/hif_usb.c
index 77c8ded..4c48483 100644
--- a/drivers/net/wireless/ath/ath9k/hif_usb.c
+++ b/drivers/net/wireless/ath/ath9k/hif_usb.c
@@ -39,6 +39,7 @@ static struct usb_device_id ath9k_hif_usb_ids[] = {
        { USB_DEVICE(0x040D, 0x3801) }, /* VIA */
        { USB_DEVICE(0x0cf3, 0xb003) }, /* Ubiquiti WifiStation Ext */
        { USB_DEVICE(0x057c, 0x8403) }, /* AVM FRITZ!WLAN 11N v2 USB */
+        { USB_DEVICE(0x0471, 0x209e) }, /* PHILIPS PTA01 */
 
        { USB_DEVICE(0x0cf3, 0x7015),
          .driver_info = AR9287_USB },  /* Atheros */

```

---


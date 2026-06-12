---
title: "USB wireless card - Help"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by ether3al on 2011-08-25
Hi All,

I recently moved my Ubuntu machine to a virtual host using virtual box. Since doing this my Ubiquiti SR71-USB no longer works. Previously on the dedicated machine the card worked perfectly, now i cannot get the device to bring up an interface.

lsusb -v output:
```
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0cf3 Atheros Communications, Inc.
  idProduct          0x9170 AR9170 802.11n
  bcdDevice            1.03
  iManufacturer          16 ATHER
  iProduct               32 USB2.0 WLAN
  iSerial                48 12345
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
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
      bNumEndpoints           4
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
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 002: ID 80ee:0021  

```

lsmod output
```
Module                  Size  Used by
ath9k                 103633  0 
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
nls_utf8               12493  1 
isofs                  39571  1 
vesafb                 13449  1 
carl9170               76967  0 
ar9170usb              53679  0 
mac80211              257001  3 ath9k,carl9170,ar9170usb
ath                    19141  4 ath9k,ath9k_hw,carl9170,ar9170usb
cfg80211              156212  5 ath9k,carl9170,ar9170usb,mac80211,ath
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  0 
joydev                 17322  0 
soundcore              12600  1 snd
psmouse                73312  0 
serio_raw              12990  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e1000                 101089  0 
ahci                   21591  2 
libahci                25548  1 ahci

```

This is some highlights from dmesg:
```
[    6.737244] cfg80211: Calling CRDA to update world regulatory domain
[    6.760361] cfg80211: World regulatory domain updated:
[    6.760361] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.760361] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.760361] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.760361] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.760361] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.760361] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.173251] usb 1-2: reset full speed USB device using ohci_hcd and address 3
[    8.769478] usbcore: registered new interface driver ar9170usb
[    8.801839] usbcore: registered new interface driver carl9170

[    9.816279] usb 1-2: USB setup failed (-110).
```

Thanks in advance.

---

### Post by nm_geo on 2011-08-25
Try this link.

[http://linuxwireless.org/en/users/Drivers/ar9170](http://linuxwireless.org/en/users/Drivers/ar9170)

---


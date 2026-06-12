---
title: "LeadTek DTV2000DS Plus not loading drivers"
date: 2012-09-20
forum: Mythbuntu
---

### Post by AJuice42 on 2012-09-20
Hi everyone,

I recently bought a Leadtek DTV2000DS Plus (dual-tuner PCI) to add to my existing backend, however it does not appear to work at all. Before I bought it, I had read up about the card, and expected it to work fairly easily, however, I later realised that all previous discussion appears to have been about the non-plus version, and I had bought an updated version. 

Originally thinking the existing card and new card were conflicting and not wanting to muck around with the working backend too much, I installed the card to an old test machine (~3GHz P4) , and installed a clean version of MythBuntu 12.04.1 32-bit. Currently I find that :

- The 'Additional Drivers' dialogue does not list available DVB drivers or firmware to install (just the typical proprietary graphics drivers)
- lsusb shows both LeadTek tuners as expected
- /dev/dvb does not exist

I have tried using the graphical installer located [here]("https://github.com/map7/tvconfig"), which completes OK, but does not work. I have also tried building the V4L-DVB drivers as suggested [here]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") on linuxtv.org, which seems to build and install without error, and verifying a copy of the firmware located at /lib/firmware. Rebooting does not load the correct modules, and modprobing them loads them without error, but lsmod tells me they are not being used. Note that most of this was done prior to me realising there was a 'plus' version, and that I had it.

dmesg seems to say nothing about finding the devices, or loading firmware for them, as typically seems to happen with these cards. (often says something like 'found blah in cold state, searching for firmware' or something)

The LeadTek website tells me that this card has the same chipsets (AF9015 + AF9013) as the non-plus version, so I figure that this should still work. I was also wondering if the fact that the device name in lsusb has changed in this model could be the root of these issues? Other posts people have made of various forums seem to suggest it should be either a hex number or the numeral 2. In the case of this card it says 'iProduct                2   WinFast DTV2000 DS Plus'

Please let me know if I explained anything poorly, am asking in the wrong place, am missing something obvious (I work with macs mostly, and am fairly novice with linux) or you require more info.

Also note that I've been carefully shutting down, removing power and cold booting as suggested in other discussions.

Thanks, 

-AJuice

PS, here is the lsusb of one of the LeadTek tuners.

> Bus 002 Device 002: ID 0413:6f12 Leadtek Research, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0413 Leadtek Research, Inc.
  idProduct          0x6f12 
  bcdDevice            1.00
  iManufacturer           1 Realtek
  iProduct                2 WinFast DTV2000 DS Plus
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB2.0-Bulk&Iso
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)


---

### Post by charliebr0wn on 2012-10-02
I too have this card
i mistakenly replaced a dtv2000ds with the dtv2000ds plus and cannot find drivers for this card anywhere
has anyone got this thing to work in linux? or is it going to ebay

---

### Post by Ibbz on 2012-11-16
Did you have any luck tracking down any drivers for this AJuice? Or any solution using other drivers?

---

### Post by nickrout on 2012-11-16
> **Ibbz said:**
> Did you have any luck tracking down any drivers for this AJuice? Or any solution using other drivers?pretty sure this card is unsupported by linux at present, but the place you really need to look is linuxtv.org wiki.

---

### Post by sparx66 on 2012-12-16
Hi There, same problem.

I looked up the card on the linuxtv website and only bought it when I had checked it would work.
BUT I missed the whole plus thing. (they should have a caveat for that)

First time noob, learning lots about ubuntu/linux/gnu etc but card she no work.

Its funny that MythTv doesn't even create the /dev/dvb directory during the load. is that because it doesn't detect a valid card?

Am I barking up the wrong tree here?

I can try it on win xp, but I hate to admit defeat.

any suggestions?

---

### Post by nickrout on 2012-12-16
Suggestions:

1. If the linuxtv wiki needs changing, then change it! That  is what a wiki is all about!

2. Get a supported card

3. Write a driver

---

### Post by MichaelT40 on 2013-02-02
I have just made the same mistake of buying this card thinking it was supported. However, I think the Leadtek website is wrong and it has a *different chipset* to the non-plus version. It seems to me that it has the Realtek RTL2832U chipset which is partially supported. See the linuxtv wiki. I also suspect that it is very similar to, or possibly a clone of, the Mygica T1800B.

This may mean that it will be possible to get the card working by installing one of the various drivers for the RTL2832U and making it accept the id of the dtv2000ds+. This might be done like this [http://www.ha19.no/usb/]("http://www.ha19.no/usb/").

I have made a few changes to the linuxtv wiki to try to help others avoid this problem.

---

### Post by MichaelT40 on 2013-02-05
I have just managed to get this card working in Xubuntu 12.04. See the [linuxtv wiki page]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS_PLUS") I just made for it.

---

### Post by VeitchJ on 2013-05-13
Has anyone had any luck with this card with ubuntu 13.04?

I downloaded, installed and built the driver from the linuxtv site.

Following the advice above I substituted the 6f11 device ID with 6f12. Built and installed the driver.

There only rtl driver I could find from the build was the dvb_usb_rtl128xxu driver so I loaded that module.
The module loaded but did not provide any new dvb device.

What am I doing wrong? Any thoughts?

---

### Post by jaredquinn on 2013-11-19
Hi VeitchJ,

A prepatched version of the driver that builds with all latest kernels (and Ubuntu supplied sources) can be found at [https://github.com/jaredquinn/DVB-Realtek-RTL2832U](https://github.com/jaredquinn/DVB-Realtek-RTL2832U)

Jared

---

### Post by os2 on 2013-11-27
Hi,
I'm confused.
You're referring to RTL2832U as the tuner or the USB-bridge-demodulator?

I believe it is the demodulator. So does it mean any stick with any tuner but with a RTL2832U demod chip will now work? Or are addiotional drivers needs for the tuners?
I'm thinking R820 AND FC0013 tuners.

---


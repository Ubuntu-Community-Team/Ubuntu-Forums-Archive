---
title: "TV card (DViCO Dual digital 4) no longer found after update"
date: 2009-04-17
forum: Multimedia Software
---

### Post by edgecombe_r on 2009-04-17
I've been running a Mythtv/Ubunto (Intrepid?) system for some 6 weeks with no problems. Yesterday I accepted a few updates via Synaptic, and since then my DViCO Dual digital 4 card is no longer recognised during boot up.

uname shows: Linux TvBox 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

An lsusb -v shows that the card is known to exist (see lsusb segment below).

However /var/log/messages used to contain a number of lines concerning the DViCO card &#8211; and these are no longer there &#8211; so it seems that probing has been broken? 
(See messages segment below).

The list of updates applied is listed below (see updates segment)

I'm not sure where to start looking for the cause of the missing probe activity. Any suggestions &#8211; better still solutions :) &#8211; would be most welcome.

updates applied:

------------------------------
Upgraded the following packages:
doc-base (0.8.16) to 0.8.16ubuntu1
dpkg (1.14.20ubuntu6.1) to 1.14.20ubuntu6.2
dpkg-dev (1.14.20ubuntu6.1) to 1.14.20ubuntu6.2
firefox (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-3.0 (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-3.0-branding (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-3.0-gnome-support (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-gnome-support (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
libavahi-compat-libdnssd1 (0.6.23-2ubuntu2) to 0.6.23-2ubuntu2.1
libicu38 (3.8.1-2) to 3.8.1-2ubuntu0.1
libjasper1 (1.900.1-5) to 1.900.1-5ubuntu0.1
liblcms1 (1.16-10ubuntu0.1) to 1.16-10ubuntu0.2
liblcms1-dev (1.16-10ubuntu0.1) to 1.16-10ubuntu0.2
libnss3-1d (3.12.0.3-0ubuntu5) to 3.12.0.3-0ubuntu5.8.10.1
libsmbclient (2:3.2.3-1ubuntu3) to 2:3.2.3-1ubuntu3.4
libsndfile1 (1.0.17-4) to 1.0.17-4ubuntu0.8.10.1
libssl-dev (0.9.8g-10.1ubuntu2.1) to 0.9.8g-10.1ubuntu2.2
libssl0.9.8 (0.9.8g-10.1ubuntu2.1) to 0.9.8g-10.1ubuntu2.2
linux-headers-2.6.27-11 (2.6.27-11.27) to 2.6.27-11.31
linux-headers-2.6.27-11-generic (2.6.27-11.27) to 2.6.27-11.31
linux-image-2.6.27-11-generic (2.6.27-11.27) to 2.6.27-11.31
linux-libc-dev (2.6.27-11.27) to 2.6.27-11.31
nvidia-common (0.2.4) to 0.2.4.1
openssl (0.9.8g-10.1ubuntu2.1) to 0.9.8g-10.1ubuntu2.2
tzdata (2009b-0ubuntu0.8.10) to 2009d-0ubuntu0.8.10
xserver-common (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-core (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-video-intel (2:2.4.1-1ubuntu10.3) to 2:2.4.1-1ubuntu10.4
xulrunner-1.9 (1.9.0.7+nobinonly-0ubuntu0.8.10.1) to 1.9.0.8+nobinonly-0ubuntu0.8.1&#8203;0.1
xulrunner-1.9-gnome-support (1.9.0.7+nobinonly-0ubuntu0.8.10.1) to 1.9.0.8+nobinonly-0ubuntu0.8.10.1

Installed the following packages:
nvidia-180-modaliases (180.11-0ubuntu1~intrepid1)

messages (prior to updates being applied)

-----------------------------&#8203;--------------------------------
<snip... just relevant messgaes extracted below....>
Apr 17 11:56:30 TvBox kernel: [ 10.889861] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
Apr 17 11:56:30 TvBox kernel: [ 10.890073] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr 17 11:56:30 TvBox kernel: [ 11.324690] dvb-usb: schedule remote query interval to 100 msecs.
Apr 17 11:56:30 TvBox kernel: [ 11.324697] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
Apr 17 11:56:30 TvBox kernel: [ 11.324715] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
Apr 17 11:56:30 TvBox kernel: [ 11.324905] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr 17 11:56:30 TvBox kernel: [ 11.728201] dvb-usb: schedule remote query interval to 100 msecs.
Apr 17 11:56:30 TvBox kernel: [ 11.728206] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
Apr 17 11:56:30 TvBox kernel: [ 11.728663] usbcore: registered new interface driver dvb_usb_cxusb
<snip...>

isusb -v output (relevant parts extracted)

-----------------------------&#8203;------------------------------
Bus 008 Device 003: ID 0fe9:db98 DVICO
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 2.00
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 64
idVendor 0x0fe9 DVICO
idProduct 0xdb98
bcdDevice 20.c2
iManufacturer 1 Dvico
iProduct 2 Bluebird
iSerial 4 000020c2
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 99
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0
bmAttributes 0x80
(Bus Powered)
MaxPower 500mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 3
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 1
bInterfaceProtocol 1
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 1
bNumEndpoints 3
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 1
bInterfaceProtocol 1
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 2
bNumEndpoints 3
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 1
bInterfaceProtocol 1
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 1
Transfer Type Isochronous
Synch Type None
Usage Type Data
wMaxPacketSize 0x13f2 3x 1010 bytes
bInterval 1
Device Qualifier (for other device speed):
bLength 10
bDescriptorType 6
bcdUSB 2.00
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 64
bNumConfigurations 1
Device Status: 0x0000
(Bus Powered)

<snip .. 2nd tuner/device also listed>

---

### Post by marcovanb on 2009-04-19
This thread discusses the issue:

[http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103)

at the end

Nick

---


---
title: "sweex 150N Nano / RTL 8188SU on karmic..."
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by Ashrael on 2010-07-15
I have bought today, a Sweex usb 150N nano wifi adapter... When I plug it in, LSUSB gives only this: Bus 001 Device 004: ID 177f:0154. I downloaded the driver from realtek.com and installed realtek-firmware and wireless-tools. When I modprobe for r8192s_usb it loads but... well see for yourself:


> Module                  Size  Used by
r8192s_usb            222456  0 
ieee80211_rsl         126448  1 r8192s_usb
ieee80211_crypt_ccmp     6012  1 ieee80211_rsl
ieee80211_crypt_tkip     9276  1 ieee80211_rsl
ieee80211_crypt_wep     3932  1 ieee80211_rsl
ieee80211_crypt         5024  4 ieee80211_rsl,ieee80211_crypt_ccmp,ieee80211_crypt_tkip,ieee80211_crypt_wep
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
aes_i586                8124  2 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
arc4                    1660  2 
ecb                     2524  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
zd1211rw               45408  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
mac80211              181236  1 zd1211rw
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hwmon_vid               2940  0 
soundcore               7264  1 snd
psmouse                56180  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
cfg80211               93052  2 zd1211rw,mac80211
x_tables               16544  1 ip_tables
nvidia               9586440  36 
i2c_ali15x3             6336  0 
lp                      8964  0 
i2c_ali1563             6368  0 
i2c_ali1535             5792  0 
serio_raw               5280  0 
parport                35340  2 ppdev,lp
uli526x                15564  0 
k8temp                  4188  0 
shpchp                 32272  0 
usb_storage            52544  0 
amd64_agp               9796  1 
ali_agp                 5148  0 
agpgart                34988  3 nvidia,amd64_agp,ali_agp

How do I get this thing to work? Any tips etc welcome...

TIA

---

### Post by Ashrael on 2010-07-15
Some more info about this thing:

lsusb:

> Bus 001 Device 004: ID 177f:0154  
Bus 001 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 002: ID 079b:0062 Sagem XG-76NA
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


hwinfo:


> hal.1: read hal data
  hal: connected to: :1.70
----- hal device list -----
  0: udi = '/org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001_if0'
  usb.interface.number = 0 (0x0)
  usb.interface.class = 255 (0xff)
  usb.interface.subclass = 255 (0xff)
  linux.subsystem = 'usb'
  usb.interface.protocol = 255 (0xff)
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'usb'
  info.product = 'USB Vendor Specific Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.3/usb1/1-1/1-1:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.device_class = 0 (0x0)
  usb.vendor_id = 6015 (0x177f)
  usb.vendor = 'Sweex'
  usb.product = 'USB Vendor Specific Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.3/usb1/1-1/1-1:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001'
  usb.max_power = 500 (0x1f4)
  usb.product_id = 340 (0x154)
  usb.linux.device_number = 4 (0x4)
  usb.num_ports = 0 (0x0)
  usb.speed = 480.000
  usb.serial = '00e04c000001'
  usb.is_self_powered = false
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.can_wake_up = false
  usb.device_revision_bcd = 512 (0x200)

  1: udi = '/org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001'
  info.vendor = 'Sweex'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  info.subsystem = 'usb_device'
  info.product = 'LW154 Wireless 150N Adapter'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.3/usb1/1-1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.device_class = 0 (0x0)
  usb_device.vendor_id = 6015 (0x177f)
  usb_device.vendor = 'Sweex'
  usb_device.product = 'LW154 Wireless 150N Adapter'
  usb_device.product_id = 340 (0x154)
  usb_device.max_power = 500 (0x1f4)
  usb_device.num_ports = 0 (0x0)
  usb_device.linux.device_number = 4 (0x4)
  usb_device.serial = '00e04c000001'
  usb_device.speed = 480.000
  usb_device.version = 2.00000
  usb_device.is_self_powered = false
  usb_device.can_wake_up = false
  usb_device.bus_number = 1 (0x1)
  linux.device_file = '/dev/bus/usb/001/004'
  usb_device.device_revision_bcd = 512 (0x200)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.3/usb1/1-1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_3'

  usb device: name = 1-1
    path = /devices/pci0000:00/0000:00:13.3/usb1/1-1
  usb device: name = 1-1:1.0
    path = /devices/pci0000:00/0000:00:13.3/usb1/1-1/1-1:1.0
    modalias = "usb:v177Fp0154d0200dc00dsc00dp00icFFiscFFipFF"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 255
    bInterfaceProtocol = 255
    if: 1-1:1.0 @ /devices/pci0000:00/0000:00:13.3/usb1/1-1
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x177f
    idProduct = 0x0154
    manufacturer = "Sweex"
    product = "LW154 Wireless 150N Adapter"
    serial = "00e04c000001"
    bcdDevice = 0200
    speed = "480"

P: /devices/pci0000:00/0000:00:13.3/usb1/1-1
  N: bus/usb/001/008
  S: char/189:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:13.3/usb1/1-1
  E: MAJOR=189
  E: MINOR=7
  E: DEVNAME=/dev/bus/usb/001/008
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: DEVICE=/proc/bus/usb/001/008
  E: PRODUCT=177f/154/200
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=008
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Sweex
  E: ID_VENDOR_ENC=Sweex
  E: ID_VENDOR_ID=177f
  E: ID_MODEL=LW154_Wireless_150N_Adapter
  E: ID_MODEL_ENC=LW154\x20Wireless\x20150N\x20Adapter
  E: ID_MODEL_ID=0154
  E: ID_REVISION=0200
  E: ID_SERIAL=Sweex_LW154_Wireless_150N_Adapter_00e04c000001
  E: ID_SERIAL_SHORT=00e04c000001
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ffffff:
  E: DEVLINKS=/dev/char/189:7

P: /devices/pci0000:00/0000:00:13.3/usb1/1-1/1-1:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:13.3/usb1/1-1/1-1:1.0
  E: DEVTYPE=usb_interface
  E: DEVICE=/proc/bus/usb/001/008
  E: PRODUCT=177f/154/200
  E: TYPE=0/0/0
  E: INTERFACE=255/255/255
  E: MODALIAS=usb:v177Fp0154d0200dc00dsc00dp00icFFiscFFipFF
  E: SUBSYSTEM=usb

prop read: /org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001_if0 (failed)

68: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_177f_154_00e04c000001_if0
  Unique ID: ADDn.kjkHOGZjzn5
  Parent ID: k4bc.qNABSq05Ib0
  SysFS ID: /devices/pci0000:00/0000:00:13.3/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: unknown
  Model: "Sweex LW154 Wireless 150N Adapter"
  Hotplug: USB
  Vendor: usb 0x177f "Sweex"
  Device: usb 0x0154 "LW154 Wireless 150N Adapter"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Speed: 480 Mbps
  Module Alias: "usb:v177Fp0154d0200dc00dsc00dp00icFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #63 (Hub)



and from syslog:

> 
Jul 15 21:00:10 bahamut udev-configure-printer: Device vendor/product is 177F:0154
Jul 15 21:00:10 bahamut udev-configure-printer: invalid or missing IEEE 1284 Device ID

Here it seems to think it's a printer????

---

### Post by Ashrael on 2010-07-15
More progress: (don't know if this actually helps/helped)

Since my lsusb output did not reveal the make and model, I decided to add the device to the usb.ids file... Now at least it gives me lsusb output that I would expect...

lsusb:

> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 079b:0062 Sagem XG-76NA 802.11bg
Bus 001 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 002: ID 177f:0154 LW154 Wireless 150N Adapter [Realtek RTL8192SU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

But I do not know if this will bring actual functuality any closer...
ANY HELP IS WELCOME!

TIA!

---

### Post by Ashrael on 2010-07-15
Also take a look here, it is not perfect but it might help..

[http://blog.xff.lt/2009/12/28/canyon-cnp-wf518n2-usb-wireless-linux/comment-page-1/](http://blog.xff.lt/2009/12/28/canyon-cnp-wf518n2-usb-wireless-linux/comment-page-1/)

TIA!

---


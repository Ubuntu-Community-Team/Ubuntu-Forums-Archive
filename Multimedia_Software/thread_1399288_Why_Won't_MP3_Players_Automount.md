---
title: "Why Won't MP3 Players Automount?"
date: 2010-02-05
forum: Multimedia Software
---

### Post by kc8hr on 2010-02-05
I bought myself an inexpensive USB mp3 player the other day, thinking that I could sync it just like I do my digital camera and thumb drives. No such luck.

The player is identified by 'lsusb -vv' as follows:

> Bus 001 Device 005: ID 10d6:1101 Actions Semiconductor Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x10d6 Actions Semiconductor Co., Ltd
  idProduct          0x1101 
  bcdDevice            1.00
  iManufacturer           1 USB 
  iProduct                2 Media Player
  iSerial                 3 4512482adf0fe
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      5 SFF-8070i
      bInterfaceProtocol     80 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

The following is from /var/log/messages
> Feb  5 13:04:57 dojo kernel: [ 6698.045552] usb 1-1.1: new full speed USB dev using uhci_hcd and address 5
Feb  5 13:04:58 dojo kernel: [ 6698.170624] usb 1-1.1: configuration #1 choserom 1 choice
Feb  5 13:04:58 dojo kernel: [ 6698.380552] usbcore: registered new interfaceiver libusual
Feb  5 13:04:58 dojo kernel: [ 6698.477150] Initializing USB Mass Storage dri...
Feb  5 13:04:58 dojo kernel: [ 6698.485363] scsi2 : SCSI emulation for USB MaStorage devices
Feb  5 13:04:58 dojo kernel: [ 6698.491938] usbcore: registered new interfaceiver usb-storage
Feb  5 13:04:58 dojo kernel: [ 6698.491956] USB Mass Storage support register
Feb  5 13:05:03 dojo kernel: [ 6703.490762] scsi 2:0:0:0: Direct-Access     U     Media Player     2.00 PQ: 0 ANSI: 0 CCS
Feb  5 13:05:03 dojo kernel: [ 6703.506059] sd 2:0:0:0: [sdb] 8025009 512-bytardware sectors (4109 MB)
Feb  5 13:05:03 dojo kernel: [ 6703.508689] sd 2:0:0:0: [sdb] Write Protect iff
Feb  5 13:05:03 dojo kernel: [ 6703.517695] sd 2:0:0:0: [sdb] 8025009 512-bytardware sectors (4109 MB)
Feb  5 13:05:03 dojo kernel: [ 6703.520684] sd 2:0:0:0: [sdb] Write Protect iff
Feb  5 13:05:03 dojo kernel: [ 6703.520716]  sdb:
Feb  5 13:05:03 dojo kernel: [ 6703.578781] sd 2:0:0:0: [sdb] Attached SCSI rvable disk
Feb  5 13:05:03 dojo kernel: [ 6703.578903] sd 2:0:0:0: Attached scsi generic3 type 0
Feb  5 13:05:06 dojo kernel: [ 6706.461968] FAT: Did not find valid FSINFO siture.
Feb  5 13:05:06 dojo kernel: [ 6706.461974]      Found signature1 0x00000000 nature2 0x00000000 (sector = 1)
Feb  5 13:20:15 dojo kernel: [ 7614.617211]      Found signature1 0x00000000 nature2 0x00000000 (sector = 1)


'fdisk -l' produces the following
> Disk /dev/sdb: 4108 MB, 4108804608 bytes
127 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Disk identifier: 0x00000000


Can anybody tell me why this device won't automount? I did find a simple-enough solution here, [http://ubuntuforums.org/search.php?searchid=69780664]("http://ubuntuforums.org/search.php?searchid=69780664")

But I sure wish I could get it to 'just work'.

---

### Post by labinnsw on 2010-02-12
What brand is you MP3 player?

I could not check the link you posted. It does not work.

I am not the most proficient at interpreting logs, so please forgive me not reading them.

---

### Post by kc8hr on 2010-02-12
Thanks for the reply.

The player is a Jensen, manufactured by Actions Semiconductor Co., Ltd. in China--of course.

Sorry about the dead link.

---

### Post by chewearn on 2010-02-12
From the kernel log, it found the MP3 player, detected that it's an mass storage class (good), assigned /dev/sdb to the device.

But failed to assign a working partition /dev/sdb1 due to some problem with the filesystem?

If the MP3 has a format function, try formatting it (I assumed you don't have any data in it).

If there is not format function, read the user manual how to format it.

Last resort, try using GParted to format (this carry a small risk of bricking the device, if it requires special formating Windows program).

---

### Post by kc8hr on 2010-02-13
Hi chewearn!

> **chewearn said:**
> From the kernel log, it found the MP3 player, detected that it's an mass storage class (good), assigned /dev/sdb to the device.

But failed to assign a working partition /dev/sdb1 due to some problem with the filesystem?

If the MP3 has a format function, try formatting it (I assumed you don't have any data in it).

If there is not format function, read the user manual how to format it.

Last resort, try using GParted to format (this carry a small risk of bricking the device, if it requires special formating Windows program).

You were right!

The device had no true partitions on it from the factory, although it was formatted as MS-DOS.

I was shoveling through various websites when I found this post on an MP3 player support site:[http://s1-mp3-player.org/Support_and_How_To/linux-support-.html]("http://s1-mp3-player.org/Support_and_How_To/linux-support-.html") Following the simple howto, I nervously used gparted to add a VFAT partition to the device. It wiped the device of files, of course. But when I disconnected the player, it asked "new playlist?", so I let it write a new, empty playlist. Upon reconnecting the device, bang--there it was, automounted just like a thumb-drive. Thankfully, the player's OS is in firmware, and the empty playlist reconstructed the default filesystem. So, I am in business--playing the tunes!

Thanks so much for your help.

Tim:popcorn:

---


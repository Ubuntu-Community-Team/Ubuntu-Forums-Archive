---
title: "Getting MP3 player to work  in Rhythmbox"
date: 2008-07-23
forum: Multimedia Software
---

### Post by mawe3661 on 2008-07-23
I have a iRiver T60 and it is detected as a storage device when I plug it in in the USB-port. However, it would be nice if it showed up as a music player in Rhythmbox. What is missing when it doesn't "work out of the box"?

I did run hal-device to see how it was recognised:
```
margita@margita-laptop:~$ hal-device | grep iriver
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_iriver_MP3_T60_0_0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_iriver_MP3_T60_0_0'  (string)
1: udi = '/org/freedesktop/Hal/devices/storage_serial_iriver_MP3_T60_0_0'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_iriver_MP3_T60_0_0'  (string)
  info.vendor = 'iriver'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_iriver_MP3_T60_0_0'  (string)
  storage.vendor = 'iriver'  (string)
  storage.serial = 'iriver_MP3_T60-0:0'  (string)
  scsi.vendor = 'iriver'  (string)
  info.product = 'iriver MP3 T60'  (string)
  usb_device.product = 'iriver MP3 T60'  (string)

```

Any help would be appreciated!

---

### Post by ethanay on 2010-01-29
Hi Mawe3661,

The T60 can operate in two modes:  

1. MSC (mass storage class) 2. MTP (media transfer protocol, M$)

Explanations
1. OS sees it as a normal USB storage device.  For this purpose, you use the Nautilus file system to drag and drop files and folders directly onto the drive.

2. OS sees it specifically as a media player, and in order to transfer files, you need an MTP-enabled software player (like Rhythmbox).

If your player is in MSC mode (which I believe is default) then it won't work directly with Rhythmbox.  You need to "cross update" it first using the iRiver software, or you can try to do it manually by downloading the 1.03 MTP firmware at this site: 
[http://nyaochi.sakura.ne.jp/iriverupdate/](http://nyaochi.sakura.ne.jp/iriverupdate/)

You should be able to place the .hex file in the root directory of the player, and unplug the player, and it SHOULD automatically install the new firmware.

After that, you need to enable the "mtp players" plugin in Rhythmbox, which is disabled by default.

I can't tell you, because I just killed my T60, and all it displays is "file check error" :( I am hoping to fix it if I can get a complete disk image of a working T60...

---

### Post by mawe3661 on 2010-01-30
Thanks, but what you write only aplies to T60 (and other music devices) sold in the US. The european version are allowed to work as a USB device, which it does. However, it is just that developers have not put it in their list of music devices, now it works as a plain USB-stick. However, I have another iRiver device bought in the US which I had to fix using your description. It's the WTOs fault, is it not? Or is it due to special US laws?

Thanks,
Martin

---

### Post by ethanay on 2010-01-30
Every Ubuntu T60 user I know of has used it only as a MSC device, so I am unsure.  I thought the EU/US versions were the same.  But it may be that it is only the French/US versions.  You can load different firmware to convert it to MTP mode -- try the US or French MTP firmware?

If it is only a matter of Rhythmbox recognizing it as a device, then there are a few tutorials that you can use to hack your way into it.  I personally don't think it is worth it, since the device has only limited playlist support.  All you need is FATSort to sort the files in their correct order after they are loaded onto the player, and you are done.

However, if you have it in MTP mode and Rhythmbox is set up, your problem could possibly be a simple permissions issue?
[http://ubuntuforums.org/showthread.php?t=911505](http://ubuntuforums.org/showthread.php?t=911505)

Try loading your MTP player as root, e.g.,```
sudo rhythmbox
``` and see if it is able to connect to your device?

As far as I know, Rhythmbox has only basic support for MSC devices (drag and drop songs or albums).

---


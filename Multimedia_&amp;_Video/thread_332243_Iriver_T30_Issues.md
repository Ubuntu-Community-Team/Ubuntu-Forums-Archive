---
title: "Iriver T30 Issues"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by pbureau on 2007-01-05
I got ubuntu linux, and I have to tell you what I love it...everrythign works like a charm on my Laptop (Toshiba satellite Pro 4600).

when I plug a generic USB drive it comes on the desktop and I can use it without a problem.

When I plug MY T30 Irive MP3 player ubuntu reconizes it as a "camera" loads the image import utility, and I see all the MP3's on the drive..

how do I get the drive to be reconized as a flash drive (would be just fine with me as I prefer to manipulate file manually than use an application) or have an application that reconizes teh Iriver T30 UMT properly.

Thank you for the help.

Patrick

---

### Post by Jussi Kukkonen on 2007-01-05
You should file a bug on this -- I have no idea what package it should be filed against though.

To fix it, you could first try mounting it manually (after closing the image import wizard):
[https://help.ubuntu.com/community/MountingWindowsPartitions#head-40b4842b2a3a2f56987675b3fed4e878fcec2dd9](https://help.ubuntu.com/community/MountingWindowsPartitions#head-40b4842b2a3a2f56987675b3fed4e878fcec2dd9)
something like this:
```
mkdir ~/T30
mount /dev/XXX ~/T30 -t vfat -o iocharset=utf8,umask=0000

```
check *dmesg* to find out the device name XXX (should be in the last 10 lines just after you've inserted the usb).

If that works (~/T30/ has the files visible), check mentioned wiki page for permanent mounting instructions.

---

### Post by pbureau on 2007-01-05
dmesg indicates;

[17181913.064000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17181913.264000] usb 1-2: configuration #1 chosen from 1 choice

what does /dev/XXX <- ??? becomes..am i missing something ?

<confused>

---

### Post by Jussi Kukkonen on 2007-01-06
Is that all that gets written to dmesg when you insert the USB cord? If it is, then it's not seen as a normal USB Mass Storage, and can't be used as such -- at least not without finding some special drivers for it.

---

### Post by m83 on 2007-01-07
I think that the iRiver T30 that you have is working in [MTP]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol") mode, which means that you will be able to transfer files **only** using Windows and Windows Media Player 10.

iRiver is kind enough to provide a [UMS]("http://en.wikipedia.org/wiki/USB_mass_storage_device_class") (USB Mass Storage) firmware version on their [download page]("http://www.iriver.com/html/support/download/sudw_list.asp?searchProductIdx=73&searchCategoryIdx=&searchString=&page=1&idx=&tmpSearchProductIdx=73&tmpSearchCategoryIdx=&tmpSearchString="). So all you have to do is upgrade the firmware of your player with an UMS enabled version.

---


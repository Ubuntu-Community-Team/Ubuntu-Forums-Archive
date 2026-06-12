---
title: "Sylvania MP3 player not recognized and won't mount"
date: 2015-05-23
forum: Multimedia Software
---

### Post by thenanodude2 on 2015-05-23
I just purchased a simple MP3 player that I cannot get to mount in Ubuntu.  The MP3 player does not have a display screen, just play, fast forward, rewind, and vol up/down buttons.  Here is the info:

player:  Sylvania SMP2002 2GB

Relevant output of "lsusb":
> Bus 002 Device 018: ID 10d6:fd01 Actions Semiconductor Co., Ltd 


Output of "sudo tail -f /var/lob/syslog"
> May 23 09:27:26 atipc01 kernel: [ 5511.859296] usb 2-1.4: new high-speed USB device number 18 using ehci_hcd
May 23 09:27:26 atipc01 kernel: [ 5511.951898] usb 2-1.4: New USB device found, idVendor=10d6, idProduct=fd01
May 23 09:27:26 atipc01 kernel: [ 5511.951910] usb 2-1.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
May 23 09:27:26 atipc01 mtp-probe: checking bus 2, device 18: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
May 23 09:27:26 atipc01 mtp-probe: bus: 2, device: 18 was not an MTP device
May 23 09:28:09 atipc01 wpa_supplicant[1542]: WPA: Group rekeying completed with 98:fc:11:6c:e1:3a [GTK=TKIP]


Output of mtp-devices:
> 
libmtp version: 1.1.3

Listing raw device(s)
   No raw devices found.


"sudo fdisk -l" reports only /dev/sda (my harddrive) information and nothing relevant to this MP3 player.  Equally "ls /dev/sd*" only shows devices related to my internal harddrive

Any help would be appreciated!

---


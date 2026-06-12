---
title: "HELP installing/mounting MP3 player"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by phenolholic on 2006-08-25
Hello,
I have a Creative Zen Nano MP3 player. On lsusb this appears:

Bus 004 Device 005: ID 041e:412c Creative Technology, Ltd

and on dmesg I get this when I plug in my mp3 player:

[4294920.693000] usb 4-7: new high speed USB device using ehci_hcd and address 7
[4294920.808000] usb 4-7: configuration #1 chosen from 1 choice
[4294920.808000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294920.808000] usb-storage: device found at 7
[4294920.808000] usb-storage: waiting for device to settle before scanning
[4294925.808000]   Vendor: CREATIVE  Model: Zen Nano          Rev: 1011
[4294925.808000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294925.811000] usb-storage: device scan complete




My question is rather simple. How do I mount it (and show it on my desktop) so I can browse it and add/delete mp3s from its memory. Also I don't want to use gnomad. Thanks in advance

---

### Post by scxtt on 2006-08-25
if you just want to use it as a hard drive (and don't need to update a database) do the following:

1. plug it in
2. (1st time, only needed once) create a directory called /media/creative_zen: **sudo mkdir /media/creative_zen**
3. run this command: **sudo mount /dev/sda1 /media/creative_zen**, enter your password
note: it's only /dev/sda1 if that's your 1st usb device and you don't have SATA drives

if you want, you can add an entry to /etc/fstab, something like:
```
/dev/sda1     /media/creative_zen     usbfs     defaults     0     0
```which should handle it mounting when plugged in, tho gnome can take care of that on its own ...

---

### Post by phenolholic on 2006-08-25
I tried that. This is what I get:

mount: special device /dev/sda1 does not exist

I did a 'ls sd*' on /dev and I returned nothing.

---

### Post by scxtt on 2006-08-25
well you need to find out what /dev/ designation it's getting assigned ... try hitting tab after **/dev/sd**, see what your options are ...

---

### Post by phenolholic on 2006-08-25
nothing at all. I know what's wrong. I messed around with SATA and mass storage options on kernel configuration when I compiled my kernel. I forgot how to get back to those kernel options and modify it.

---


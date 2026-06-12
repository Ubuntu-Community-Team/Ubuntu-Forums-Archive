---
title: "Huawei e1550 problems"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by i-sultan on 2009-10-26
Hello I have installed Huawei USB Modem e1550 support on Ubuntu 8.04, but when I plug it, it works a few minutes and crashes with errors like 

```

dmesg > 
[ 2538.703456] usb 5-1: reset high speed USB device using ehci_hcd and address 2
[ 2549.114635] usb 5-1: device not accepting address 2, error -110
[ 2549.230413] usb 5-1: reset high speed USB device using ehci_hcd and address 2
[ 2559.637610] usb 5-1: device not accepting address 2, error -110
[ 2559.637905] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 2559.616929] VFS: busy inodes on changed media.
[ 2559.717720] usb 5-4: new high speed USB device using ehci_hcd and address 7
[ 2574.835983] usb 5-4: device descriptor read/64, error -110
[ 2590.057096] usb 5-4: device descriptor read/64, error -110
[ 2590.271673] usb 5-4: new high speed USB device using ehci_hcd and address 8
[ 2605.390449] usb 5-4: device descriptor read/64, error -110
[ 2620.611063] usb 5-4: device descriptor read/64, error -110
[ 2620.827615] usb 5-4: new high speed USB device using ehci_hcd and address 9
[ 2631.237825] usb 5-4: device not accepting address 9, error -110
[ 2631.350083] usb 5-4: new high speed USB device using ehci_hcd and address 10
[ 2641.761782] usb 5-4: device not accepting address 10, error -110
....
....
....

```I am trying to uplug it and plug it again but nothing happens :confused:.
Is there any issues of this problems?



Thanks in advance.

---

### Post by pdc on 2009-10-27
If you have the opportunity at all, you might try a liveCD of the new version of Ubuntu, and see if you can configure this modem on it;

here is a thread where folks have got it working on 9.04

[http://forums.hardwarezone.com.sg/showthread.php?t=2412863](http://forums.hardwarezone.com.sg/showthread.php?t=2412863)

and here someone got it work on 8.04

[http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu](http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu)

the essence seems to be that be making udev rules, you are telling ubuntu to see the modem not as  CD-ROM device but as a modem

let us know how you get along

---

### Post by i-sultan on 2009-10-27
Success is awaiting for me :) I'll report

Thanks a lot.

---

### Post by i-sultan on 2009-10-27
It's good if you are using 9.04 there is no any challenges. But there is some problems with Hardy 8.04 sometimes  when You plug it, it fails with the errors shown before :)

---


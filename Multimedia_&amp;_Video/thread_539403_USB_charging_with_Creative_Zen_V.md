---
title: "USB charging with Creative Zen V"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by whawes on 2007-08-31
My Creative Zen V will only charge via USB if I have Gnomad2 running and holding a connection open to the player. If Gnomad2 is not running, the battery stays at its existing level of charge even after several hours.

Ubuntu is recognising the device, but from the dmesg output below it appears to be dropping the connection periodically for some reason:

will@munky:~$ lsusb
Bus 005 Device 005: ID 041e:4150 Creative Technology, Ltd 
Bus 005 Device 003: ID 05ca:1830 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000

will@munky:~$ dmesg | tail
[   89.628000] usb 5-1: new high speed USB device using ehci_hcd and address 5
[   89.780000] usb 5-1: configuration #1 chosen from 1 choice
[  237.376000] usb 5-1: reset high speed USB device using ehci_hcd and address 5
[  959.852000] usb 5-1: reset high speed USB device using ehci_hcd and address 5
[  974.172000] usb 5-1: USB disconnect, address 5
[  976.712000] usb 5-1: new high speed USB device using ehci_hcd and address 6
[  976.864000] usb 5-1: configuration #1 chosen from 1 choice
[ 1018.216000] usb 5-1: USB disconnect, address 6
[ 1031.872000] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 1032.024000] usb 5-1: configuration #1 chosen from 1 choice

Is there a way to fix this?

---

### Post by TM123 on 2008-02-26
Maybe too late for the original poster but maybe useful for others? 

Does this hack help?

[http://offbe.at/blogs/sample_weblog/archive/2007/04/18/charge-creative-zen-v-plus-without-software-installed.aspx](http://offbe.at/blogs/sample_weblog/archive/2007/04/18/charge-creative-zen-v-plus-without-software-installed.aspx)

---


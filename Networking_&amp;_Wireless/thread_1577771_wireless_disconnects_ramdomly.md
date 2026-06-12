---
title: "wireless disconnects ramdomly"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by termin on 2010-09-19
i know i posted this in general help, but the reason i got no answers was because it was  the wrong spot, i apologize.


okay, yestarday and today when i do something on the internet, my wireless adapter ( Linksys compact wireless adapter G) disconnects. i went on the log viewer and i got this:
Sep 19 11:30:10 dylan-desktop kernel: [ 5119.381926] Registered led device: rt73usb-phy5::quality
Sep 19 11:30:10 dylan-desktop kernel: [ 5119.429521] udev: renamed network interface wlan0 to wlan1
Sep 19 11:30:10 dylan-desktop kernel: [ 5119.434007] rt73usb 1-2:1.0: firmware: requesting rt73.bin
Sep 19 11:30:10 dylan-desktop kernel: [ 5119.497804] usb 3-1: new full speed USB device using uhci_hcd and address 25
Sep 19 11:30:10 dylan-desktop kernel: [ 5119.565287] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Sep 19 11:30:11 dylan-desktop kernel: [ 5120.069059] usb 3-1: new low speed USB device using uhci_hcd and address 26
Sep 19 11:30:11 dylan-desktop kernel: [ 5120.644053] usb 3-1: new full speed USB device using uhci_hcd and address 27
Sep 19 11:30:12 dylan-desktop kernel: [ 5121.169072] usb 3-1: new low speed USB device using uhci_hcd and address 28
Sep 19 11:30:18 dylan-desktop kernel: [ 5127.194242] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Sep 19 11:30:45 dylan-desktop kernel: [ 5154.690841] usb 1-2: USB disconnect, address 10
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.285083] usb 1-2: new high speed USB device using ehci_hcd and address 11
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.602858] usb 1-2: configuration #1 chosen from 1 choice
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.878312] Registered led device: rt73usb-phy6::radio
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.878380] Registered led device: rt73usb-phy6::assoc
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.878419] Registered led device: rt73usb-phy6::quality
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.911663] udev: renamed network interface wlan0 to wlan1
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.915474] rt73usb 1-2:1.0: firmware: requesting rt73.bin
Sep 19 11:30:46 dylan-desktop kernel: [ 5155.996283] usb 3-1: new full speed USB device using uhci_hcd and address 29
Sep 19 11:30:47 dylan-desktop kernel: [ 5156.025639] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Sep 19 11:30:48 dylan-desktop kernel: [ 5157.309084] usb 3-1: new low speed USB device using uhci_hcd and address 31
Sep 19 11:30:48 dylan-desktop kernel: [ 5157.547279] usb 3-1: new full speed USB device using uhci_hcd and address 32
Sep 19 11:30:48 dylan-desktop kernel: [ 5157.785140] usb 3-1: new low speed USB device using uhci_hcd and address 33
Sep 19 11:30:49 dylan-desktop kernel: [ 5158.312081] usb 3-1: new full speed USB device using uhci_hcd and address 34
Sep 19 11:30:54 dylan-desktop kernel: [ 5163.724736] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Sep 19 11:32:38 dylan-desktop kernel: [ 5267.542382] usb 1-2: USB disconnect, address 11
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.144056] usb 1-2: new high speed USB device using ehci_hcd and address 12
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.465284] usb 1-2: configuration #1 chosen from 1 choice
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.734755] Registered led device: rt73usb-phy7::radio
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.736167] Registered led device: rt73usb-phy7::assoc
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.736935] Registered led device: rt73usb-phy7::quality
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.780172] udev: renamed network interface wlan0 to wlan1
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.783866] rt73usb 1-2:1.0: firmware: requesting rt73.bin
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.853133] usb 3-1: new low speed USB device using uhci_hcd and address 35
Sep 19 11:32:39 dylan-desktop kernel: [ 5268.906356] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Sep 19 11:32:40 dylan-desktop kernel: [ 5269.421036] usb 3-1: new full speed USB device using uhci_hcd and address 36
Sep 19 11:32:40 dylan-desktop kernel: [ 5269.989063] usb 3-1: new full speed USB device using uhci_hcd and address 37
Sep 19 11:32:41 dylan-desktop kernel: [ 5270.509045] usb 3-1: new low speed USB device using uhci_hcd and address 38
Sep 19 11:33:00 dylan-desktop kernel: [ 5289.303816] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Sep 19 11:36:08 dylan-desktop kernel: [ 5477.334020] usb 1-2: USB disconnect, address 12
Sep 19 11:36:12 dylan-desktop kernel: [ 5481.604028] usb 1-2: new high speed USB device using ehci_hcd and address 13
Sep 19 11:36:12 dylan-desktop kernel: [ 5481.922234] usb 1-2: configuration #1 chosen from 1 choice
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.189942] Registered led device: rt73usb-phy8::radio
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.190403] Registered led device: rt73usb-phy8::assoc
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.190881] Registered led device: rt73usb-phy8::quality
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.220035] udev: renamed network interface wlan0 to wlan1
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.226482] rt73usb 1-2:1.0: firmware: requesting rt73.bin
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.300042] usb 3-1: new full speed USB device using uhci_hcd and address 39
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.332990] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.532051] usb 3-1: new full speed USB device using uhci_hcd and address 40
Sep 19 11:36:13 dylan-desktop kernel: [ 5482.989034] usb 3-1: new full speed USB device using uhci_hcd and address 41
Sep 19 11:36:14 dylan-desktop kernel: [ 5483.512043] usb 3-1: new full speed USB device using uhci_hcd and address 42
Sep 19 11:36:20 dylan-desktop kernel: [ 5489.888540] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready




thanks!

---

### Post by termin on 2010-09-19
also my usb device is better known as:

Linksys WUSB54GC 802.11g Adapter

---

### Post by termin on 2010-09-19
a closer look when i go on dmesg is:
[22108.696018] usb 3-1: new low speed USB device using uhci_hcd and address 124
[22108.928022] usb 3-1: new full speed USB device using uhci_hcd and address 125
[22109.160069] usb 3-1: new low speed USB device using uhci_hcd and address 126
[22109.568028] usb 3-1: device not accepting address 126, error -71
[22109.680033] usb 3-1: new full speed USB device using uhci_hcd and address 127
[22110.088019] usb 3-1: device not accepting address 127, error -71
[22110.088042] hub 3-0:1.0: unable to enumerate USB device on port 1

---


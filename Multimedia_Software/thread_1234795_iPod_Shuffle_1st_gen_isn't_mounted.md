---
title: "iPod Shuffle 1st gen isn't mounted"
date: 2009-08-08
forum: Multimedia Software
---

### Post by orkerone on 2009-08-08
Hi all, 

I'm trying to mount an iPod Shuffle 1st Gen on my computer running Ubuntu Jaunty, but can't get anything working.

```
**lsusb**
Bus 001 Device 005: ID 05ac:1300 Apple, Inc. iPod Shuffle
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
**dmesg | tail**
[ 9941.316506] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 9946.448153] usb 1-1: unable to read config index 0 descriptor/start: -110
[ 9946.448160] usb 1-1: chopping to 0 config(s)
[ 9956.448082] usb 1-1: string descriptor 0 read error: -110
[ 9966.448141] usb 1-1: string descriptor 0 read error: -110
[ 9976.448067] usb 1-1: string descriptor 0 read error: -110
[ 9976.452524] usb 1-1: no configuration chosen from 0 choices

```

Please help :) !

---


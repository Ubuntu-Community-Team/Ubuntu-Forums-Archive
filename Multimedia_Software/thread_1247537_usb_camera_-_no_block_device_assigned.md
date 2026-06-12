---
title: "usb camera - no block device assigned?"
date: 2009-08-23
forum: Multimedia Software
---

### Post by subgiraffe on 2009-08-23
I have two different Canon cameras, both giving the same problem on my dell mini-10 running 8.04

When I plug in the camera and check dmesg:

[ 1782.686614] usb 4-4: new high speed USB device using ehci_hcd and address 20
[ 1782.725626] usb 4-4: configuration #1 chosen from 1 choice

and lsusb gives:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 021: ID 04a9:3110 Canon, Inc. 
Bus 004 Device 009: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0c45:63e3 Microdia 

Problem I have is that no device is being assigned so I can't mount the camera anywhere.  gphoto etc.. don't seem to work either.

Any help will be much appreciated.

---

### Post by subgiraffe on 2009-08-25
ok .. so it seems canpn are using ptp or mtp protocols rather than mass storage.

managing to access my camera using gphotofs - it is slow and clunky, will probably go and buy a cf card reader for now, until this has better support in linux..

---


---
title: "Need help getting TP-link wn422g working (USB dongle)"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by svguy on 2009-06-06
I've got an Asus EEE that i've got easy peasy running on (8.04).  
Kernel version 2.6.24-21-eeepc.  I went through some walk throughs when I got it to get the Atheros card working with monitor mode and injection, and that's worked flawlessly. The wireless is fine on this thing, but it's about as strong as you can get from a mini-pci card.  For fun I bought the TP-link wn422g USB wifi stick since it has an external antenna. I then bought an indoor directional antenna to hook up to it.  Mostly I wanted to use it for playing with my home WDS network, but I'd also like to see if it might be a decent wireless solution at my buddy's place where he's very far away from his AP.

Anyway, when I plug the adapter in it gets power, but the firmware doesn't and of course, no driver.  From what i've gathered this chipset needs the zd1211rw driver, however the download for it via aptitude doesn't include the firmware (says it's unavailable).  And any individual downloads i've found through various other sites seem to have dead links.

I put 9.04 on a thumb drive and booted to that and it recognizes the usb dongle fine and even associates with APs, it just drops the connection quite often.

I don't have the zd1211rw module, and i'm kind of stuck here. Wondering if anyone has any hints for me.

Here's the tail of dmesg after plugging in the USB dongle:
```

[12391.492797] usb 5-4: new high speed USB device using ehci_hcd and address 6
[12391.625894] usb 5-4: configuration #1 chosen from 1 choice

```

And here's the output from lsusb
```

wascally@wabbit:/etc$ lsusb
Bus 005 Device 006: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 005 Device 002: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

It's the top entry.

---


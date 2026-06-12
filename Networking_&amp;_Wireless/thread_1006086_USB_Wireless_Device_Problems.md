---
title: "USB Wireless Device Problems"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by xerox1101 on 2008-12-08
Hi, I have a zd1211rw based USB wireless device. It used to work fine in Ubuntu without any special configuration when I used it in 7.04.  At some point, however, it stopped working. I haven't used it in awhile so I can't say for sure when the problem started, but I can say that I'm now running 8.10 and the last time I really used it was in 7.10. 

Anyways, I think that the problem is USB related and I was hoping someone could help me out. When I boot the system, the wireless device is not detected at all and doesn't even appear in the lsusb output. My dmesg output sheds some light on the situation...

```
[  109.064021] usb 5-6: new high speed USB device using ehci_hcd and address 70
[  109.120337] hub 5-0:1.0: unable to enumerate USB device on port 6
[  109.308238] hub 5-0:1.0: unable to enumerate USB device on port 6
[  109.496252] hub 5-0:1.0: unable to enumerate USB device on port 6
[  109.684260] hub 5-0:1.0: unable to enumerate USB device on port 6
[  109.872277] hub 5-0:1.0: unable to enumerate USB device on port 6
[  110.060296] hub 5-0:1.0: unable to enumerate USB device on port 6
[  110.304028] usb 5-6: new high speed USB device using ehci_hcd and address 76
[  110.360283] hub 5-0:1.0: unable to enumerate USB device on port 6
[  110.604031] usb 5-6: new high speed USB device using ehci_hcd and address 77
[  110.660297] hub 5-0:1.0: unable to enumerate USB device on port 6
[  110.904019] usb 5-6: new high speed USB device using ehci_hcd and address 78
```

This same pattern repeats infinitely with the address cycling from 1-255  Looking back at the system startup log I found the output from when the ehci_hcd module was loaded, but nothing there seemed glaringly wrong.
```

[    2.984878] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.984905] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.984913] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.984977] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.988954] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.988971] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd8100000
[    3.041065] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.041369] usb usb5: configuration #1 chosen from 1 choice
[    3.041434] hub 5-0:1.0: USB hub found
[    3.041450] hub 5-0:1.0: 8 ports detected
```

After googling and searching the forums, the only advice that I've found recommends using the command below to disable the ehci_hcd module altogether.
```
sudo rmmod ehci_hcd
```
After running this, the wireless is instantly found and loaded which is great.  Of course removing the ehci_hcd module disables USB 2.0 support so I don't consider this a practical solution.
 
Does anyone have any other ideas about what I could do to fix this or at least figure out what's going on? Is there are a way to make the ehci_hcd module output extra debug messages to the log so I could find more information about why it's not connecting? Any advice would be greatly appreciated.

Thanks.

---

### Post by jhoderd on 2008-12-09
(I already replied to this same problem in another thread; the answer is still the same)

I have the same exact problem.  There are several reports about this in Launchpad, some of them dating back several months.  The Ubuntu kernel devs recommend that you disable ehci_hcd (modprobe -r ehci_hcd) until a fix is found  (I think that the Jaunty kernel suffers from the same problem, so you might have to wait for release 9.10).  The downside, of course, is that you loose high-speed USB...

---


---
title: "HTC phone USB tethering on 10.10 Maverick"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by taiang on 2011-02-16
I just got an HTC Desire phone and wanted to use the built-in USB tethering on my laptop running 10.10 Maverick. Thethering with this phone works 100% on my home desktop box, also running 10.10. However, when attempting to tether the laptop, the wired connection succeeds and is instantly lost. This is the output of tail /var/log/messages right after the USB tethering option is activated on the phone's network settings menu (after connecting laptop via USB):


> kernel: [86566.972428] usb 2-5: USB disconnect, address 38
kernel: [86567.440051] usb 2-5: new high speed USB device using ehci_hcd and address 39
kernel: [86567.624251] rndis_host 2-5:1.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-5, RNDIS device, a3:a4:66:e6:db:ce
kernel: [86572.411205] usb 2-5: USB disconnect, address 39
kernel: [86572.411339] rndis_host 2-5:1.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-5, RNDIS device
kernel: [86572.910048] usb 2-5: new high speed USB device using ehci_hcd and address 40
kernel: [86573.074723] scsi30 : usb-storage 2-5:1.0
kernel: [86574.073179] scsi 30:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
kernel: [86574.074270] sd 30:0:0:0: Attached scsi generic sg3 type 0
kernel: [86574.083781] sd 30:0:0:0: [sdc] Attached SCSI removable disk

anyone have this same issue? Suggestions will be loved x-)

---

### Post by AlexQM on 2011-02-16
Hi there,

I would be inclined to look at the network manager on both machines when you have the Desire attached and make notes on the connection settings etc.


It might also be worth checking the settings that are in the Development section of the phone:
Settings > Application Settings > Development

Toggle with the USB Debugging and Allow Mock Location tick boxes, this has been known to have an influence.

There are also plenty of tethering application available on the Android Market so have a look through those too.

Regards,

Alex

---

### Post by AlexQM on 2011-02-24
Any luck on this?

---

### Post by jjb945025 on 2011-02-24
Your problem sounds sort of similar to mine. But I've been unable to locate network manager and am using lucid lynx on a desktop.think you can help me get things rolling? ;read my thread on networking if/when you've got the time..thanks

---

### Post by taiang on 2011-02-24
Today, I tried turning on USB Debug mode as Alex suggested. When I plugged it in, it worked right away! I'm not sure if it was the effect of changing the debug setting though; it still works after turning it off again... Anyway, might be worth a shot if you're also getting this kind of trouble. Also, updating your system might be a good idea, too; my apt logs indicate that a bunch of package updates were installed today, that may have played a part. Many thanks for your help!

---


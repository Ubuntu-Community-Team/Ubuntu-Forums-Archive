---
title: "Android USB Tether and Ubuntu Server"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by Mriswithe on 2011-01-02
I am currently trying to get my server box to recognize my Samsung epic 4g (sprint) which is rooted and has usb tether enabled. It works perfectly and effortlessly on my ubuntu desktop box, but I hook it up to my server box and ifconfig does not find a usb0 device like my desktop does. Any ideas/input on what I could try? I am running 10.4.1 on both desk and server box.

---

### Post by irvotheturbo on 2011-01-09
> **Mriswithe said:**
> I am currently trying to get my server box to recognize my Samsung epic 4g (sprint) which is rooted and has usb tether enabled. It works perfectly and effortlessly on my ubuntu desktop box, but I hook it up to my server box and ifconfig does not find a usb0 device like my desktop does. Any ideas/input on what I could try? I am running 10.4.1 on both desk and server box.

Same here using a Samsung Galaxy S. Looks like my 32-bit Ubuntu system does seem to attempt to recognise the phones USB Tethered network connection, but on my laptop and other desktop (both 64bit) nothing happens. The only thing that happens after pressing USB Tethering is the following:
```
[10061.647787] usb 1-4: USB disconnect, address 5
[10061.991406] usb 1-4: new high speed USB device using ehci_hcd and address 6

```
I think hotplug or something else isn't starting up to recognise what it is. Maybe a udev rule is missing? :confused:

---


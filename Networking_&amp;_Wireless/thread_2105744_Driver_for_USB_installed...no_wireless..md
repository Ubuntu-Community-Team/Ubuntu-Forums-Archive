---
title: "Driver for USB installed...no wireless."
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by Enigmapond on 2013-01-16
Greets!

I have a small propblem getting a Linksys AE1200 Wireless-N USB Adapter to work on a DEll Optiplex GX620. I have installed the driver by way of ndiswrapper which went very well and my ndiswrapper -i states..

```
$ndiswrapper -l
bcmwlhigh5 : driver installed
	device (13B1:0039) present

```

however I'm unable to get this to start at boot. I tried 
```
sudo modprobe -r ndiswrapper | sudo modprobe ndiswrapper
```

but it gives 
```
FATAL: Module ndiswrapper not found
```

How can I add this to /ect/modules so that it starts...?? Or is there something I've missed?

Thank you in advance!

---


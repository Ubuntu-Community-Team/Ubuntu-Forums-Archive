---
title: "Driver installed .. Still no Wifi ?"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Kev-Mc on 2011-05-27
Hi i have installed my wireless driver using ndiswrapper and the installation disc that came with the driver.On the windows wireless drivers it shows bcmwl5 hardware present : yes. unfortunately however on the taskbar it still shows my firmware to be missing ? 

the network controller is shown as Broadcom Corporation BCM4306 802.11b/g WLAN controller and the subsystem is Belkin F5D7000 v1000 Wireless G desktop card. Could it be that my wireless card just isn't supported or is there anything i could do to make it work? 

Thanks.

---

### Post by chili555 on 2011-05-27
> Could it be that my wireless card just isn't supportedNo, it could not be that it's unsupported.> is there anything i could do to make it work?Sure. Let's troubleshoot your installation. Please open Applications > Accessories > Terminal and run and post:```
ndiswrapper -[COLOR="Red"]l[/COLOR]
dmesg | grep -e ndis -e b43
lsmod
```That's a lower-case L for 'list.' The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---


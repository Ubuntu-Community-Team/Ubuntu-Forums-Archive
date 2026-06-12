---
title: "Only unsecured WLAN access with HP 550 and broadcom wlan chipset"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by smarti_J on 2009-03-23
Hallo,

just got a new HP 550 laptop where I would like to install ubuntu 8.10. Before installing I tried to test if everything works fine with a live CD. It's everything except the wlan access. The driver won't let me connect secured (WPA / WPA2 PSK). All wlan accesspoints in the neighbourhood including my own are recognized, but when I klick on one and after entering my key it tries to connect a while and then returns requesting the key again. It seems that the key can't be exchanged with the router.

```
lspci
BMC4312 802.11 b/g (rev 01)
```

So I ran through all available forums for a solution and tried all the hints I read.

First I activated the broadcam sta wireless driver. Nothing. Transfered the live cd to a usb-stick so that after a reboot my settings would remain. Same result after reboot.

So I deactivated the driver and looked if the B43 or BMC43XXX driver where loaded into the kernel. Nope, they where blacklisted. Then I installed them one after the other. Same result.

NDISWRAPPER should do with the original windows driver (.inf). Looked fine but didn't work although I tried the windows drivers from DELL, Broadcom and HP.

Last try was exchanging network manager by wicd. All the wlan ap's recognized but connection only unsecured.

The HP 550 is a very nice machine with a very nice price (399,- €) but without wlan access it's nothing for me.

Perhaps I didn't realize everything for a solution, so if someone had a similar problem and solved it please give me a hint (or two).

B.t.w.: With another HP laptop wlan access was no problem (same live CD), it worked out-of-the box.

I can't answer questions about hardware or settings before next weekend, but help is appreciated very much.

Regards
smarti_J

---

### Post by lazyart on 2009-06-23
Old thread, but all seems to work well with my hp 550, broadcom wireless and Jaunty.

---


---
title: "Wireless USB suspend/resume problem RTL8192SU adapter"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by walt.smith1960 on 2011-05-01
Well, the kernel giveth and the kernel taketh away, or something like that.:rolleyes:  I've installed 11.04 and hadn't had any major glitches until I suspended/resumed a machine with an RTL8192SU plugged in.  The adapter would not resume.  If I unplugged and plugged in again it works perfectly
```

Relevant parts of dmesg after a suspend/resume cycle

[44820.162843] PM: resume of drv:sd dev:2:0:0:0 complete after 5573.547 msecs
[44820.162884] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 2546.730 msecs
[44820.162891] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 5573.567 msecs
[44820.162942] PM: resume of devices complete after 5578.383 msecs
[44820.167933] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x03F0 pid 0x1604
[44820.168092] PM: resume devices took 5.584 seconds
[44820.168121] PM: Finishing wakeup.
[44820.168122] Restarting tasks ... done.
[44820.252043] r8169 0000:02:00.0: eth0: link down
[44820.252408] ADDRCONF(NETDEV_UP): eth0: link is not ready
[44820.361033] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[44820.432232] r8712u: in r8711_wx_set_scan: bDriverStopped=1
[44820.749316] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[44821.002176] r8712u: in r8711_wx_set_scan: bDriverStopped=1
[44841.003106] r8712u: in r8711_wx_set_scan: bDriverStopped=1

After unplugging then replugging the adapter

[45049.543789] usb 1-1: USB disconnect, address 7
[45051.812142] usb 1-1: new high speed USB device using ehci_hcd and address 8
[45051.947763] r8712u: DriverVersion: v7_0.20100831
[45051.947803] r8712u: register rtl8712_netdev_ops to netdev_ops
[45051.947811] r8712u: USB_SPEED_HIGH with 4 endpoints
[45051.949085] r8712u: Boot from EFUSE: Autoload OK
[45052.686170] r8712u: CustomerID = 0x0000
[45052.686180] r8712u: MAC Address from efuse = 00:14:d1:e7:17:ba
[45052.721366] <30>udev[15931]: renamed network interface wlan0 to wlan1
[45053.444618] r8712u: 1 RCR=0x153f00e
[45053.445365] r8712u: 2 RCR=0x553f00e
[45053.553108] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[45060.845353] r8712u: [r8712_got_addbareq_event_callback] mac = 00:26:62:7c:b1:5b, seq = 0, tid = 7
[45060.845684] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[45063.737587] r8712u: [r8712_got_addbareq_event_callback] mac = 00:26:62:7c:b1:5b, seq = 0, tid = 0
[45071.744072] wlan1: no IPv6 routers present
[45075.632704] r8712u: [r8712_got_addbareq_event_callback] mac = 00:26:62:7c:b1:5b, seq = 512, tid = 0


```Googling shows this bug:  [https://lists.linux-foundation.org/pipermail/bugme-new/2011-January/026559.html](https://lists.linux-foundation.org/pipermail/bugme-new/2011-January/026559.html)  so I don't feel so lonely.

This device works perfectly in Maverick which uses the 2.6.35 kernel when the firmware patch is applied.  I assume that firmware patch won't work where kernel level support is present.  Any thoughts about how to work around this problem until this bug is squashed?

Edit:  When I run lsmod I see what appear to be two realtek modules loaded, r8169 and r8712u. I was thinking dueling modules so I blacklisted r8169. Restart and r8169 still showed up in lsmod and the device worked after restart.  I then went back and blacklisted r8712u and restarted.  The device didn't come alive and r8712u was not listed by lsmod.  Obviously the devices uses r8712u.  I wonder why r8169 loads after being blacklisted when r8712u does not?

---

### Post by chili555 on 2011-05-01
> Edit: When I run lsmod I see what appear to be two realtek modules loaded, r8169 and r8712u. I was thinking dueling modules so I blacklisted r8169. Restart and r8169 still showed up in lsmod and the device worked after restart. I then went back and blacklisted r8712u and restarted. The device didn't come alive and r8712u was not listed by lsmod. Obviously the devices uses r8712u. I wonder why r8169 loads after being blacklisted when r8712u does not?I don't know the answer to the suspend problem; however r8169 is the driver for your ethernet card and has nothing to do with wireless. It is not dueling with r8712u.

You might try this, substituting r8712u, of course. Report back so we all learn from your experience.

[http://ubuntuforums.org/showpost.php?p=10226021&postcount=2](http://ubuntuforums.org/showpost.php?p=10226021&postcount=2)

---

### Post by ppareit on 2011-05-06
I can confirm that the solution by chili555 works. This is what I now have in the pm config file:

```
# cat /etc/pm/config.d/config
SUSPEND_MODULES=r8712u
```

---

### Post by walt.smith1960 on 2011-05-06
Ding Ding Ding!  Another win for Chili555!!! Suspend and resume work as expected after adding the file. Thread marked as solved.

---

### Post by pablokornfeld on 2011-08-01
Thank you so much! It helped me to solve the same problem as well.

---

### Post by bosyber on 2011-11-18
> **chili555 said:**
> I don't know the answer to the suspend problem; however r8169 is the driver for your ethernet card and has nothing to do with wireless. It is not dueling with r8712u.

You might try this, substituting r8712u, of course. Report back so we all learn from your experience.

[http://ubuntuforums.org/showpost.php?p=10226021&postcount=2](http://ubuntuforums.org/showpost.php?p=10226021&postcount=2) Thanks very much chili555, that solved the suspend/resume issue with the new usb wifi for my wife's netbook.

---

### Post by carra on 2012-06-01
> **bosyber said:**
> Thanks very much chili555, that solved the suspend/resume issue with the new usb wifi for my wife's netbook.

It did the trick for me too, with 
1. Asus usb wifi dongle 
2. HP TX 1000 Pavilion laptop
3. Chakra Linux ;-)
Thanks a lot!

carra from Italy

---

### Post by Lindsay.Mathieson on 2012-07-09
> **chili555 said:**
> I don't know the answer to the suspend problem; however r8169 is the driver for your ethernet card and has nothing to do with wireless. It is not dueling with r8712u.

You might try this, substituting r8712u, of course. Report back so we all learn from your experience.

[http://ubuntuforums.org/showpost.php?p=10226021&postcount=2](http://ubuntuforums.org/showpost.php?p=10226021&postcount=2)

Thank you so much Chilli, that worked for me as well

- Kubuntu 12.04
- Billion Adapter (same chipset as OP)

---


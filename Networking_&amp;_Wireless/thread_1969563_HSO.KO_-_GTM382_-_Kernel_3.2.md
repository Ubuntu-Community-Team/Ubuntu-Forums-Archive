---
title: "HSO.KO - GTM382 - Kernel 3.2"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by litch84 on 2012-04-30
I've scoured the net for an answer - but to avail.

I've got a GTM382E (Mini PCIe Option Globtrotter MO40x 3G Modem; 0af0:7601)

Now I had this working back in my custom Kernel 3.0.20 for Oneiric - but now that I've upgraded to Precise (Stock kernel 3.2.0-24-generic) - none of the 6-or-so /dev/ttyHSx devices appear - instead, only 1 - and you can't even get a response from minicom using AT commands.

```

[31075.948539] hso: /build/buildd/linux-3.2.0/drivers/net/usb/hso.c: Option Wireless
[31075.949264] usbcore: registered new interface driver hso

...and

root@gwol:~/udev# ll /dev/ttyHS*
crw-rw---- 1 root dialout 249, 0 Apr 30 22:11 /dev/ttyHS0

```Does anyone have an idea on how to get this HSO module working properly again?

---

### Post by litch84 on 2012-04-30
Anyone?

---

### Post by alexfish on 2012-05-01
find out the id's of the device from the lsusb command
```
lsusb
```the find the driver path
```
ls /sys/bus/*/drivers/*/new_id
```put the device id's into the path of the <driver>/new_d
```
echo [COLOR=Blue]****[/COLOR] [COLOR=Green]****[/COLOR] > /sys/bus/<*cls>/drivers/<*driver>/new_id
```[COLOR=Blue]**** = vendor id
[/COLOR][COLOR=Green]**** = product id[/COLOR]

see what happens

alexfish

---

### Post by litch84 on 2012-05-01
> **alexfish said:**
> see what happens

Nothing except the 1 x /dev/ttyHS0 that did exist, disappears.

No extra info in dmesg either.

---

### Post by alexfish on 2012-05-01
weird,

can re-plug device , ensure the first /dev/HS* shows and post the results of
```

usb-devices
```

---

### Post by litch84 on 2012-05-01
> **alexfish said:**
> weird,

can re-plug device , ensure the first /dev/HS* shows and post the results of
```

usb-devices
```

Ok, wtf, now they're all there.

I've just fully unplugged the server 5 times today from power, rebooted like 10 times (separate issue) - and it didn't once work.

I unplug the modem and re-plug it while on and it starts working.

/sigh

Thanks Alex...

---

### Post by alexfish on 2012-05-01
can also try using touch to see what happens
```

sudo /bin/touch /dev/<yourdevice>_mobile
```

---


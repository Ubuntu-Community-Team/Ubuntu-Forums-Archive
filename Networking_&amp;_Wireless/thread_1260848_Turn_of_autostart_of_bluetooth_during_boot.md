---
title: "Turn of autostart of bluetooth during boot"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Lomz on 2009-09-08
I recently got one Acer Aspire One with 11,x" 8 hours of battery and so on.
It also has bluetooth but I dont normally use it so I find it a bit anoying to turn it off every time I start the computer.

It seems to turn it self on during boot or the following process (before GUI) so just removing the autostart of the bluetooth-manager doesnt cut it.

Anyone that knows how to make the device not turn on?

If it matters, I would be suprised, I use Xubuntu 9.04.

---

### Post by Lomz on 2010-01-03
bump

---

### Post by SimeonF on 2010-10-10
This is probably a matter of stopping the bluetooth service. On my laptop

```

$ sudo /etc/init.d/bluetooth stop
```

Changes the status icon to bluetooth off. You can adjust whether services autostart by installing the rcconf program and de-selecting bluetooth...

---


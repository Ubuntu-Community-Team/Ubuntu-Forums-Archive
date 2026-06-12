---
title: "can't blacklist e100"
date: 2006-04-13
forum: Networking &amp; Wireless
---

### Post by fhennies on 2006-04-13
Hej there,

I am running Breezy on my Notebook compaq evo n410. My NIC doesn't work correctly with the e100 driver (produces crc errors). Replacing with the eepro100 driver manually via rmmod / modprobe works nice.

But when I try to do it permanently by blacklist, my systems always starts up with both e100 and eepro100.

My blacklist looks like

```
# replaced by e100
e100
# eepro100

```

After reboot, lsmod gives this:

```
sudo lsmod | grep 100
eepro100               30192  0
e100                   34976  0
mii                     5696  2 eepro100,e100

```

Any ideas?

---

### Post by koshari on 2008-05-16
the line should read

```
blacklist e100
``` instead of simply e100

---

### Post by amingv on 2008-05-16
My goodness! :)
I'm sure she either solved it or left Ubuntu by now.

---


---
title: "Bluetooth name"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by Jay Nnib on 2012-12-26
Hey, I wonder whether we can change the name of the bluetooth device because I don't want my laptop to identified as "ubuntu-0". And I prefer GUI to CUI. So please don't say, "It's simple. Go to the terminal..."(no offence code lovers).

---

### Post by slickymaster on 2012-12-26
I'm not 100% sure, but I think you can't change bluetooth device name from Bluetooth control panel.

Anyway, if you want to change the bluetooth device name permanently, you have to create a file called **/etc/machine-info** which should have the following content:

```
PRETTY_HOSTNAME=Device Name
```

---

### Post by Jay Nnib on 2013-01-06
What do mean by "permanently change"? And please be clear.

---

### Post by slickymaster on 2013-01-07
Permanently means that every time you boot your machine it will read that file and will assign the name you've defined to your bluetooth device.

---


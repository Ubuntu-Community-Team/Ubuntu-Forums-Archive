---
title: "Intel WiFiLink 5100 driver settings won't survive reboot"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by greenie9 on 2009-06-12
> **Evil Dax said:**
> Jaunty64, Intel WiFiLink 5100 and WPA2

lspci:
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

OS:
Jaunty64: 2.6.28-11-generic

Issue:
non-secured and WEP working, while WPA and WPA2 fail to connect

Solution:
download latest microcode from Intel:
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz")
put the file into /lib/firmware

change modprobe:
```

sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

```

And you can connect to WPA2

sorry if i'm being painful, but this settings doesnt seem to stick for me
each time i start up, i have to re-run this

---

### Post by dmizer on 2009-06-12
I've separated your post into a new thread.

Edit /etc/rc.local, and add those two lines, so it looks something like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Red"]modprobe -r iwlagn
modprobe iwlagn 11n_disable=1 11n_disable50=1[/COLOR]
exit 0
```

---

### Post by greenie9 on 2009-06-15
thank you so much!!!!
fixed it straight away

---


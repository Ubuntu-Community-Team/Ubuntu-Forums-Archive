---
title: "Ubuntu does not recognise TV Tuner on ASUS F8SA notebook"
date: 2010-07-11
forum: Multimedia Software
---

### Post by mstrelan on 2010-07-11
Ever since switching to Ubuntu (Hardy at the time) I have had no luck getting my TV Tuner to work. I think the closest I have come is finding [this information]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/995988.html") but it didn't really help and I'm not sure if it's relevant. Can anyone help? I have attached the relevant output of lsusb -v

***EDIT***
Further to this I have read [these instructions]("http://www.stud.fit.vutbr.cz/~xzemek02/articles/Asus-M50SV-AS160C-Debian-Lenny/#tv-tuner") and I get the following result.

```
michael@michael-laptop:~/v4l-dvb$ sudo modprobe dvb-usb-dib0700
WARNING: Error inserting dib0070 (/lib/modules/2.6.32-19-generic/kernel/drivers/media/dvb/frontends/dib0070.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting dib7000m (/lib/modules/2.6.32-19-generic/kernel/drivers/media/dvb/frontends/dib7000m.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting dib0090 (/lib/modules/2.6.32-19-generic/kernel/drivers/media/dvb/frontends/dib0090.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting dib7000p (/lib/modules/2.6.32-19-generic/kernel/drivers/media/dvb/frontends/dib7000p.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting dvb_usb_dib0700 (/lib/modules/2.6.32-19-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dib0700.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg output is attached

---

### Post by mstrelan on 2011-04-08
Still nothing :(

---


---
title: "Installation troubles VT6656"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by PaulStat on 2009-12-12
Hi Folks,

Ok I think this is probably a good place to ask, I'm having no end of problems installing this wireless card. I found a useful link that showed my how to compile the source and install the module into the linux kernel.

If I now do a 

```

modprobe -l

```

I can see that it has installed

```

kernel/lib/crc-itu-t.ko
kernel/lib/crc7.ko
kernel/lib/libcrc32c.ko
kernel/lib/zlib_deflate/zlib_deflate.ko
kernel/lib/reed_solomon/reed_solomon.ko
kernel/lib/lzo/lzo_compress.ko
kernel/lib/lzo/lzo_decompress.ko
kernel/lib/ts_kmp.ko
kernel/lib/ts_bm.ko
kernel/lib/ts_fsm.ko
kernel/drivers/video/nvidia.ko
**kernel/drivers/net/vntwusb.ko**
```

However, if I try to do a 

```

iwconfig

```

It only lists the following

```

lo        no wireless extensions.

eth0      no wireless extensions.
```

lo I believe is the loopback interface, and eth0 is the wired connection. I was expecting to see a wlan0 or something similar? Any ideas as to why this is?

Any help appreciated

Paul

---

### Post by PaulStat on 2009-12-13
*bump* anyone?

---

### Post by PaulStat on 2009-12-13
still no-one

---

### Post by NichoTL on 2010-04-24
First workaround:
you can restart the network-manager job:

sudo restart network-manager

If the module is installed (sudo make clean, sudo make install, modprobe vntwusb), it should work.

A full reboot should also work (normally).

I have now started to identify some of the issues not with the driver itself (it works), but its quirks which create some issues.

I encourage to follow this thread if you are interested (I know it's been 4 months now since you last posted):

[VT6656 USB Wireless]("http://ubuntuforums.org/showthread.php?t=841849&page=3&highlight=vt6656")

---


---
title: "usb-uirt setup in lirc"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by gormine on 2007-11-11
I'm getting this error when I run lirc in a terminal and irw in another.

```
sudo lircd -n --driver usb_uirt_raw -d /dev/ttyUSB0
```

lircd-0.8.2[5695]: lircd(userspace) ready
lircd-0.8.2[5695]: accepted new client on /dev/lircd
lircd-0.8.2[5695]: uirt2_raw: checksum error
lircd-0.8.2[5695]: uirt2_raw: UIRT version 0905 ok
lircd-0.8.2[5695]: uirt2_raw: could not set DTR
lircd-0.8.2[5695]: caught signal
Terminated


I found a post on another board where the guy had the same exact error. This is what he said he did to fix it. 

> I replaced linux/drivers/usb/serial/ftdi_sio.c and ftdi_sio.h with
versions from a couple kernels back. Works fine now.

Here is a link to the whole thread

[http://www.gossamer-threads.com/lists/mythtv/users/293503?do=post_view_flat]("http://www.gossamer-threads.com/lists/mythtv/users/293503?do=post_view_flat")

My question is if anyone knows how to fix this another way or if someone could explain to me how to do what this guy says. Do I have to roll back the whole kernel?

---


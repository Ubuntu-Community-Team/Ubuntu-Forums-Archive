---
title: "not video working in Webcam Creative vf0350 in karmic already patched"
date: 2010-02-21
forum: Multimedia Software
---

### Post by Wiley_Linux on 2010-02-21
Hi guys,

I have ubuntu karmic already patched to support webcam Creative vf0350. Everything looks fine for me, but when I open skype, i only can see green and black lines in the video. The same if I open camstream.

I think that perhaps I have to configure some file, but I have no clue which one. Here I copy the dmesg logs.

```
[ 5551.000041] usb 3-3: new full speed USB device using ohci_hcd and address 13
[ 5551.220508] usb 3-3: configuration #1 chosen from 1 choice
[ 5551.223055] gspca: probing 041e:4067
[ 5551.454361] ov519: I2C synced in 0 attempt(s)
[ 5551.454367] ov519: starting OV7xx0 configuration
[ 5551.478361] ov519: Sensor is an OV7670
[ 5554.710466] gspca: /dev/video0 created
```

Any help is appreciate,

Thanks,
Wiley

---

### Post by Wiley_Linux on 2010-02-21
Finally, it works after googling and try different things. I found this link [http://linuxmoc.wordpress.com/2009/01/04/creative-labs-live-im-webcam-vf0350-in-linux/]("http://linuxmoc.wordpress.com/2009/01/04/creative-labs-live-im-webcam-vf0350-in-linux/"). I only had to change the folder. In my case was to run skype:

sudo env LD_PRELOAD=/usr/**lib32**/libv4l/v4l1compat.so skype

to run camstream the same but changing lib32 to lib

sudo env LD_PRELOAD=/usr/**lib**/libv4l/v4l1compat.so skype

Hope this help other people.

---


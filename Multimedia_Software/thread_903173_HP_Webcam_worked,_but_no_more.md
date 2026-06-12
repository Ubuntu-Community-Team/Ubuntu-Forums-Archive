---
title: "HP Webcam worked, but no more"
date: 2008-08-28
forum: Multimedia Software
---

### Post by uhappo on 2008-08-28
My laptop is HP Pavilion dv5-1035eo. When I tried my webcam in Cheese for the first time, it worked as it should and all was clear.

But when I tried it next day, it wasn't working. Also Camorama wasn't working with it.

lsusb says it's
```

5986:0137 Bison

```

And dmesg says about it
```

[   34.104817] uvcvideo: disagrees about version of symbol video_devdata
[   34.104822] uvcvideo: Unknown symbol video_devdata
[   34.105123] uvcvideo: disagrees about version of symbol video_unregister_device
[   34.105125] uvcvideo: Unknown symbol video_unregister_device
[   34.105215] uvcvideo: disagrees about version of symbol video_device_alloc
[   34.105217] uvcvideo: Unknown symbol video_device_alloc
[   34.105287] uvcvideo: disagrees about version of symbol video_register_device
[   34.105289] uvcvideo: Unknown symbol video_register_device
[   34.105479] uvcvideo: disagrees about version of symbol video_device_release
[   34.105481] uvcvideo: Unknown symbol video_device_release

```

What's wrong?

---

### Post by Crafty Kisses on 2008-08-28
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by doug1212 on 2008-08-28
Hi,
I had similar issues with a webcam (logitech quickcam) it appears cheese defaults to /dev/video0 even if started with cheese -d /dev/video1 (my TV card is video0).

With camorama try changing video input to v4l in "multimedia settings" (from v4l2) and start in terminal camorama -d /dev/video1 (or whatever the webcam is).

Doug.

---

### Post by uhappo on 2008-08-29
lsusb:
```

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 5986:0137 Bison 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Ekiga/Camorama wasn't working, and cheese with both video0/video1 gave no moving picture, neither still pitcture.

---

### Post by uhappo on 2008-08-29
dmesg:
```

[   33.425155] Linux video capture interface: v2.00
[   33.507406] sdhci: Secure Digital Host Controller Interface driver
[   33.507413] sdhci: Copyright(c) Pierre Ossman
[   33.512436] uvcvideo: disagrees about version of symbol video_devdata
[   33.512445] uvcvideo: Unknown symbol video_devdata
[   33.513002] uvcvideo: disagrees about version of symbol video_unregister_device
[   33.513007] uvcvideo: Unknown symbol video_unregister_device
[   33.513178] uvcvideo: disagrees about version of symbol video_device_alloc
[   33.513181] uvcvideo: Unknown symbol video_device_alloc
[   33.513314] uvcvideo: disagrees about version of symbol video_register_device
[   33.513318] uvcvideo: Unknown symbol video_register_device
[   33.513674] uvcvideo: disagrees about version of symbol video_device_release
[   33.513678] uvcvideo: Unknown symbol video_device_release

```

---


---
title: "modprobe ivtv aborts"
date: 2005-12-05
forum: Multimedia &amp; Video
---

### Post by klaus.maier on 2005-12-05
Hello,

I would like to install my TV-Card WinTV PVR250 on Ubuntu "Breezy Badger" but when I type "sudo modprobe ivtv" I got this error message:
```
FATAL: Module ivtv not found.
``` 
I compiled the module successfully with the How-To on [ivtvdriver.org]("http://www.ivtvdriver.org"). Into the directory (/lib/modules/2.6.12/ivtv) i tried out "sudo insmod ./ivtv.ko", but then happens:
```
insmod: error inserting './ivtv.ko': -1 Unknown symbol in module
``` Now "dmesg" tell me:
```
[4295078.976000] ivtv: Unknown symbol i2c_bit_add_bus
[4295078.976000] ivtv: Unknown symbol i2c_bit_del_bus
[4295078.976000] ivtv: Unknown symbol video_unregister_device
[4295078.976000] ivtv: Unknown symbol video_device_alloc
[4295078.976000] ivtv: Unknown symbol video_register_device
[4295078.976000] ivtv: Unknown symbol video_usercopy
[4295078.976000] ivtv: Unknown symbol video_device_release
``` I don't understand why I got this error messages. The module was successfully compiled; duplicates of tuner.ko etc. were moved and so on - how the How-To on [ivtvdriver.org]("http://www.ivtvdriver.org") describes. When I compiled the module I only got the error that gcc-3.4 was not found. So I installed them and it compiled fine. But the module although will not load successful. The module is definitive here. Where is the error? Or, where is my mistake?

Thank you for any help!

---


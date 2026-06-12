---
title: "cx88xx failing to load"
date: 2008-08-08
forum: Multimedia Software
---

### Post by jammln on 2008-08-08
Hi There,

I had a nova-T tv card running fine and then I decided to install a second card which is a nova-T 500 (dual tuner).

This worked fine and I ended up with 3 adapters: 0 and 1 for the dual card, 2 for the old card.

VLC could still stream from the old card but couldn't get a lock on the new card.

I followed this howto:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")

to install v4l-dvb.

Now the new dual card works fine but the old card fails to work as the modules don't load.

dmesg says:

```
[   34.123233] cx88xx: Unknown symbol videobuf_dma_free
[   34.123341] cx88xx: disagrees about version of symbol videobuf_waiton
[   34.123344] cx88xx: Unknown symbol videobuf_waiton
[   34.123959] cx88xx: Unknown symbol videobuf_dma_unmap
[   34.124172] cx88xx: disagrees about version of symbol video_device_alloc
[   34.124176] cx88xx: Unknown symbol video_device_alloc
[   34.124605] cx88xx: disagrees about version of symbol video_device_release
[   34.124608] cx88xx: Unknown symbol video_device_release
[   34.126002] cx88xx: Unknown symbol videobuf_dma_free
[   34.126106] cx88xx: disagrees about version of symbol videobuf_waiton
[   34.126109] cx88xx: Unknown symbol videobuf_waiton
[   34.126704] cx88xx: Unknown symbol videobuf_dma_unmap
[   34.126958] cx88xx: disagrees about version of symbol video_device_alloc
[   34.126962] cx88xx: Unknown symbol video_device_alloc
[   34.127381] cx88xx: disagrees about version of symbol video_device_release
[   34.127384] cx88xx: Unknown symbol video_device_release
```

---


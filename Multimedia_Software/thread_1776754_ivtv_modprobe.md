---
title: "ivtv modprobe"
date: 2011-06-06
forum: Multimedia Software
---

### Post by janumix on 2011-06-06
Hi

I'm getting following error inserting ivtv module:

```

[  686.882569] ivtv: disagrees about version of symbol v4l2_i2c_new_subdev_cfg
[  686.882574] ivtv: Unknown symbol v4l2_i2c_new_subdev_cfg
[  686.882721] ivtv: disagrees about version of symbol video_register_device_no_warn
[  686.882723] ivtv: Unknown symbol video_register_device_no_warn
[  686.883571] ivtv: disagrees about version of symbol v4l2_device_register_subdev
[  686.883573] ivtv: Unknown symbol v4l2_device_register_subdev
[  686.883766] ivtv: disagrees about version of symbol video_devdata
[  686.883768] ivtv: Unknown symbol video_devdata
[  686.884471] ivtv: disagrees about version of symbol v4l2_device_set_name
[  686.884473] ivtv: Unknown symbol v4l2_device_set_name
[  686.884899] ivtv: disagrees about version of symbol video_unregister_device
[  686.884901] ivtv: Unknown symbol video_unregister_device
[  686.885113] ivtv: disagrees about version of symbol video_device_alloc
[  686.885116] ivtv: Unknown symbol video_device_alloc
[  686.885441] ivtv: disagrees about version of symbol v4l2_device_register
[  686.885443] ivtv: Unknown symbol v4l2_device_register
[  686.886073] ivtv: disagrees about version of symbol v4l2_device_unregister
[  686.886075] ivtv: Unknown symbol v4l2_device_unregister
[  686.886386] ivtv: disagrees about version of symbol video_device_release
[  686.886388] ivtv: Unknown symbol video_device_release

```

I think it's been stopped working since upgrading kernel to:
2.6.32-32-generic

I tried to reinstall package: linux-image-2.6.32-32-generic but still the same error appears.

What can I do ? 
BR
Janusz

---

### Post by wolfen69 on 2011-06-06
Download the firnware from [here]("http://dl.ivtvdriver.org/ivtv/firmware/ivtv-firmware.tar.gz"). Then extract and put the files into /lib/firmware

Then do
```
sudo modprobe ivtv
```

---

### Post by janumix on 2011-06-07
Thanks

Already have them there nevertheless I overwrote them - stll the same.... :(


BR
Janusz

---

### Post by wolfen69 on 2011-06-07
Do you have ivtv-utils installed?

---

### Post by janumix on 2011-06-07
Now I've got ;)
modprobe ivtv still returns the same errors

---

### Post by janumix on 2011-06-09
something to do with those ivtv-utils ??

---

### Post by wolfen69 on 2011-06-09
What version of ubuntu are you using?

---

### Post by janumix on 2011-06-09
lucid upgraded from karmic

/etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

---

### Post by wolfen69 on 2011-06-09
Unfortunately, sometimes kernels can get screwed up after "upgrading". If it were me, I would just backup and clean install Lucid. I don't have a lot of experience fixing broken kernels. Good luck.

---

### Post by janumix on 2011-06-09
I'll be waiting for new one or just downgrade to previous where it was working.


thanks.

---


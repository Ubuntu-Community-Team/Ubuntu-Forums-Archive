---
title: "Installing webcamstudio module fails"
date: 2011-01-06
forum: Multimedia Software
---

### Post by Superyoshi on 2011-01-06
When trying to compile the webcamstudio modulae (ws4gl.org) it doesn't give an error, but when I want to modprobe it....
```
FATAL: Error inserting webcamstudio (/lib/modules/2.6.32-27-generic/kernel/drivers/misc/webcamstudio.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

This is from dmesg:
```
[ 1043.969162] webcamstudio: disagrees about version of symbol video_devdata
[ 1043.969166] webcamstudio: Unknown symbol video_devdata
[ 1043.969275] webcamstudio: disagrees about version of symbol video_unregister_device
[ 1043.969277] webcamstudio: Unknown symbol video_unregister_device
[ 1043.969349] webcamstudio: disagrees about version of symbol video_device_alloc
[ 1043.969351] webcamstudio: Unknown symbol video_device_alloc
[ 1043.969428] webcamstudio: disagrees about version of symbol video_register_device
[ 1043.969430] webcamstudio: Unknown symbol video_register_device
[ 1043.969551] webcamstudio: disagrees about version of symbol video_device_release
[ 1043.969553] webcamstudio: Unknown symbol video_device_release
[ 5068.788509] webcamstudio: disagrees about version of symbol video_devdata
[ 5068.788515] webcamstudio: Unknown symbol video_devdata
[ 5068.788666] webcamstudio: disagrees about version of symbol video_unregister_device
[ 5068.788669] webcamstudio: Unknown symbol video_unregister_device
[ 5068.788800] webcamstudio: disagrees about version of symbol video_device_alloc
[ 5068.788803] webcamstudio: Unknown symbol video_device_alloc
[ 5068.788914] webcamstudio: disagrees about version of symbol video_register_device
[ 5068.788916] webcamstudio: Unknown symbol video_register_device
[ 5068.789092] webcamstudio: disagrees about version of symbol video_device_release
[ 5068.789095] webcamstudio: Unknown symbol video_device_release
```

Does anyone know about that problem? Is there a solution?
Thanks in advance

---

### Post by jeicrash on 2011-03-15
same issue here after updating v4l-dvb. Ubuntu rocks but seams to have some major issues in the video department. Hope someone come up with an answer. Till then I'll keep looking.

---

### Post by benny232391212 on 2012-03-10
same problem in natty .... see if anybody helps... :(

---


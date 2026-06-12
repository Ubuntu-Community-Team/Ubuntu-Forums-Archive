---
title: "Creative camera (05a9:a511 OmniVision)"
date: 2009-05-08
forum: Multimedia Software
---

### Post by iosifidis on 2009-05-08
Hello,

I just got a camera from a friend. It's an old camera. I use Ubuntu 8.10
lsusb gives:
```
05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
```

After googling I followed the instructions:
[http://forum.skype.com/index.php?showtopic=101297&view=findpost&p=466914]("http://forum.skype.com/index.php?showtopic=101297&view=findpost&p=466914")

MAKE gives  me errors:

```
make[2]: *** [/home/iosifidis/Desktop/webcam/ov511-2.32/ov511_core.o] Error 1
make[1]: *** [_module_/home/iosifidis/Desktop/webcam/ov511-2.32] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make: *** [default] Error 2

```

And MAKE INSTALL gives me:

```
./do_install.sh *.ko
Detected 2.6 kernel
Creating install path: /lib/modules/2.6.27-14-generic/kernel/drivers/usb/media/
Installing *.ko to /lib/modules/2.6.27-14-generic/kernel/drivers/usb/media/
install: cannot stat `*.ko': No such file or directory
Finding module dependencies
All done!

```

modprobe commands give me errors

and dmesg
gives me:

```
[37072.043763] ov511: disagrees about version of symbol video_devdata
[37072.043777] ov511: Unknown symbol video_devdata
[37072.044824] ov511: disagrees about version of symbol video_unregister_device
[37072.044829] ov511: Unknown symbol video_unregister_device
[37072.045181] ov511: disagrees about version of symbol video_device_alloc
[37072.045186] ov511: Unknown symbol video_device_alloc
[37072.045345] ov511: disagrees about version of symbol video_register_device
[37072.045349] ov511: Unknown symbol video_register_device
[37072.045999] ov511: disagrees about version of symbol video_usercopy
[37072.046003] ov511: Unknown symbol video_usercopy
[37072.046130] ov511: disagrees about version of symbol video_device_release
[37072.046134] ov511: Unknown symbol video_device_release
[37433.857533] nautilus[19548]: segfault at 60000018 ip b75ffc46 sp bfb1c430 error 4 in libgconf-2.so.4.1.5[b75df000+2e000]
[37503.860885] ov511: disagrees about version of symbol video_devdata
[37503.860904] ov511: Unknown symbol video_devdata
[37503.861938] ov511: disagrees about version of symbol video_unregister_device
[37503.861942] ov511: Unknown symbol video_unregister_device
[37503.862268] ov511: disagrees about version of symbol video_device_alloc
[37503.862272] ov511: Unknown symbol video_device_alloc
[37503.862420] ov511: disagrees about version of symbol video_register_device
[37503.862424] ov511: Unknown symbol video_register_device
[37503.862943] ov511: disagrees about version of symbol video_usercopy
[37503.862947] ov511: Unknown symbol video_usercopy
[37503.863073] ov511: disagrees about version of symbol video_device_release
[37503.863077] ov511: Unknown symbol video_device_release
[38436.604342] nautilus[19748]: segfault at 28000018 ip b7618c46 sp bfc34d50 error 4 in libgconf-2.so.4.1.5[b75f8000+2e000]
[38682.945575] ov511: disagrees about version of symbol video_devdata
[38682.945591] ov511: Unknown symbol video_devdata
[38682.946612] ov511: disagrees about version of symbol video_unregister_device
[38682.946616] ov511: Unknown symbol video_unregister_device
[38682.946936] ov511: disagrees about version of symbol video_device_alloc
[38682.946939] ov511: Unknown symbol video_device_alloc
[38682.947094] ov511: disagrees about version of symbol video_register_device
[38682.947097] ov511: Unknown symbol video_register_device
[38682.947606] ov511: disagrees about version of symbol video_usercopy
[38682.947611] ov511: Unknown symbol video_usercopy
[38682.947739] ov511: disagrees about version of symbol video_device_release
[38682.947744] ov511: Unknown symbol video_device_release

```

Does anyone knows how to help me?
Thanks

---


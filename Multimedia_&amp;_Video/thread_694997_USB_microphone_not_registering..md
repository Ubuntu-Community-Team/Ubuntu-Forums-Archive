---
title: "USB microphone not registering."
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by cowzkull on 2008-02-12
Hi, 
I'm running Ubuntu 7.10 and for some reason my USB microphone doesn't load any drivers when I plug it in. It's a "Supreme PMU1" and seems to be using a C-Media chipset.

Here's from my /var/log/syslog:

Feb 12 22:37:09 FVIII kernel: [  975.300000] input: C-Media USB Audio Device    as /class/input/input7
Feb 12 22:37:09 FVIII kernel: [  975.300000] input: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:1d.0-1
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.103375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial'). 
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.147667] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial_if0'). 
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.197985] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial_if1'). 
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.250392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial_if2'). 
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.300518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial_if3'). 
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.361952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial_usbraw'). 
Feb 12 22:37:09 FVIII NetworkManager: <debug> [1202852229.383366] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_d8c_8_noserial_if3_logicaldev_input'). 

And here's from lsusb:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0d8c:0008 C-Media Electronics, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

But as I can see in lsmod nothing seems to have anything to do with it:(
snd                    56580  11 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_seq,snd_timer,snd_seq_device


So. What can I do or where can I find a driver and how do I install it?
Best regards,
Anders

---

### Post by cowzkull on 2008-02-14
I forgot I'd compiled the new Alsa version (1.0.15rc3) only with the hda-intel driver.
I recompiled it after running "./configure --with-drivers=hda-intel,usb-audio " and everything worked properly.

:)

---


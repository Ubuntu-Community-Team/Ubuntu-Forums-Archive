---
title: "USB Video capture device doesn't work when plugged in"
date: 2010-09-25
forum: Multimedia Software
---

### Post by thelusiv on 2010-09-25
In Ubuntu 9.10, I was successfully able to use my Pinnacle Dazzle DVC 100 (a cheap USB analog video capture device). I use it for backing up old video that is stored on tapes, and it isn't working with my current install of Ubuntu 10.04. When I plug the device in, it should be detected and the em28xx module should be loaded. This fails and /var/log/messages has the following:

```
Sep 25 16:13:18 kernel: [1196215.111898] usb 2-2: new high speed USB device using ehci_hcd and address 20
Sep 25 16:13:18 kernel: [1196215.266097] usb 2-2: configuration #1 chosen from 1 choice
Sep 25 16:13:18 kernel: [1196215.399379] v4l2_compat_ioctl32: Unknown symbol compat_alloc_user_space
Sep 25 16:13:18 kernel: [1196215.399742] v4l2_compat_ioctl32: Unknown symbol compat_alloc_user_space
Sep 25 16:13:18 kernel: [1196215.400071] v4l2_compat_ioctl32: Unknown symbol compat_alloc_user_space
Sep 25 16:13:18 kernel: [1196215.426085] usbcore: registered new interface driver snd-usb-audio

```

Trying to manually "modprobe em28xx" I get the following on the command line:
```
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/v4l1-compat.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting videodev (/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/videodev.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting v4l2_common (/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/v4l2-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting em28xx (/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/em28xx/em28xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

With kernel logs looking very similar to before:

```
Sep 25 16:27:01 kernel: [1197038.364411] v4l2_compat_ioctl32: Unknown symbol compat_alloc_user_space

```


Does anyone know a solution to this problem?

---

### Post by thelusiv on 2010-09-25
It looks like a similar bug is recently affecting Arch Linux: [https://bugs.archlinux.org/task/20878?project=1](https://bugs.archlinux.org/task/20878?project=1)

---

### Post by thelusiv on 2010-09-26
I decided to see if I could use the firewire connection with Kino to copy the video from my camera instead of the DVC 100. I plug in the cable and get just about the same problem:

```
Sep 26 11:28:35 kernel: [1265532.400617] raw1394: Unknown symbol compat_alloc_user_space
```

It seems this symbol is required by the em28xx and raw1394 (and I'm guessing many other) modules, but the running kernel no longer supports this. I am using kernel "2.6.32-25-generic #43-Ubuntu". Soon I will try rebooting and using an older kernel to see how recently this problem has come up. I already checked and I do have the modules for the running kernel, so I am assuming that the proper modules are being loaded (although it's a possibility that it's loading an older version's modules for some reason, I suppose).

---

### Post by thelusiv on 2010-09-26
Well, it turns out I just needed to reboot and start using a new kernel. Oops! :mrgreen:

---


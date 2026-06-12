---
title: "GeForce MX 440 Go (NV17) Driver Issue (Hardy)"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Velcro39 on 2008-05-21
Everything was working fine, but appeared that the 3D drivers were not enable as even a 3D screen saver would run choppy. I went to check the 'Hardware Drivers' and there was an unchecked box next to nVidia 3D drivers box, so I checked it. One file was downloaded, several things installed, and it asked for a reboot.

Once the login screen arrives, all video disappears, even the backlight shuts off. How can I remove/replace these drivers. I can live with only 2D if I have to but no video is not an option.

Thanks a million.

---

### Post by Velcro39 on 2008-05-22
bump

---

### Post by Velcro39 on 2008-05-22
Ok.

So I got a bunch of stuff doing:

dpkg-reconfigure xserver-xorg

and now I'm stuck in low-res mode and trying to figure out how to install video drivers.

---

### Post by Velcro39 on 2008-05-22
Downloaded nVidia drivers from their website. Can't install because I'm using a Xen Kernel. How else am I supposed to do it?

Thanks a whole bunch.

---

### Post by Velcro39 on 2008-05-22
I was able to install the drivers with EnvyNG to get it working, and used the Screens and Graphics application.

My problem comes back to why I started this whole thing. The 3D is really slow. Slower than before. Any 3D screen saver will run.

I don't know what else to do now.

---

### Post by Xiong Chiamiov on 2008-05-22
> **Velcro39 said:**
> Downloaded nVidia drivers from their website. Can't install because I'm using a Xen Kernel. How else am I supposed to do it?

Thanks a whole bunch.
You aren't using the stock kernel?

If you can aren't getting kicked back to a login prompt, then that means X is starting fine, just you can't see anything.  I don't know about with a different kernel, but have you tried using some of [the beta drivers]("http://www.nvidia.com/object/linux_display_archive.html")?

---


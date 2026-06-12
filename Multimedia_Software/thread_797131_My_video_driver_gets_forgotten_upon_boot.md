---
title: "My video driver gets forgotten upon boot"
date: 2008-05-17
forum: Multimedia Software
---

### Post by dmsuperman on 2008-05-17
Alright, here's my issue. Whenever I reboot my machine, it goes to load X. It says that it needs to run in low settings mode, then continues to do so. The cursor is the little X, and so on. I go into a TTY, reinstall the video driver, then reboot X. After that, the rest of the time everything runs smooth.
If I don't reinstall the video driver though, it will just run in low settings mode.

xorg.conf has been reconfigured several times, at the very least the nvidia driver installer asks to run nvidia-xserver which regenerates the xorg.conf to use nvidia as the driver.


I have a nVidia 7900 GS KO, in Hardy Heron. If you need further information, please ask.

Thanks in advance for any help I can get :D

---

### Post by Xiong Chiamiov on 2008-05-17
T[ry installing the driver with gdm stopped]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

---

### Post by dmsuperman on 2008-05-17
That's the only way to install it, it complains if it's running.

---

### Post by dmsuperman on 2008-05-18
Ah, installing the beta driver seems to have fixed it. Thanks anyway guys.

---

### Post by xanas3712 on 2008-05-18
In my experience this has happened whenever I had installed the nvidia driver from the website and also installed it through apt.   In any case, what I had to do to fix this issue was to copy the nvidia module installed to /lib/modules/kernel-ver/kernel/drivers/video/nvidia.ko to /lib/linux-restricted-modules/2.6.24-16-generic/nvidia_new/nvidia.mod.o

The reason this was occurring for me was a version mismatch in what was getting modprobed at boot (the old drivers), and what x was trying to use (the new drivers).  I also sometimes had to remove nvidia_legacy and nvidia, as the system would sometimes seem to be attempting to use those as well (I'd see 96.xx or what-not listed in dmesg)

---


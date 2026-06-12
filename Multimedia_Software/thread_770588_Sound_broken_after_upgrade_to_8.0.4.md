---
title: "Sound broken after upgrade to 8.0.4"
date: 2008-04-27
forum: Multimedia Software
---

### Post by nomenclature3000 on 2008-04-27
Hi, after upgrading my inspiron 1420 from 7.1.0 to 8.0.4 my sound stopped working. I tried all the solutions in [http://ph.ubuntuforums.com/showthread.php?t=720043&page=5&](http://ph.ubuntuforums.com/showthread.php?t=720043&page=5&) but to no avail. Here is some info about my system:

```
lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

```
linux-ubuntu-modules-2.6.24-16-generic is already the newest version.
```

```

aplay -l
aplay: device_list:205: no soundcards found...

```

```

alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

The volume control tells me:

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
```

Thank you for any advice you can offer!

Adam

---

### Post by nomenclature3000 on 2008-04-27
My sound began working again once I switched to the 386 kernel:

```

sudo apt-get install linux-386

```

```

uname -r
2.6.24-16-386

```

I'm not really sure if this is a true solution, or just a hack. I'm not sure of the ramifications of using the 386 vs generic kernel.

As side effects, my webcam has ceased to function, and I have to start Gnome up manually now with startx.

Does anyone know if some tech support is available on a non-free basis? I would love to pay an expert $40 or $50 to spend an hour fixing my problems with me and teaching me a bit about the OS.

Thanks,
Adam

---

### Post by hrkljush on 2008-04-28
reloading the module works for me!
```

lsof | grep snd
#this will probably show xfce-mcs-manager
#kill it, and everything else that's using the device
kill -9 ???
sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel

```

---


---
title: "Maverick ALSA Install"
date: 2011-03-02
forum: Multimedia Software
---

### Post by Pooch on 2011-03-02
I have been fumbling around with getting sound to work properly in Maverick. I removed pulse-audio after experiencing intermittent crashes and have been following the [Comprehensive Sound Problems and Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") to attempt installing ALSA.

I have gotten as far as running './configure' on my driver's make file but I encounter an error when I attempt to 'make' my driver.

Configure Command:
```

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ca0106 --with-oss=yes 

```

Error:
```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_wrapper.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from include/linux/pci.h:58,
                 from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error: @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory
compilation terminated.

```

I have checked and the pci_ids.h file does exist at this location:
```

/usr/src/modules/alsa-driver/include/linux/pci_ids.h

```

I tried searching for a solution but nothing has worked. My kernel version is **2.6.35-27-generic**

Any help is greatly appreciated. Thanks.

**Edit:** I purged my ALSA install, rebooted and the driver appeared after calling 'aplay -l'. Sound started to work after I changed my sound preferences, adjusted levels using alsamixer and enabled 5.1 surround by setting playback to ALSA in gstreamer-properties.

---


---
title: "Microphone not working. Error when installing driver."
date: 2011-07-25
forum: Multimedia Software
---

### Post by Oodles on 2011-07-25
Hi everyone, I'm trying to get my microphone to work so I followed the instructions on [ubuntu help (option two)]("https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250#Fixing the microphone"). It was going well... until I got to "make". After a long process, this is what I got in the end:

```
  CC [M]  /home/denisse/alsa-driver-1.0.20/pci/asihpi/hpidspcd.o
  CC [M]  /home/denisse/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.o
/home/denisse/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.c: In function ‘HpiOs_DelayMicroSeconds’:
/home/denisse/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.c:34: error: implicit declaration of function ‘schedule_timeout_uninterruptible’
make[4]: *** [/home/denisse/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.o] Error 1
make[3]: *** [/home/denisse/alsa-driver-1.0.20/pci/asihpi] Error 2
make[2]: *** [/home/denisse/alsa-driver-1.0.20/pci] Error 2
make[1]: *** [_module_/home/denisse/alsa-driver-1.0.20] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make: *** [compile] Error 2
```

Could anyone please let me know what I did wrong, or how to solve this? Oh, and is there a way to undo the entire process that I've just done? I kinda want to undo it so that there wouldn't be "unknown clutter" hidden in my netbook. =\

---


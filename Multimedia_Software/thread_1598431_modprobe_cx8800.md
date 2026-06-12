---
title: "modprobe cx8800"
date: 2010-10-16
forum: Multimedia Software
---

### Post by tzg6sa on 2010-10-16
Hi All,

I've got troubles setting up my Winfast TV2000 analog TV tuner. This tuner uses CX23880 chipset and it requires "modprobe cx8800" to set the kernel module driver as it is written here [http://linuxtv.org/wiki/index.php/Leadtek_WinFast_PVR2000](http://linuxtv.org/wiki/index.php/Leadtek_WinFast_PVR2000), but I got errors.

```
:~$ sudo modprobe cx8800
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting cx8800 (/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I have looked at dmesg, but it carried no useful information for me.
```
:~$ dmesg | grep cx88
[   20.065678] cx88xx: Unknown parameter `pll'
[   20.085409] cx88xx: Unknown parameter `pll'
[ 2594.100081] cx88xx: Unknown parameter `pll'

```

The system recognize the device
```
:~$ lspci | grep -i cx
02:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
```


I use Ubuntu 10.04 with kernel version 2.6.32-25.

Could you tell me why won't the kernel module load and how can I solve this issue? Any suggestion what should I check or any help about how should I set up this card would be greatly appreciated.

Thanks!
Zoltan

---


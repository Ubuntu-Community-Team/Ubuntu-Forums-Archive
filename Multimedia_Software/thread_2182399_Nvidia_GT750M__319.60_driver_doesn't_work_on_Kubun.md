---
title: "Nvidia GT750M  319.60 driver doesn't work on Kubuntu 12.04 LTS 64 bit"
date: 2013-10-21
forum: Multimedia Software
---

### Post by Vadim_Karpenko on 2013-10-21
Installed Kubuntu 12.04, made full upgrade.
Video is Nvidia GT750M and integrated Intel  on Asus N750J notebook

```

# uname -a                                                                                                                                                      
Linux vksw 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

# lspci -v
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 129d
        Flags: bus master, fast devsel, latency 0, IRQ 255
        Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at f000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>

01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 129d
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        Expansion ROM at f7000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nouveau, nvidiafb

```

nouveau doesn't work, videocard is not detected in X
Disabled nouveau drivers
```

# tail /etc/modprobe.d/blacklist.conf 
                                                                                                                                              
blacklist nouveau                                                                                                                                                        
blacklist nvidiafb  

```
Downloaded and installed latest proprietary driver from nvidia.com
```

# lsmod |grep nvidia
nvidia               9447117  0 

```

X still not detecting Nvidia card and doesn't start
```

# cat /var/log/Xorg.0.log  
[    44.234] (II) NVIDIA dlloader X Driver  319.60  Wed Sep 25 14:04:14 PDT 2013
[    44.234] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    44.234] (++) using VT number 7

[    44.234] (EE) No devices detected.
....
Fatal server error:
[    44.235] no screens found

```
Any ideas?

---

### Post by Yellow Pasque on 2013-10-21
You need to use Bumblebee. You can't install nvidia driver directly on an Optimus system.

---


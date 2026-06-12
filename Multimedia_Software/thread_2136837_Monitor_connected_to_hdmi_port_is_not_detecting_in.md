---
title: "Monitor connected to hdmi port is not detecting in Kubuntu 12.10"
date: 2013-04-18
forum: Multimedia Software
---

### Post by nutimallikarjun on 2013-04-18
My system details.

Dell Vostro 3750 laptop

Ubuntu version:   No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.10
Release:        12.10
Codename:       quantal

linux kernal version 

Linux version 3.8.8-030808-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201304170248 SMP Wed Apr 17 06:49:45 UTC 2013

result of lspci -v for VGA 



00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 04c6
        Flags: bus master, fast devsel, latency 0, IRQ 51
        Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915


01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff) (prog-if ff)
        !!! Unknown header type 7f


nvidia-current and nvidia-setting up to date Bumbleebee is also up to date

Searched in other forums  what ever is mentioned I could did it but still my monitor is not getting detected.

---

### Post by nutimallikarjun on 2013-04-27
Upgraded system to 13.04 version. installed nvidia drivers properly 

lspci -v output

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 04c6
        Flags: bus master, fast devsel, latency 0, IRQ 51
        Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 04c6
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 4000 [size=128]
        Expansion ROM at f1000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current_updates, nvidia, nouveau, nvidiafb

But still monitor connected to Hdmi port is not getting detected. I connect the same monitor to my friend system having Windows 7 and it works fine. So this rules out that there is no issue with monitor and hdmi cable. 

Any help is appriciated

---

### Post by SimplyHuffy on 2013-09-25
[http://askubuntu.com/questions/331625/kubuntu-no-display-configuration-tool-after-upgrade-from-12-10](http://askubuntu.com/questions/331625/kubuntu-no-display-configuration-tool-after-upgrade-from-12-10) check this out man

---


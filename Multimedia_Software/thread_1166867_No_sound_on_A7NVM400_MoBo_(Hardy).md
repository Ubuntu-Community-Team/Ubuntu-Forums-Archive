---
title: "No sound on A7NVM400 MoBo (Hardy)"
date: 2009-05-22
forum: Multimedia Software
---

### Post by logixoul on 2009-05-22
```
$ sudo lshw | grep Motherboard -A5
       description: Motherboard
       product: A7NVM400
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 2.xx
       serial: MB-1234567890
``````
$ sudo fuser -k /dev/dsp
$
``````
$ lspci -v | grep Audio -A5
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: ASUSTeK Computer Inc. nForce2 AC97 Audio Controler (MCP)
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Memory at fe700000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
``````
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy
```

PCM and Master volume in alsamixer are 100% and unmuted.

Tried purging alsa-base and alsa-utils, rebooting, and installing them again.

Tried with several types of speakers and madplay/Amarok. The sound used to work until yesterday when I changed my mobo, CPU, RAM and GPU.

result of alsa-info.sh [(click here)]("http://www.alsa-project.org/db/?f=fbac38fdd4897e6dd6379b0fa842107aaff5e3bb"). Note how it says driver version is "1.0.16" which is different from the library/utilites version "1.0.15".

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia) seems to list my "nForce2" soundcard.

I would appreciate any help!

---

### Post by logixoul on 2009-05-22
Fixed!
Turns out the mobo was wired to route the audio to the front of the case and it needed a jumper setting to fix that.

---


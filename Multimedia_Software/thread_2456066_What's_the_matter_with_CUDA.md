---
title: "What's the matter with CUDA?"
date: 2021-01-03
forum: Multimedia Software
---

### Post by railgun744 on 2021-01-03
I have a NVIDIA card and installed the latest drivers and CUDA, which are correctly detected by the system, such as when running nvidia-smi

```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.27.04    Driver Version: 460.27.04    CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce RTX 3070    On   | 00000000:01:00.0  On |                  N/A |
|  0%   49C    P8    20W / 220W |    657MiB /  7972MiB |      1%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1499      G   /usr/lib/xorg/Xorg                102MiB |
|    0   N/A  N/A      2205      G   /usr/lib/xorg/Xorg                314MiB |
|    0   N/A  N/A      2346      G   /usr/bin/gnome-shell              113MiB |
|    0   N/A  N/A      4859    C+G   ...AAAAAAAA== --shared-files      111MiB |
+-----------------------------------------------------------------------------+
```

However, any time I try to run an program that actually requires it, I get some variation of "Unable to load CUDA" as an error.

What's going on here?

---

### Post by CelticWarrior on 2021-01-04
How did you installed the Nvidia drivers and Cuda?

---

### Post by railgun744 on 2021-01-04
Through the [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/) repository, I think, or anyway with apt-get.

---

### Post by railgun744 on 2021-01-04
More info:

```
update-alternatives --display cuda-11

cuda-11 - auto mode
  link best version is /usr/local/cuda-11.2
  link currently points to /usr/local/cuda-11.2
  link cuda-11 is /usr/local/cuda-11
/usr/local/cuda-11.2 - priority 112

```

```
cat /proc/driver/nvidia/version

NVRM version: NVIDIA UNIX x86_64 Kernel Module  460.27.04  Fri Dec 11 23:35:05 UTC 2020
GCC version:  gcc version 9.3.0 (Ubuntu 9.3.0-17ubuntu1~20.04)
```

---

### Post by rbmorse on 2021-01-04
My understanding is that the last driver/CUDA combination that works reliably is 450.xx with CUDA 10.1 and the machine running on a 5.8 kernel.

A driver issue.  I was hoping it would be fixed in 460, but apparently not.

---

### Post by railgun744 on 2021-01-04
So it's either a downgrade or wait for a patch/miracle?

---

### Post by rbmorse on 2021-01-04
Dunno nuttin. 

I get the feeling Jensen is getting ready to respond to (pre-reform) Linus' infamous message to Nvidia with one of his own.  I wouldn't like to see that myself, but given the miniscule user base and the fact there is no money to be made from desktop Linux, along with a series of recent developer decisions (ex., rejection of EGL support by Wayland and the GPL "condom" conundrum) that serve only to increase the time and effort required to support desktop Linux driver development I would not be surprised.

---


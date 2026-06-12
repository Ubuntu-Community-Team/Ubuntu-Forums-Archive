---
title: "nvidia-glx in Gutsy"
date: 2008-10-18
forum: Multimedia Software
---

### Post by mogs on 2008-10-18
What's wrong with my installation ?
I have just installed a GeForce4 MX 440 with AGP 8X on my desktop.
To install the restricted driver I executed the commands :
            sudo apt-get install nvidia-glx
            sudo depmod -a.
The installation end up without a hitch.
Why the file /proc/driver/nvidia/version contains :

NVRM version: NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007
GCC version:  gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

I would have expected 9643.
And above all the driver doesn't start.

Thanks in advance for any hint or tip
Maurizio

---


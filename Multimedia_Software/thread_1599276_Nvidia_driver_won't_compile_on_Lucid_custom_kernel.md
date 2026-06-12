---
title: "Nvidia driver won't compile on Lucid custom kernel."
date: 2010-10-17
forum: Multimedia Software
---

### Post by Jonie on 2010-10-17
I've been using x-swat ppa for some time on my Lucid machine. I'm also using a custom kernel, which is a recompile of Ubuntu kernel with just a tiny mod that enables me to use power saving features of an AMD CPU without breaking the operation of drivers that require realtime responsiveness.
So far, so good. When I tried to install nvidia 260.19.12 update, it failed to recompile. A more detailed investigation showed that it could not find /usr/src/linux/include/asm/asm-offsets.h and /usr/src/linux/include/linux.bounds.h. I resolved the problem by simply linking the files. But, as far as I guess, since those files do exist in /usr/src/linux-headers-2.6.foo-custom there has to be a bug so that those headers are looked for in the main tree instead of the linux headers tree (which is where the driver makefiles should look for the headers).
The funny thing is that previously I have moved the source tree (and forgot to update the symlink) and nvidia drivers compiled without a glitch. When I updated the symlink, the error occurred.
The conclusion is: there is a "preference" in the nvidia driver install system to use the main tree (if available) instead of linux-headers-version. This way, the driver will fail to install if the source tree is symlinked in /usr/src/linux as it is in the case of a custom driver.

Or, perhaps, there is a more elegant way to avoid the problem than to link/copy the files? Did anyone stumble upon this issue?

---


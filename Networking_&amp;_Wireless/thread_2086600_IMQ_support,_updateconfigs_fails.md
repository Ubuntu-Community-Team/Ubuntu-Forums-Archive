---
title: "IMQ support, updateconfigs fails"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2012-11-21
Hi,

i would like to try IMQ for ingress shaping because IFB does not support iptables MARK/CLASSIFY support.

got a older ubuntu 11.04 box where i tried to add IMQ support to the kernel without much success, heres what i did:

```

rm -r linux-2.6.38 ; \
apt-get source --only-source linux \
&& cd linux-2.6.38 && \
patch -p1 < ../linux-2.6.38-imq-multiqueue-test1.patch && \
chmod +x /home/julius/tmp/linux-2.6.38/debian/scripts/misc/* && \
fakeroot debian/rules clean && \
debian/rules updateconfigs 

```

the patch runs without any errors


which fails with:
```

Creating stub configs ...
  processing config.common.i386 ... done.
  processing config.common.powerpc ... done.
  processing config.common.armel ... done.
  processing config.common.ppc64 ... done.
  processing config.common.amd64 ... done.

Running config-check for all configurations ...

debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied
debian/scripts/misc/kernelconfig: line 160: /home/julius/tmp/linux-2.6.38/debian/scripts/misc/../config-check: Permission denied

*** ERROR: 13 config-check failures detected

```

i added the chmod line to make this error go away, but even after the scripts in that directory are all executable it fails.

what i did comes from:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://blog.avirtualhome.com/how-to-compile-a-ubuntu-2-6-35-kernel-for-lucid/](http://blog.avirtualhome.com/how-to-compile-a-ubuntu-2-6-35-kernel-for-lucid/)


this all seems overly complicated, isnt there a easier way to just add some modules to the default kernel?
i remember building kernels for lfs/archlinux/gentoo was easier.

---


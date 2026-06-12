---
title: "How to clean up after upgrade"
date: 2010-05-21
forum: Mythbuntu
---

### Post by rramesh on 2010-05-21
Hi 

  In the past few months my kernel has been upgraded several times and
all old kernels are left in the system. The grub menu is quite full. How do I tell
the system that I do not want to keep more than 3 versions of any package including kernel.

Ramesh

---

### Post by ian dobson on 2010-05-22
Hi,

You can remove old packages using :-

apt-get remove PACKAGE-NAME

so If you want to remove linux-2.6.31-20 use 
apt-get remove linux-image-2.6.31-20-generic

to get a list of "linux" kernels installed use
dpkg -l | grep linux

This will produce a list something like:-
```

rc  linux-image-2.6.24-16-generic              2.6.24-16.30                                    Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.24-18-generic              2.6.24-18.32                                    Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.24-19-generic              2.6.24-19.41                                    Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.24-21-generic              2.6.24-21.43                                    Linux kernel image for version 2.6.24 on x86
rc  linux-image-2.6.27-11-generic              2.6.27-11.31                                    Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.27-14-generic              2.6.27-14.39                                    Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.27-7-generic               2.6.27-7.16                                     Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.27-9-generic               2.6.27-9.19                                     Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.28-15-generic              2.6.28-15.52                                    Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.28-16-generic              2.6.28-16.57                                    Linux kernel image for version 2.6.28 on x86
rc  linux-image-2.6.31-15-generic              2.6.31-15.50                                    Linux kernel image for version 2.6.31 on x86
rc  linux-image-2.6.31-16-generic              2.6.31-16.53                                    Linux kernel image for version 2.6.31 on x86
rc  linux-image-2.6.31-17-generic              2.6.31-17.54                                    Linux kernel image for version 2.6.31 on x86
rc  linux-image-2.6.31-19-generic              2.6.31-19.56                                    Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-20-generic              2.6.31-20.58                                    Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.32-21-generic              2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-2.6.32-22-generic              2.6.32-22.33                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic                        2.6.32.22.23                                    Generic Linux kernel image
ii  linux-libc-dev                             2.6.32-22.33                                    Linux Kernel Headers for development
rc  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20                                  Non-free Linux 2.6.20 modules on x86/x86_64
rc  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29                                  Non-free Linux 2.6.20 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                 Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                                 Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                 Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                                 Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.27-11-generic 2.6.27-11.16                                    Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-2.6.27-14-generic 2.6.27-14.20                                    Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-2.6.27-7-generic  2.6.27-7.12                                     Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-2.6.27-9-generic  2.6.27-9.13                                     Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-2.6.28-15-generic 2.6.28-15.20                                    Non-free Linux kernel modules for version 2.
rc  linux-restricted-modules-2.6.28-16-generic 2.6.28-16.21                                    Non-free Linux kernel modules for version 2.
ii  linux-sound-base                           1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
rc  linux-ubuntu-modules-2.6.24-16-generic     2.6.24-16.23                                    Ubuntu supplied Linux modules for version 2.
rc  linux-ubuntu-modules-2.6.24-18-generic     2.6.24-18.26                                    Ubuntu supplied Linux modules for version 2.

```

If the line starts with rc then the package as been removed, a ii means the package is installed.

When you remove the "linux-image" you should also remove the corresponding "restricted-modules" and "linux-headers" packages.

Hope this helps
Regards
Ian Dobson

---

### Post by axelsvag on 2010-05-23
If you like GUI better  a lot of cleaning up can be done with Ubuntu Tweak [[HTML]http://ubuntu-tweak.com/[/HTML]

---

### Post by rramesh on 2010-05-25
Thanks for the help. I knew I could simply remove packages. I was hoping that that there is some automatic way
of purging older than 3 (installed) versions. I guess this only happens to kernel. So I can delete them manually.


Ramesh

---

### Post by ian dobson on 2010-05-25
> **rramesh said:**
> Thanks for the help. I knew I could simply remove packages. I was hoping that that there is some automatic way
of purging older than 3 (installed) versions. I guess this only happens to kernel. So I can delete them manually.


Ramesh

I would recommend using apt-get to remove the packages as it'll remove all other dependant packages (headers/modules etc) and update grub if necessary.

Regards
Ian Dobson

---


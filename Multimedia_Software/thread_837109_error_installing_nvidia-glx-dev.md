---
title: "error installing nvidia-glx-dev"
date: 2008-06-22
forum: Multimedia Software
---

### Post by anomalous_underdog on 2008-06-22
running
sudo apt-get install nvidia-glx-dev

gives me this error

```

Unpacking nvidia-glx-dev (from .../nvidia-glx-dev_1%3a96.43.05+2.6.24.500-500.24~envy_amd64.deb) ...
**dpkg-divert: `diversion of /usr/lib/libGL.so to /usr/lib/nvidia/libGL.so.xlibmesa by nvidia-glx-dev' clashes with `diversion of /usr/lib/libGL.so to /usr/lib/nvidia/libGL.so.xlibmesa by nvidia-glx-new-dev'**
dpkg: error processing /var/cache/apt/archives/nvidia-glx-dev_1%3a96.43.05+2.6.24.500-500.24~envy_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-dev_1%3a96.43.05+2.6.24.500-500.24~envy_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I had installed nvidia-glx-new-dev at one time, but I removed it. I'm certain its been removed as a purge command says its not present.

Need help fixing this, and an explanation of how these things happen so I'd know better next time =)

---


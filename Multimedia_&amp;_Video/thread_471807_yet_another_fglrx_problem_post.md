---
title: "yet another fglrx problem post"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Dodger73 on 2007-06-12
Hi all,

So, I got a brand spanking new ATI Radeon X1900XTX PCI-e in my K8N-DL (with 2 Opteron 246's), running Feisty. I have had an NVIDIA card before, uninstalled the driver, and have tried a variety of ways (pretty much all of them) to install fglrx.
Now here's the kicker. I don't have the Mesa problem. Yet, anyway. My latest fglrx install was done with envy, and everything seems to be working - except for DRI, of course. Now, Xorg.0.log tells me DRI was initialized perfectly fine, however, take a look at this:

```

$ LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.36.5 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.36.5 fglrx (screen 0)
drmOpenByBusid: busid is PCI:4:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:4:0:0
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/dodger/.drirc: No such file or directory.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  128 (XFree86-DRI)
  Minor opcode of failed request:  5 ()
  Value in failed request:  0x59
  Serial number of failed request:  27
  Current serial number in output stream:  27

```

here's the libGL links:

```
$ ls -la /usr/lib/xorg/libGL*
lrwxrwxrwx 1 root root     26 2007-06-10 17:39 /usr/lib/xorg/libGL.so -> /usr/lib/xorg/libGL.so.1.2
lrwxrwxrwx 1 root root     26 2007-06-10 17:39 /usr/lib/xorg/libGL.so.1 -> /usr/lib/xorg/libGL.so.1.2
-rw-r--r-- 1 root root 783353 2007-06-10 17:39 /usr/lib/xorg/libGL.so.1.2

```

What am I doing wrong? It seems to try to load the correct DRI module, but for some reason it's a no-go. Any hints would be greatly appreciated!

---

### Post by Dodger73 on 2007-06-15
Anybody? 
I've tried going through another couple of tutorials, but no cookie so far...

---


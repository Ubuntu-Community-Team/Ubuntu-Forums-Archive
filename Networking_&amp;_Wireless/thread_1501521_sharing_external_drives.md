---
title: "sharing external drives"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by phantalon on 2010-06-04
Hi...I have two machines, a laptop and a desktop, both running Lucid.
each works fine, but...
I can't seem to mount the external drives attached to either machine over the network.
I can share folders from the internal drives fine but when I try to access an external drive from either machine I get "unable to Mount volume".
Is it possible to mount the external drives across the network? If so, How?
I would be grateful for any help. Thx.

---

### Post by Zakhafr on 2010-06-04
It is not very clear what you want to achieve.

It seems that you want to "remote-mount" a device without having it mounted on the PC where it is connected.

I do not see why you would need such a complicated thing, and I don't know of any software doing such things. Obviously, you'll need a piece of soft on the "server" (the PC where the physical device is connected), and a piece of soft on the "client" (the PC that will access the mount).

The easyest way is:
-1) mount the device on the PC where it is connected
-2) share it (NFS, Samba,...)
-3) mount the share on the "client" PC

---


---
title: "Can mount, but not unmount a certain samba share"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by jinx099 on 2010-04-02
I am having an issue with all of my Ubuntu 9.10 machines.  I have a certain samba share that I am mounting and I can mount it and use it fine, but when I try to unmount it I get errors like this:

```
jinx@conroe:~$ sudo umount pbfd/
This utility only unmounts cifs filesystems.
This utility only unmounts cifs filesystems.
jinx@conroe:~$
```

The share does not get unmounted, AND this prevents me from rebooting, or shutting down the computer.  I am forced to do a hard power off in this state.

This just recently started happening, and I do not know what may have changed.  This does not happen on all shares, even ones from the same server.  The server is running opensolaris and samba, I am not using the built in cifs server.

Any ideas?

EDIT: more info:  it works just fine in Arch, but still not in ubuntu 10.04

---


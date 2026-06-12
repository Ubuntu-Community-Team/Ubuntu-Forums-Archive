---
title: "Automounting a share when the other computer is plugged into the network?"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2009-07-25
Hi there,

I've read quite a few of the NFS / Samba guides and tried quite a bit, but I'm still trying to figure out:

Can you have NFS (or Samba) automatically mount a share (from another computer) when that computer is plugged in to the network?

Everything I've seen of automounting shares seems to be to do with having fstab mount them at boot time like an internal drive. I'm looking for behaviour more like a usb drive where it auto mounts when another (known) computer becomes available without the user having to run a manual mount script.

---

### Post by swerdna on 2009-07-25
You could write a script whereby the machine could test at intervals to see if the remote was attached to the network and then run the mount command if test=yes.

---

### Post by Ubuntiac on 2009-07-26
> **swerdna said:**
> You could write a script whereby the machine could test at intervals to see if the remote was attached to the network and then run the mount command if test=yes.

If I knew how to code I could, yes! ;)

---


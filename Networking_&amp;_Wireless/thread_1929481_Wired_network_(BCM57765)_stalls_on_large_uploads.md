---
title: "Wired network (BCM57765) stalls on large uploads"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by kc600 on 2012-02-22
After starting an upload (scp, rsync) of a large (4Gb) file, after a few seconds the process freezes. After this, the network connection is dead: nm-applet shows [FONT="Courier New"]eth0[/FONT] to be active, but ssh gives "no route to host", mail and www don't work.

It happens regardless of where the upload originated: downloading from the remote machine has the same effect. Downloading a file of that size works fine.

The dead network connection can be restored by running [FONT="Courier New"]ifconfig down; ifconfig up[/FONT].

I'm on a MacBook Pro 8, according to [FONT="Courier New"]lshw[/FONT] my card is a NetXtreme BCM57765 Gigabit Ethernet PCIe. Running 11.10.

Edit: uploading to another machine works, so it's not just a problem of my machine.

---

### Post by roelforg on 2012-02-22
Maybe there's some sort of limit set on how much you may upload?
Just guessing here.

---


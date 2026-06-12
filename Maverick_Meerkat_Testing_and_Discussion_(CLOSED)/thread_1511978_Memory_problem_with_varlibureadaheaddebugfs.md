---
title: "Memory problem with /var/lib/ureadahead/debugfs"
date: 2010-06-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-06-17
Rebooted up after an update and found 900 MB in use with var/lib/ureadahead/debugfs mounted. Nothing running only firefox and mem was high before I ran it.

Rebooted and back to normal.

---

### Post by cariboo on 2010-06-17
I had the same problem on 3 systems running maverick, after a reboot memory usage dropped quite a bit on all three. On one system that was using over 1Gb of ram, usage dropped to 185Mb.

On the system I'm on ram usage is now 437 with just chrome open, whereas before the reboot is was using 1029Mb.

---

### Post by philinux on 2010-06-22
Still doing it. Just booted in and I've got 1 gig of ram used. It must be this ureadahead/debugfs that's getting left mounted.

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773)

---

### Post by Nr90 on 2010-06-22
same here,
First reboot after update was very slow, another reboot and things improved.
I'm unsure if the last kernel was faster.

---

### Post by philinux on 2010-06-22
Doh, 

Completely forgot I commented on this bug re lucid.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by Longinus00 on 2010-06-22
I've experienced this bug since karmic so hopefully they'll decide it's worth fixing soon!

---

### Post by psusi on 2010-06-23
Thank God!  I thought I was going insane.  I'd see this sometimes and it seemed every time I decided to dig in looking for it, it wouldn't happen.

---


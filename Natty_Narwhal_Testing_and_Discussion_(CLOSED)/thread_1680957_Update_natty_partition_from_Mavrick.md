---
title: "Update natty partition from Mavrick"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by snkiz on 2011-02-03
So last week an update broke the wireless on my natty partition. I was busy with other things, so I left it alone sure that another update would probably fix it. Now I have some time i'd like to update, sure I could plug it in to an ethernet cable. But where's the fun in that?

 Maverick is running just fine so I thought why don't I just update from here...
I know it has something to do with chroot, but I'm not sure how to go about it.

---

### Post by cariboo on 2011-02-03
You can chroot your Natty partition using the following commands:

[LIST]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Where /dev/sdXx is your Natty partition.

---

### Post by snkiz on 2011-02-03
wow thought that would be harder thanks.

---

### Post by Harry33 on 2011-02-03
> **snkiz said:**
> wow thought that would be harder thanks.

It is worth learning.
And most important, chrooting is just as easy from live-CD (or live-USB).
In case you have no bootable system installed, not even recovery mode to terminal.

---

### Post by snkiz on 2011-02-03
Yes I've done it from a live cd, but it was always the same version as installed. For some reason I thought this would be different. Better safe then sorry anyhow its my wifes netbook, she lets me have a 20 gigs to play :D

---

### Post by philinux on 2011-02-03
I put these commands into a script to make it easy.

```
#!/bin/sh
sudo mount /dev/sdb1 /mnt
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

sudo chroot /mnt bash -c 'echo "aptitude update && aptitude safe-upgrade" && bash' 
```

I just copy and paste the aptitude commands in then.

---

### Post by snkiz on 2011-02-03
Lol so this is a regular thing for you then.

---

### Post by philinux on 2011-02-03
> **snkiz said:**
> Lol so this is a regular thing for you then.

Oh yes.

---


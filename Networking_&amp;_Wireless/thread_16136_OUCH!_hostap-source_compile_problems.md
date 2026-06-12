---
title: "OUCH! hostap-source compile problems"
date: 2005-02-19
forum: Networking &amp; Wireless
---

### Post by ekko on 2005-02-19
i've had a lot of problems compiling
hostap-source on my ubuntu 2.6.10-686 kernel. i don't know if i'm
doing everything right, but here are the steps i follow:

apt-get source linux-source-2.6.10 hostap-source
cp /boot/config-2.6.10-3-686 /usr/scr/linux-source-2.6.10-2.6.10/.config
ln -s /usr/src/linux-source-2.6.10-2.6.10/ linux
tar xvzf hostap-source.tar.gz
cd modules/hostap-source/
make pci

but then make exits because it can't find things like linux/version.h
i also tried (as said in the README.debian)  with debian-rules, but
the errors are the same.

---

### Post by az on 2005-02-19
Try building the kernel headers beforehand, since the pristine kernel source with the config file is not enough.

sudo make-kpkg --append-to-version=-3-386 --revision=1 kernel_headers

---

### Post by ekko on 2005-02-20
[QUOTE=azz]Try building the kernel headers beforehand, since the pristine kernel source with the config file is not enough.

sudo make-kpkg --append-to-version=-3-386 --revision=1 kernel_headers[/QUOTE]
 hey, thanks! i wasn't used to this debian-like way of dealing with the kernel.

---


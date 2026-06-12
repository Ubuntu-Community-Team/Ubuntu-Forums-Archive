---
title: "ATI Radeon X1200 framebuffer"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by marwooj on 2007-12-16
How to enable fb (/dev/fb0) with ATI Radeon X1200 framebuffer, or how to make TVtime to work with that card?

Regards,

---

### Post by eth on 2007-12-18
I can answer the first question, maybe.
So:
```

sudo vim /etc/modprobe.d/blacklist-framebuffer

```
comment (type # at the begginning of) the line 
```

blacklist vesafb

```
so that it will look like this
```

#blacklist vesafb

```
now go to
```

sudo vim /etc/initramfs-tools/modules

```
and add those 2 lines:
```

vesafb
fbcon

```
then type in a shell
```

sudo update-initramfs -u -k all

```
then add the usual "**vga=791**" string in the kernel line in file
```

sudo vim /boot/grub/menu.lst

```
```

title           Fluxbuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 quiet **vga=791**
initrd          /boot/initrd.img-2.6.22-14-generic

```
and it should work

---

### Post by marwooj on 2007-12-19
super cool - fb works fine, thx

---

### Post by yanbee on 2008-03-24
Thank you VERY MUCH, I've been loking for this for a loooong time. Your explanation was the only way to make fb work.

---

### Post by anupamsr on 2008-07-14
eth: Here you are using VESA, right?

Do you know if the ati framebuffer module actually works or not? (I get blank screen... and VESA is very slow :( )

---


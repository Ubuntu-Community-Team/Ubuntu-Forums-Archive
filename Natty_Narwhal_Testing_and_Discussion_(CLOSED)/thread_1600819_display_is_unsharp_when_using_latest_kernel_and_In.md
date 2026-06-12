---
title: "display is unsharp when using latest kernel and Intel graphics"
date: 2010-10-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Benjamin_Lebsanft on 2010-10-19
I get an unsharp display when using the 2.6.36 kernel. Does anyone know how to fix it? Is this already known?

---

### Post by utilitytrack on 2010-10-19
Read this:
[http://ww.ubuntuforums.org/showthread.php?p=9678781]("http://ww.ubuntuforums.org/showthread.php?p=9678781")

I don't sure it's your situation, though.

---

### Post by jerrylamos on 2010-10-19
> **Benjamin_Lebsanft said:**
> I get an unsharp display when using the 2.6.36 kernel. Does anyone know how to fix it? Is this already known?

Which intel graphics?  There are a bunch.  This is i830 Thinkpad 1024x768 just fine.  I also have an i845G tower 1024x768 and it is fine.

On booting, what does your grub linux line look like?  Mine is:

#! /bin/bash
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Natty on sda3" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet 
        initrd /initrd.img
}

Obviously I don't care for all that UUID clutter so I make a file with the above menuentry in 
/etc/grub.d/06_custom
then do a sudo update-grub
and a sudo grub-install /dev/sda
since I've got several bootable partitions

Looking in /var/log/Xorg.0.log for the video driver in use:
Loading sub module "fbdevhw"

Jerry

---

### Post by Benjamin_Lebsanft on 2010-10-20
It's a X3500. Doesn't work with latest mesa/xorg/intel driver. Uninstalled the kernel and it works just fine, so it's a kernel bug I guess.

---


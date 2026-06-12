---
title: "X11 recovery dialogue on boot..."
date: 2008-07-06
forum: Multimedia Software
---

### Post by boblemur on 2008-07-06
Hi all, im on my laptop running hardy, and every time i turn it on, it stops on a graphics recovery menu, it contains continue, root repair and a few other options, and i click continue and nothing appears to be wrong with x, however it seems stuck in this loop and it displays the message every time...

---

### Post by overdrank on 2008-07-06
> **boblemur said:**
> Hi all, im on my laptop running hardy, and every time i turn it on, it stops on a graphics recovery menu, it contains continue, root repair and a few other options, and i click continue and nothing appears to be wrong with x, however it seems stuck in this loop and it displays the message every time...

HI and it sounds like you are booting into recovery mode. Are you booting to the first choice at the grub and are you dual booting with windows? Did you modify the grub menu list?

---

### Post by boblemur on 2008-07-06
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aa190b03-bd0e-4ac9-bc00-b16c8e1fc87f ro vga=771
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aa190b03-bd0e-4ac9-bc00-b16c8e1fc87f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

thats my menu.lst boot entries i dont have windows on this computer, ubuntu only :) ( slowly escaping micro$oft )


but yeh it dosent seem to be the recovery one :s but i could be wrong... 

but its not like recovery  because it just stops 1/2 way through normal boot and comes up with this menu...

but it dosent drop strait to a root terminal like recovery...

---

### Post by mcduck on 2008-07-07
You are booting into recovery mode. The recovery mode will give you that menu during the boot.

Have you perhaps configured the default boot option for Grub? In that case you should remember that the numbering starts from 0, so if you have set it to 1 now that will boot the _second_ option, the recovery mode.

---


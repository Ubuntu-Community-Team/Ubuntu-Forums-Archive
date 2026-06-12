---
title: "Can't boot with Kernel 2.6.35-1 - 3 with ATi Display Driver"
date: 2010-06-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by iA++ on 2010-06-15
when i choose all of kernel 2.6.35 in grub
it can't boot 
and in kernel 2.6.35-2 it will show ERST: Table is not found!
:confused::confused:

---

### Post by Reiger on 2010-06-15
You are using fglrx, aren't you? Welcome to the wonderful world of ABI breakage! :P

-- I'm guessing what happened is that the kernel changed in such a way that the in-memory layout of code/data has changed (ABI) to the point that your older fglrx driver is no longer able to work with it. In order to fix that the fglrx module needs to be rebuilt against the newer kernel (at the very least).

---

### Post by aviramof on 2010-06-16
Maverick Meerkat is currnetly using xserver 1.8x and the ati driver does not support this 
and soon there is going to be xserver 1.9x and then we need to wait till ati release an 
ati driver that support the new xserver versions before a new fglrx driver be released.

---

### Post by iA++ on 2010-06-16
I try to edit /etc/default/grub
add "nomodeset noapic nolapic" in GRUB_CMDLINE_LINUX_DEFAULT 

I can boot with kernel 2.6.35-x already
but plymount it low resolution 
:p

---


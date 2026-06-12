---
title: "depreciated"
date: 2010-08-11
forum: Multimedia Software
---

### Post by jtmedin on 2010-08-11
When i boot 10.04 i get: vga=791 depreciated then comments to enter this command before the linux command:gfxpayload=1024x768x16,1024x768 ... 

i know that my display will only handle 1024x768 so i need to enter that command somewhere. So where do i enter that gfxpayload ... . TIA

---

### Post by jtmedin on 2010-08-13
Bump:(

---

### Post by kaivalagi on 2010-08-13
Sounds like the options set for grub to me...your boot loader. If it's grub v.1 then take a look at you /boot/grub/menu.lst file

---


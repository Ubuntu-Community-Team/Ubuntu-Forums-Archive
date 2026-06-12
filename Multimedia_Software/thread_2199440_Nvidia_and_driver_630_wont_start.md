---
title: "Nvidia and driver 630 wont start"
date: 2014-01-13
forum: Multimedia Software
---

### Post by juanse254 on 2014-01-13
My Pc was running all good with 3.8.* kernel and the 319 driver for nvidia, i decided to upgrade the kernel to the current 3.12.7, after that the nvidia driver got fkd up and daemon wont start. I upgraded the driver to the 313 version which supposdley supported the 3.12.7 kernel, even with that it didnt work. So i just went all the way back to start, deleted all the nvidia drivers and went back to kernel 3.8.* when i booted using the noveau driver i started in low graphics mode, after trying to reinstall the 319 nvidia driver it wont start, as soon as it passes the grub it shows me the tty1 terminal right away and when i go to the graphics area is just loading and nothing comes up but a message that says Could not stop RX, we could be confusing the DMA engine when we start RX up.

Thanks in Advance

---

### Post by timluoo on 2014-01-14
I also see this kind of Nvidia issue a lot ;). imo, it looks like the driver wasn't correctly built into the 3.8.* kernel. you could check this by '```
lsmod | grep nvidia
```' after login (thru virtual console). if not, means a failed driver built. 

The Nvidia/ATI driver is built using DKMS, which should be triggered every time you upgrade the kernel or driver.  but sometimes it just doesn't ... verify you have the linux-headers-<vno>  installed too.

you can have more information from /var/log/lightdm  and /var/log/X.org.0.log

---

### Post by juanse254 on 2014-01-14
> **timluoo said:**
> I also see this kind of Nvidia issue a lot ;). imo, it looks like the driver wasn't correctly built into the 3.8.* kernel. you could check this by '```
lsmod | grep nvidia
```' after login (thru virtual console). if not, means a failed driver built. 

The Nvidia/ATI driver is built using DKMS, which should be triggered every time you upgrade the kernel or driver.  but sometimes it just doesn't ... verify you have the linux-headers-<vno>  installed too.

you can have more information from /var/log/lightdm  and /var/log/X.org.0.log


I did that already, but i dont know how to build the moudle again with the current kernel. Every time i try to it says skipping module, since there is no source code for the kernel. The linux-headers are installed an running.

---


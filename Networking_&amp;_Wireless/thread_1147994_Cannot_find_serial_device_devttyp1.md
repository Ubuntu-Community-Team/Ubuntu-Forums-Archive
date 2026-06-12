---
title: "Cannot find serial device /dev/ttyp1"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by ac7yy on 2009-05-03
I have installed ubuntu 9.04 and I am getting this error when I attempt to attach to a pseudo port. Looking into /dev ... I do not see any of the ttyp# or ptyp# device pairs. This is a change from 8.10 and prior versions. Not being an expert I am totally confused as to how to create these devices. 

Any help would be great

kim

---

### Post by ac7yy on 2009-05-31
They switched off the legacy pty/tty devices in the latest
linux distributions as it seems.  Mandriva 2009.1, Ubuntu 9.04 Jaunty, etc.
(kernel 2.6-28 and 2.6-29)

I received an interesting note from Bernard, F6BVP this morning..

 >Hi Bob,

 >Actually I received a response from a Mandriva kernel guy only 14 
minutes after I posted the "bug" report !
 >The explanation is very interesting for I did not know the trick.
 >It is explained in the Wiki pages :

 >[http://wiki.mandriva.com/en/2009.0_Notes#LEGACY_PTY_COUNT_is_now_0](http://wiki.mandriva.com/en/2009.0_Notes#LEGACY_PTY_COUNT_is_now_0)
---------------------quote-------------------
 >Other Changes
 >LEGACY_PTY_COUNT is now 0
 >Legacy pty (/dev/ttyxx) are still enabled in our kernel but we now 
create none by default, to save several seconds of boot time. If you 
need some >for an obsolete application, you can add the boot parameter 
pty.legacy_count=32 (or another number depending on your needs).


This works also for Ubuntu 9.04 with kernel 2.6-28, etc  as  I tried 
this out after receiving his mail.

Just open /boot/grub/menu.lst with an editor and add pty.legacy_count = 
32  to the boot line, like below and reboot

title           Ubuntu 9.04, kernel 2.6.28-11-server
root            (hd0,0)
kernel          /vmlinuz-2.6.28-11-server root=/dev/mapper/linux-root ro 
quiet splash pty.legacy_count= 32
initrd          /initrd.img-2.6.28-11-server
quiet

So no need to recompile the kernel :=)

73,

Bob VE3TOK

---


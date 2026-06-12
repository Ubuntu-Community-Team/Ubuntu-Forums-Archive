---
title: "fail to burn regular CD but success with DVD"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by roterl on 2006-10-28
Hi
I'm using the Edgy release, on core2due with Intel DG965SS motherboard.
On the installation I had no cdrom at all because it fail to recognize it.
Later I followed [https://launchpad.net/distros/ubuntu/+bug/67012]("https://launchpad.net/distros/ubuntu/+bug/67012") and now it recognize the cdrom.

The using K3B.
The problem is that I'm able to burn DVD disks, but when I'm try to burn regular CD it fail with message "...cdrecord has no permissions..."

My user does had the cdrom group.
ls -l /dev :[INDENT]lrwxrwxrwx 1 root root 4 2006-10-27 22:32 /dev/cdrom -> scd0
lrwxrwxrwx 1 root root 4 2006-10-27 22:32 /dev/cdrw -> scd0
brw-rw---- 1 root cdrom 11, 0 2006-10-27 22:32 /dev/scd0[/INDENT]

ls -l /usr/bin/X11 :[INDENT]rwxr-xr-x 1 root root    133 2006-08-17 15:57 cdrecord
rwxr-xr-x 1 root root 334104 2006-08-17 15:57 cdrecord.mmap[/INDENT]

* using the Nautilus CD/DVD creator it work ok.
* attached the K3B log

any one has idea?

thanks a lot,
Rotem.

---

### Post by roterl on 2006-10-30
any one ??

---

### Post by roterl on 2006-11-03
I'm still have the problem.
Does some one have an idea ?

thanks

---

### Post by tommcd on 2006-11-03
Why are you using Hoary? You should use Dapper, or better yet, Edgy, if you want up to date kernel support for newer motherboards.

---

### Post by roterl on 2006-11-03
Ops..  I'm using Edgy.  (I really don't know why I wrote Hoary. I must had too tired :-) )
I installed it just few days before the official release, and keeping updates since then.
Thanks for your note.  I fixed my original message.

I still had the problem.  I'm able to burn DVDs but not CDs.

Thanks,
Rotem.

---


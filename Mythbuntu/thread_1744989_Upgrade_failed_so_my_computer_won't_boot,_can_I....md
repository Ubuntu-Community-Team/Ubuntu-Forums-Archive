---
title: "Upgrade failed so my computer won't boot, can I?....."
date: 2011-04-30
forum: Mythbuntu
---

### Post by PatrickD-52761 on 2011-04-30
I tried an upgrade from 10.10 to 11.04 using the Live CD.  It was stuck in the "removing conflicting operating system files" portion for about 8 hours now, so I closed it out and rebooted.  I was greeted with my GRUB screen, but when I chose my default kernel, I got an {initramfs} prompt with an error about not finding init.

When I booted to the LiveCD again, the option to upgrade is not there (obviously because it can't find the files that tell it I had 10.10 installed).  So, I have three questions.

1.  If I choose to install on the same partition that I have 10.10, and do not select the option to format the partition, will that take care of my problem (I have two partitions set up: / and swap, so everything is on the / partition)?

2.  If I choose to do a complete clean install (format the partition and everything), will I be able to restore everything from a backup that I did in MythControlCentre prior to the installation (or will the password have to be the same in MySQL)?

Have a great day, and thanks.:)
Patrick.

---

### Post by kja999 on 2011-05-01
Hi,

Do you have any ideas of the state of your root directory ??
You can try to boot from the live cd then chroot to your disk and then reinstall grub (update-grub).
If you old kernel is still there it may work.

The second option sounds nicer to me though ... clean install, and with an old backup should be simpler..

---

### Post by PatrickD-52761 on 2011-05-01
> **kja999 said:**
> Hi,

Do you have any ideas of the state of your root directory ??
You can try to boot from the live cd then chroot to your disk and then reinstall grub (update-grub).
If you old kernel is still there it may work.

The second option sounds nicer to me though ... clean install, and with an old backup should be simpler..

I ended up going with a hybrid clean install.  When I would boot to the LiveCD, and use a File Manager to view the drive, half of the directories were gone.  Things like my recorded shows (in fact about 80% of the directories under /var were missing). 

As far as my previous kernels, I believe they're still there. At one point I tried booting into the "Previous versions of Linux" option on GRUB, and it showed all of them.  Of course, without anything in /sbin/init, it wouldn't go anywhere.  That's why I decided to just do the clean install (in-place upgrade).  In fact, the option that I chose was to upgrade from 11.04 to 11.04. 

In the end, I reinstalled to my drive with the same filesystem and thought I had formatted it.  However, when I booted up, all of my stuff was in my /home directory, so apparently I didn't. (I had tried a couple of times without formatting the drive in order to preserve my /home directory and anything else that it could).

So, while I lost all of my previously recorded stuff (which I had watched most of anyhow), I'm back up and running.

Thanks for the suggestions, and have a great day:)
Patrick.

---


---
title: "GNOME Desktop Locks Up on Logout"
date: 2008-07-23
forum: Multimedia Software
---

### Post by SuperMike on 2008-07-23
My GNOME Desktop locks up on logout when I use a particular Xorg.conf file that uses Xinerama mode. But when I use the first one that booted when I first installed Ubuntu 8.04 Hardy Heron, this problem goes away.

Anyone else have a lockup on logout? What's the fix?

---

### Post by kaatil on 2008-08-04
Bump.

I have same issue with you as well.

athough interesting part is that when i do it manually by 'sudo /etc/init.d/gdm stop' then 'sudo /etc/init.d/gdm start' and it work fine afterward. Make me wonder what went wrong with logout though.

---

### Post by SuperMike on 2008-08-04
> **kaatil said:**
> Bump.

I have same issue with you as well.

athough interesting part is that when i do it manually by 'sudo /etc/init.d/gdm stop' then 'sudo /etc/init.d/gdm start' and it work fine afterward. Make me wonder what went wrong with logout though.

Oh, after reporting this a week ago on Launchpad bug reports for Ubuntu, a programmer at Canonical on the video driver team told me what the fix is. Says that some video drivers do not agree with bootsplash, and when you logout, bootsplash reactivates and hangs the system before it has a chance to even flip to it. He showed me how to prove this. He had me very carefully remove the word "splash" from /boot/grub/menu.lst file, then run update-grub, and then reboot. It boots a little uglier, but then I tested logout and the bug went away. So, that proved it fixed it. He then filed it as a bug that needs to get repaired in the video driver so that it doesn't conflict with bootsplash. I don't know the status on that bug fix yet, however, so I just left my system as is and I don't experience the bug anymore for now.

---

### Post by john8791 on 2008-08-31
> **SuperMike said:**
> Oh, after reporting this a week ago on Launchpad bug reports for Ubuntu, a programmer at Canonical on the video driver team told me what the fix is. Says that some video drivers do not agree with bootsplash, and when you logout, bootsplash reactivates and hangs the system before it has a chance to even flip to it. He showed me how to prove this. He had me very carefully remove the word "splash" from /boot/grub/menu.lst file, then run update-grub, and then reboot. It boots a little uglier, but then I tested logout and the bug went away. So, that proved it fixed it. He then filed it as a bug that needs to get repaired in the video driver so that it doesn't conflict with bootsplash. I don't know the status on that bug fix yet, however, so I just left my system as is and I don't experience the bug anymore for now.

I am having the same problem with locking up on logout.  Can you be more specific on where you remove the word splash?  ie. here's part of my menu.lst

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=23c6d0ed-40ca-491c-9039-56999ab6eb41 ro
quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by SuperMike on 2008-09-01
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e5af5000-1500-4600-9700-ba2d6885dc8d ro quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

---


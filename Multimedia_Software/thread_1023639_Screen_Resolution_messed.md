---
title: "Screen Resolution messed"
date: 2008-12-28
forum: Multimedia Software
---

### Post by suniyo on 2008-12-28
Hi all,

I have just installed and than upgrade 8.10 with few additional packages. Now I want to change my screen resolution but I am unable to do so. First things I have tried were editing .conf files in /etc/X11 but the values for my driver is unknown or gnome can not detect it automatically. I am using 865gvbmsr2 mother board by jetway and has an inbuilt card for display or may be no card for display at all. In windows with some intel drivers I am able to change my resolution upto 1024x768. How do I force ubuntu to detect hardware drivers or can insert the values for it manually. I have already changed and edited xorg.conf few times and restarted rebotted gnome but it doesn't work. It never displays. Max what I get in system> preferences> screen resolution is 832x624. How do I get better resolution or there is no way at all? I am using LG Studioworks 552V monitor.

Thanks in advance.

---

### Post by suniyo on 2008-12-28
anybody out there who can solve this problem?

---

### Post by overdrank on 2008-12-28
Hi and you may try booting into recovery mode which is usually the second choice from the grub and use the xfix option. This will automatically configure your xorg. Then you should be given a choice to boot normally.

---

### Post by suniyo on 2008-12-29
> **overdrank said:**
> Hi and you may try booting into recovery mode which is usually the second choice from the grub and use the xfix option. This will automatically configure your xorg. Then you should be given a choice to boot normally.

You misunderstood it when I said it just doesn't dispaly, it just doesn't display my monitor's right resolution. But after reading a lot of stuff and LG manuals I got it all. They (my kindda monitor :D) just can not display it in linux based systems. Too primitive for them. Without changing a bit of xorg.conf I just changed my monitor with a spare one I had and it displayed right resolution. But it took me 8 hours of research and lot of learning to take my monitor out of the closet. :P

Anyway cheers !! Thanks for your comment. Busy learning/reading more about ubuntu security with servers.. Catch you people later...

---


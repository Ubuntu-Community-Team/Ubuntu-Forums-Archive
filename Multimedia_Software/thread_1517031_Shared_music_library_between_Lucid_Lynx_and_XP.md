---
title: "Shared music library between Lucid Lynx and XP"
date: 2010-06-24
forum: Multimedia Software
---

### Post by blueotter on 2010-06-24
Hi everybody!

I've decided to make the plunge and switch to linux! Actually, I plan to dualboot Win XP and Ubuntu 10.04. I figure I might as well keep XP for a few games and for syncing my iPod nano with iTunes... which leads to my question.

I want to set up my computer so that my music library on my windows partition will be accessible to Banshee (or perhaps another program) so that I can listen to my tunes in Linux. However, I want to make it so that Banshee can't actually edit my files/tags (I want to leave iTunes in charge of that). I just want it to be able to play the mp3s and aac's (none of my files are in DRM format luckily). So I guess what I am asking, is can I make my iTunes folder on the Windows partition READ-ONLY to the Linux OS maybe?

I promise my next mp3 player will be more Linux friendly :)

Thanks for any help!

---

### Post by cozman69 on 2010-12-10
A simple solution would be to mount the windows partition as read-only, or have all the files be owned by root.  That way you can be sure no changes will be written back to the mp3s.

To make the partition read only, you have to add a line for the partition in /etc/fstab, something like this:

```
/dev/sda1        /media/windows  auto    ro 0       0
```

Where /dev/sda1 is the partition of your windows drive. To find out what name is given to your windows partition, use the mount command at a terminal.

Hope this helps.

---


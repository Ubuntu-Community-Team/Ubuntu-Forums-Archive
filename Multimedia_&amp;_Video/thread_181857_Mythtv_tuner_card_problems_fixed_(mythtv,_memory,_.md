---
title: "Mythtv tuner card problems fixed (mythtv, memory, vmalloc, grub)"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by indulis on 2006-05-24
I was having major problems with mythtv- I have 3 tuner cards, and only one would work at a time.  /var/log/messages had a message about running out of vmalloc memory (check with cat /proc/meminfo ). 

Of COURSE!  I recently took my system from 768GB to 1GB of memory, so naturally there is less memory available so now my apps fail(!!!!!what are those kernel guys thinking???).

Problem symptoms are having tuners work sometimes and not other times, lots of messages in the mythtv logs about not being able to allocate memory and invalid file handles, then you get 0 length files and all sorts of other Bad Things (tm).  Okay, I should have checked the system messages earlier, but it really looked like a mythtv problem!

The solution is to add an "uppermem" line into GRUB before the kernel line, and add vmalloc=192m to the end of the kernel line, so in my case /boot/grub/menu.lst looks like this

```

....
## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-k7 with additional vmalloc
root            (hd0,0)
uppermem        524288
kernel          /vmlinuz-2.6.12-10-k7 root=/dev/mapper/rootvg-root_lv ro quiet splash vmalloc=192m
initrd          /initrd.img-2.6.12-10-k7
savedefault
boot
```

---

### Post by gitfiddler on 2006-05-25
Wow, thanks for the tip. I'm planning on adding an additional tv card to my setup, and this might come in handy.
indulis, how did you figure this out? Also, what is the significance of "vmalloc=*192m*"?

---


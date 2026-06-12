---
title: "kernel panic"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by libihero on 2010-10-06
I can't boot into maverick or recovery mode for it, it gives me an error that says kernel panic and that it can't mount vhs or something like that

any way to fix it?

---

### Post by Claus7 on 2010-10-06
Hello,

this sounds like a hardware failure to me. Have you noticed anything lately? Could you check the interior of your pc to see if everything (cables, graphics cards, memory e.t.c.) are properly plugged and are ok?

Also put an ubu cd, boot from there and check if you will get any error. That way you will be able to put aside any...mischievous bug. Just some thoughts. 

Better if you gave us some specs of your machine.

Regards!

---

### Post by drs305 on 2010-10-06
If the addresses of the Grub2 menu entries are not correct the behavior you describe can happen.

Do you get the grub menu? If so, press "e" to inspect your menu entry. 

From the main menu, you can also press "c" to get to the grub prompt. From the prompt, you can type "ls" to see what partitions you have and "set" to see what the Grub 'presets' are. 

If you know the partition, you can type the following:
```
ls (hdX,Y)/boot  # Example: ls (hd0,1)/boot
```

Can you see your Ubuntu files.

If so, you can refer to the following which can help you boot from the G2 command prompt:
[Command Line and Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")

---

### Post by libihero on 2010-10-06
grub does come up, and i think the error might be with it
when i press e on my ubuntu partition, it gives me something like this (i wrote it on piece of paper)

recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy -fs-uvid*? -***** extra stuff
519
linux /boot/vmlinuz *** kernel etc.

i can recognize it shouldnt be "msdos4" but "sda4"... so if i reinstall grub should it fix it?

---

### Post by drs305 on 2010-10-06
There are times a partition can be designated with "msdos" but I don't think it should be there in your case. I would reinstall or purge and reinstall Grub2 from a LiveCD if you can't boot into Ubuntu at all.

Here is a guide I wrote to take you through the 'chroot' process if a normal install (also detailed) doesn't work:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by libihero on 2010-10-06
it worked!  thanks!

---


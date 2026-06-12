---
title: "Help Please!! Problem  with  file system??"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jstarr20052005 on 2010-10-02
When I boot, I get to Grub and choose the first selection then get this screen. I have tried what it says, to no avail.. and I have tried all my options in grub.. 


thanks - jake
[http://www.flickr.com/photos/27218645@N03/5013391054/](http://www.flickr.com/photos/27218645@N03/5013391054/)

---

### Post by cariboo on 2010-10-02
Have you tried booting from the Live CD and reinstalling grub? To do so, Once you are at the desktop open a terminal and type the following:

[list]
[*] sudo mount /dev/sda1 /mnt
[*] sudo mount -o bind /sys /mnt/sys
[*] sudo mount -o bind /dev /mnt/dev
[*] sudo mount -o bind /proc /mnt/proc
[*] sudo chroot /mnt
[/list]

Once you are at the prompt type:

```
grub-install /dev/sda
```

Once that command has run, it should tell you it completed without errors. type the following command:

```
sudo update-grub
```

You should see a listing of all the operating sustems you have installed.  Once the command has finished, press Ctrl-D and reboot.

---

### Post by clyderino on 2010-10-03
> **cariboo907 said:**
> Have you tried booting from the Live CD and reinstalling grub? 

I had a carefully customized GRUB2 splash screen and menu with 4 operating systems which was overwritten when I installed Maverick to an open partition...

With your instructions, I was able to restore the old GRUB menu in minutes! (I was not able to find solution to the problem in documentation anywhere else.)

Thanks! :P

---


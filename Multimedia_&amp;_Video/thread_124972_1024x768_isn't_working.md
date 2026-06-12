---
title: "1024x768 isn't working"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by ashrack on 2006-02-02
With the kernel that came with BREEZY I can set the resolution for Virtual Terminal at 1024x768x16 with VGA=0x317 and it works great
```
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet vga=0x317
```
but with the kernel I built myself:
```
kernel		/boot/vmlinuz-2.6.12-hibernation root=/dev/hda5 ro quiet vga=0x317
```
I get a black screen right after the VGA=0x317 is passed to the kernel. But after X starts I get video back.

---

### Post by ashrack on 2006-02-03
So I compiled a new kernel following guide [Kernel Compilation for newbies]("http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel+com%2A")

And used ```
config-2.6.12-10-386
```
So the kernel would compile with all the settings that the native BREEZY kernel has. But VGA=0x317 still gives a blank screen.
I fail to see the logic here.
PLease could someone help out here??

---

### Post by POLO on 2006-02-03
if you can, just reinstall (easiest way)
When you get to the "boot:" just hit "enter" to install.

When you get to the screen resolution menu, just select the screen resolution witht the space bar and unselect the defualt resolutions (e.g. 1024, 800, 600)

I haven't tried this with just opening "sudo dpkg-reconfigure xserver-xorg" with terminal and then selecting your screen resolutions and unselecting the defaults but that may work for you.  After finally getting my 1680,1050 to work I don't want to mess that up!

---

### Post by ashrack on 2006-02-04
[QUOTE=POLO]if you can, just reinstall (easiest way)
When you get to the "boot:" just hit "enter" to install.

When you get to the screen resolution menu, just select the screen resolution witht the space bar and unselect the defualt resolutions (e.g. 1024, 800, 600)

I haven't tried this with just opening "sudo dpkg-reconfigure xserver-xorg" with terminal and then selecting your screen resolutions and unselecting the defaults but that may work for you.  After finally getting my 1680,1050 to work I don't want to mess that up![/QUOTE]
But that is only for X server. Which U can easily change just by editing 'xorg.conf'
I need it for the boot up. And also for the virtual terminals 1-6

---

### Post by POLO on 2006-02-04
Sorry I = newb

Can't help you

---

### Post by ashrack on 2006-02-04
[QUOTE=POLO]Sorry I = newb

Can't help you[/QUOTE]
ehh no problem
the main thing is that U tried to help

---


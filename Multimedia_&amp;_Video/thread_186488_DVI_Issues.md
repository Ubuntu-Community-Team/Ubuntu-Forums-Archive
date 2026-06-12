---
title: "DVI Issues"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Roger Mudd on 2006-06-02
Just installed Dapper Drake. After installatin and re-boot I got to GRUB, allowed GRUB to run its course and was then greeted by a black screen on my Dell 2005fpw informing me that there was no DVI signal. Performed a hard shutdown (Ack!) and booted into "safe mode" as root. Presto! Dapper Drake in all its glory (albeit at an ugly stretched resolution).
I'm driving the Dell 2005fpw with a Sapphire ATI 9800 Pro via DVI so I thought I might have to install the ATI drivers to resolve the resolution issues. Followed the instructions here:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Attempted to reboot (which is no easy task when in "safe mode"). Eventually logged out of X and attempted to reboot using:

```
shutdown -r
```

However, my system did not reboot. It simply restarted X and brought me to the login screen. I logged in as myself (not root) and, luckily enough, it appeared the that the steps outlined above fixed my resolution issues.
Unfortunately, when I rebooted the machine a moment later (not in "safe mode"), I experienced the same problem (no DVI signal).
I'm a little out of my league here. Anybody have any ideas?

---

### Post by Roger Mudd on 2006-06-08
Thought I had the problem solved, but for some reason it's back. Seems like it's searching for a VGA connection rather than the DVI connection that's in use. Recover Mode works, but that obviously dumps me into the system as root and I have to manually start X. Is there a configuration file somewhere that I can edit? Is it a bios issue? Any help is greatly appreciated!

---

### Post by mwolfe on 2006-06-12
Yeah i seem to be having a similar issue 
(or possibly the same, i'm not sure)
Its been occuring since i had breezy though. I have a dell 1905fp monitor and a radeon x600 pci express card. When i boot the pc, after grub the screen goes blank. Then when the screen shows up as i get to the login manager (gdm).
Originally x didnt start up but i've got all that working by following the tutorials on installing ATI cards. However, i've never been able to resolve the issue of my screen going blank during the boot process. Its not a huge deal but i'd prefer to be aware of whats going on, especially in those cases where things don't load correctly.

If anyone has any insight on the problem, i'd (or we'd) appreciate it, i really don't know where to look. Also, as of a few weeks ago i couldnt find any other sources of the exact problem i'm having on google or dell forums so i dont know whats up with it..

---

### Post by eternalsword on 2006-07-09
I get the no dvi input, but it only lasts until the login screen, that is only while the core files, drivers, etc are loading.  Maybe try just waiting a bit to see if the login screen loads.

---

### Post by mwolfe on 2006-07-10
Yeah i've never been able to get the screen to display during the boot process.. Its annoying but not a real big deal.. sure wish i could find an easy solution.. my guess is its something small but i've only heard of a few other people with this problem so it hasnt gotten much attention.

---

### Post by mwolfe on 2006-07-12
I got this information from the thread here:
[http://www.ubuntuforums.org/showthread.php?t=212832&highlight=blank+screen](http://www.ubuntuforums.org/showthread.php?t=212832&highlight=blank+screen)

in your /boot/grub/menu.lst file
add vga=791 to the kernel line 

```

title Ubuntu, kernel 2.6.15-23-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash **vga=791**
initrd /boot/initrd.img-2.6.15-23-686
savedefault
boot

```

then it should work on boot
(you'll need to edit the file as root using sudo)
also just add the vga=791 part, dont use my boot options as they probably arent the same

---

### Post by eternalsword on 2006-07-12
I used vga=795 for 1280x1024 full colors and I must say it looks much better in addition to allowing me to see it with dvi

---

### Post by mwolfe on 2006-07-13
I'll have to change mine to 795 as well since that would match my native resolution, thanks

---


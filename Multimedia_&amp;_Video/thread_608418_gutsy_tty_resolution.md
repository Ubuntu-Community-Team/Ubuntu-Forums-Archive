---
title: "gutsy tty resolution"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by kaiju on 2007-11-10
i'm trying to set a higher tty resolution on my ubuntu gutsy installation, so that i can properly use command-line programs outside of the x session. however, with the vga=nnn option in /boot/grub/menu.lst - that used to work for feisty - i only get a blank screen during bootup and messed-up images from x, if i later try to switch to one of the tty's. in the menu.lst file for grub, i have explicitly specifyed verbose instead of splash and quiet and that works too, unless i also use the vga option.

any ideas on what might be the problem or where i could find some info on the issue are appreciated.

peace

---

### Post by patis on 2007-11-11
The font in my console got all screwed up when I upgraded from Feisty to Gutsy. I fixed it by running the command

```
$ sudo dpkg-reconfigure console-setup
```

One of the questions you get to answer is the default font for your console. Mine was set to "fixed" which simply looked ugly. I changed it to "vga" and now I have clear fonts.

Hope it helps.

---

### Post by kaiju on 2007-11-11
hm...
i tried ```
sudo dpkg-reconfigure console-setup
``` and set the font to vga (i also fiddled with font sizes 16/14/8, but that didn't help much, as it only shrunk the font on a vertical axis). still, when i try to use the vga=nnn parameter for grub, i lose all boot-time feedback. so now at least i know that my computer doesn't use vga anymore for some reason. i'll only have to somehow enable it again :P

anyway, thanks for your reply, patis

---

### Post by mariogiov on 2007-11-16
this worked perfectly for me - i chose the vga font size 16 and now tty(1-6) are correctly displayed (previously, with the "fixed" font, the text ran off the right side and bottom of the screen, and tty1 was blank). thanks!

---

### Post by neto07 on 2008-01-03
thank you, it worked for me as well!

---


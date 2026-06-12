---
title: "Boot sequence not visible with 19&quot; LCD Display"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by ricardo06 on 2006-08-18
Hello,

I just installed a 19" LCD monitor on my PC. After the necessary adjustments to have it display in 1260x1024, I notice that the boot sequence is invisible. I must wait until the logon screen appears to be able to see something on the screen. 
Actually, I can see the very first lines of the boot sequence then black hole....

Similarily if I press CTRL + ALT F2 when in gdm, the monitor just says "OUT OF RANGE" so i  cannot work in console mode.

anybody has an idea ?

thanks a lot

Richard

---

### Post by glennric on 2006-08-18
Try typing
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
in a terminal

---

### Post by ricardo06 on 2006-08-19
no still the same.
I went into the bios setup utility to check wether there is a specic set-up for that kind of monitor but i did not find any.

Richard

---

### Post by tseliot on 2006-08-19
Type:
```
sudo nano -w /boot/grub/menu.lst
```

look for this line:

```
# defoptions=quiet splash
```


Put "vga=791" after "splash"

Save and exit: press CTRL+X

Then type this in Terminal or Konsole:

```
sudo update-grub
```


and restart your computer



P.S. did you install the graphic driver for your card?

---

### Post by ricardo06 on 2006-08-21
Still does not change anything.
About the graphic card drivers, I have not installed anything special. I know for sure that, with my old 17" CRT it used to be all right.
With the current configuration, the bios-boot sequence just flash for a second.

Richard

---

### Post by ricardo06 on 2006-08-26
Thanks a lot tseliot. It finally worked with your last post. Well almost ...now the very first steps of the boot sequence are in the dark. Anyway I can live with this.

Cheers

Richard

---


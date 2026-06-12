---
title: "&quot;Out of Range&quot; monitor message"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by Kivamaki on 2007-05-05
Well I got ubuntu to sort of start up, I hit F6 on the boot screen and remove the "quite slash -- " and hit enter. Goes through a series of text, then after it's done. My monitor shows "Out of Range".

Searching google and the forums have said to make sure your refresh rate is 60, which I checked and it is set at 60 under my graphic settings for windows.

I also see people takling about "xorg.conf" which I had no idea what that is or where it's located. Plus I have no idea where to put in these "sudo" commands.

---

### Post by taurus on 2007-05-05
Boot into recovery mode from GRUB menu and reconfigure your X again.

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Kivamaki on 2007-05-05
Ok well I'm new to Linux:

1.) What is the GRUB menu
2.) How do I execute that command?

---

### Post by taurus on 2007-05-05
GRUB is a bootloader for Linux.  When you first turn on your computer, it will probably display a logo of your mobo and then GRUB will load.  You have three seconds to press the Esc key to see the menu.  On that menu, there is an option, usually the second one, that allows you to boot into recovery mode.  Use the down arrow key to highlight that option and hit Return to boot from it.  And once it's up, you will see a prompt where you enter that command to reconfigure your monitor again.

---

### Post by Kivamaki on 2007-05-05
> **taurus said:**
> GRUB is a bootloader for Linux.  When you first turn on your computer, it will probably display a logo of your mobo and then GRUB will load.  You have three seconds to press the Esc key to see the menu.  On that menu, there is an option, usually the second one, that allows you to boot into recovery mode.  Use the down arrow key to highlight that option and hit Return to boot from it.  And once it's up, you will see a prompt where you enter that command to reconfigure your monitor again.

When I restart my computer, I insert the CD in it. And it loads the ubuntu interface (boot). WHere I have the options of "Start or install ubuntu", "Start in safe graphical (something)", "CD Error Check" and some other options I can't remember. So I never hit "ESC".

Do I want to go into that non-graphics mode?


Also, at the boot screen, I hit F6 for more options, and it gave a little text box, and I typed in the code you gave me and it's doing a long test.

---

### Post by taurus on 2007-05-05
Wait, you haven't installed Ubuntu on your machine.  You are just running it from the LiveCD!

---

### Post by Kivamaki on 2007-05-05
> **taurus said:**
> Wait, you haven't installed Ubuntu on your machine.  You are just running it from the LiveCD!

Yeah..I"m trying to boot it up. But I get the "Out of Range" message on my monitor. Or if I click "Start ubuntu", I just get a black screen after the logo.


Edit: Ok, for the black screen, I just hit control and the screen comes back on, but it's just a endless list of errors.

---

### Post by Kivamaki on 2007-05-05
Still getting "Out of range" message when trying to boot from the Live CD. I tried lowering my screen resolution, but then the screen just comes out with a whole bunch of lines that blink.

---

### Post by Dianne Nilsen on 2007-07-06
Solution:  When using a mother board with on board video (vs. independent video card), the  video requires use of shared memory. Therefore, an &#8220;OUT OF RANGE&#8221; video memory error code is generated.  Supposition is that UBUNTU requires all use of memory and cannot share it during installation.  Installed an independent video card and ran the installation again.  Kernal loaded and it went fine.

---


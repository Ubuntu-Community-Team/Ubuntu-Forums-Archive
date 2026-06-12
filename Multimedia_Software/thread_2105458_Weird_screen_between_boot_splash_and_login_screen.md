---
title: "Weird screen between boot splash and login screen"
date: 2013-01-16
forum: Multimedia Software
---

### Post by Katzenkorb on 2013-01-16
Hello everyone,

during bootup, between the boot splash and the login screen, I see a multicolored pattern (like TV noise screen in colors?) for a few seconds most of the times. The worse part is, sometimes it will show my desktop wallpaper clearly, but sometimes even my screen at some point I was working under Ubuntu. In the latter case, parts of this "screenshot" are shifted horizontally.
I assume it is some graphical problem.

Also, before the grub screen appears, I get two error messages for what feels like nanoseconds. After dozens of reboots, they'll most likely say:

error: no suitable video mode found
error: no video mode active

After I select the grub entry for Ubuntu, there will appear something like:

vga = 769 (or 796) is deprecated. Use set gfxpayload = number x number x number, number x number, instead

Again it's too fast to read the numbers.

I'd be glad if someone can help.

---

### Post by Merrattic on 2013-01-16
I get this after a fresh install to most of my machines. Usually resolved by installing the proprietory video driver and rebooting a couple of times to let things settle in. I have nvidia graphics.

---

### Post by ManamiVixen on 2013-01-17
If you are running a Nvidia card, there is a script called "fixplymouth-precise" which will correct the bootloader. Just need to run it once. but make sure you revert all the changes you did on your own before running it for stability/safety sake.

Just google search the script to find it. It also works fine on 12.10 Quantal. :p

---

### Post by Katzenkorb on 2013-01-20
@ ManamiVixen:
Which changes do you mean? The ones to the fixplymouth-precise script?

---

### Post by Katzenkorb on 2013-01-20
@ Merrattic:
Thank you, it worked. I somehow forgot about installing the proprietary graphic drivers.

---

### Post by ManamiVixen on 2013-01-20
Katzenkorb, fixplymouth-precise automatically edits grub and adds the correct resolution and such on boot so Plymouth can properly draw itself. It supposed to be used for proprietary drivers but can be used for the open source ones if desperate enough to have a proper boot. Desperate being it sets the resolution permanently until the proprietary  drivers are installed and usually the resolution is not that of the monitor, but close enough. Like my monitor is 1680x1050 but on boot it's 1280x800. But after boot it goes back to 1680x1050 with the Nvidia Driver loaded.

---

### Post by Katzenkorb on 2013-01-27
Hi, ManamiVixen!

I don't have Nvidia, I have an AMD Radeon graphics card. So that explains why I couldn't find the script you mentioned. Any other suggestions?

---

### Post by Katzenkorb on 2013-02-10
Well, at least the main problem is solved.

---


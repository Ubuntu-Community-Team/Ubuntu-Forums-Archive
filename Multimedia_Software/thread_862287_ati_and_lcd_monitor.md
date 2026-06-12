---
title: "ati and lcd monitor"
date: 2008-07-17
forum: Multimedia Software
---

### Post by hasek522 on 2008-07-17
Ok to start off i am a complete linux newb.  So I just installed ubuntu and then was asked if i wanted to install the proprietary ATI drivers so i did so.  Ubuntu was working fine until these drivers were installed.  Once I installed the drivers i restarted the computer only to when I boot up have my monitor give me an error message telling me it cannot display the video source.  How can I fix this?

I have an ati 1600 graphics card
with a dell lcd flat screen

---

### Post by xc3RnbFO8P on 2008-07-17
Your post yesterday:
> I just installed Ubuntu on my desktop with an ati radeon x800 graphics card and the display is very ugly right now. Very grainy and out of proportion. One of the notifications i see is a prompt asking me whether to install restricted drivers for my graphics card. Is this a safe step i can take to improve the display or is there other steps I should take.
Do you have a blank screen?

---

### Post by hasek522 on 2008-07-17
yes the screen is completely black

---

### Post by xc3RnbFO8P on 2008-07-17
Reboot your PC and when you see the "GRUB menu loading" prompt, hit ESC.

Then boot into "Recovery" mode.

Once at the root prompt, enter:
**dpkg-reconfigure xerver-xorg -phigh** <ENTER>

And then:
reboot<ENTER>

That should try to create a new graphic configuration file using autodetection.

---

### Post by hasek522 on 2008-07-17
ok so i took the step and now ubuntu boots and i can see things but everything is really ugly and the text seems really grainy and a little hard to read.  What step can i take now.

---

### Post by xc3RnbFO8P on 2008-07-17
ALT+F2
Copy/Paste this:
> gksudo displayconfig-gtk
Choose **Generic** 
and resolution that your monitor supports.

---


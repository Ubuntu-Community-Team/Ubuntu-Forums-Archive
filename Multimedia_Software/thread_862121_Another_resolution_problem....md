---
title: "Another resolution problem..."
date: 2008-07-17
forum: Multimedia Software
---

### Post by mefi on 2008-07-17
Hey there!

So I\ve just installed Ubuntu *dual/boot with Vista) and I've been having some problems with screen resolution. I have entered a few extra lines into the xorg.conf, which did not help at all. I was stuck on 640x480, with all attempts to change resulting in failure.
Then I installed ATI drivers from the sticky thread in this subforum, and rebooted. What happened first was that the login/menu was larger than the screen, I barely saw the field in which to enter username and password.
And well in, the resolution is set to 600x800, which is improvement.
I have also gotten a few choices in the resolutions-drop-down-list, but when I choose a bigger one, it results in black areas below and to the right of the desktop!

How do I solve this, once and for all?

Thanks in advance!

---

### Post by nikgare on 2008-07-18
> I have also gotten a few choices in the resolutions-drop-down-list, but when I choose a bigger one, it results in black areas below and to the right of the desktop!

push the "Auto-adjust" button on your monitor?

---

### Post by mefi on 2008-07-18
> **nikgare said:**
> push the "Auto-adjust" button on your monitor?

Well after next reboot the problem was solved - for my computer-monitor.
The problem remains for my LCD TV, and there is no Auto Adjust on it :) :O

---

### Post by xc3RnbFO8P on 2008-07-18
Try
atl+f2
> gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports

---

### Post by mefi on 2008-07-18
> **Ringi said:**
> Try
atl+f2

Choose Generic
and resolution that your monitor supports

for my TV?

---

### Post by xc3RnbFO8P on 2008-07-18
Yes, is it 16:9, 480p, 720p, 1080p?

---

### Post by mefi on 2008-07-18
> **Ringi said:**
> Yes, is it 16:9, 480p, 720p, 1080p?

When opening that config I'm only able to set properties for my computerscreen..
Maybe after a reboot though..

I think it is 720p, it's not FullHD, but HD Ready.

---

### Post by xc3RnbFO8P on 2008-07-18
DVI or VGA cable?
DVI 1360x768
VGA 1024x768

---

### Post by mefi on 2008-07-18
> **Ringi said:**
> DVI or VGA cable?
DVI 1360x768
VGA 1024x768

Aha, yeah it's VGA, som 1024x768 then?
But in Windows I'm running it on 1280x768!

---

### Post by xc3RnbFO8P on 2008-07-18
> Aha, yeah it's VGA, som 1024x768 then?
But in Windows I'm running it on 1280x768!
There are many threads about this,
but no easy solution that I know about.

---


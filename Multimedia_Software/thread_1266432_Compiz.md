---
title: "Compiz"
date: 2009-09-14
forum: Multimedia Software
---

### Post by hipporhinostricow on 2009-09-14
Hi,
Im wondering what the lowest limit is for desktop effects to be enabled:
Ive got a 32MB card which cannot enable desktop effects...
Is this so with all small memory cards? or is it just too old?
(got in 2000)

---

### Post by overdrank on 2009-09-14
> **hipporhinostricow said:**
> Hi,
Im wondering what the lowest limit is for desktop effects to be enabled:
Ive got a 32MB card which cannot enable desktop effects...
Is this so with all small memory cards? or is it just too old?
(got in 2000)

Hi and welcome, I have 2 system that run the effects with 32mb memory. What is the model of the graphics card and have you installed any drivers?
You may use the command in the terminal ```
lspci | grep VGA
``` to identify your hardware. The terminal is located under applications, accessories. Your password will not show when you are typing in the terminal. :)

---

### Post by hipporhinostricow on 2009-09-15
Here's what it said:
01:00.0 VGA compatible controller: nVidia Corporation NV15DDR [GeForce2 Ti] (rev a3)
The odd thing is, the splash screen before bootup says that the card is a Geforce 2 GTS, not Ti.
Any ideas why that is either?
Thanks

---

### Post by hipporhinostricow on 2009-09-15
Oh, i forgot to add; No, the drivers do not want ot load in Xorg. They cant be found...

---

### Post by overdrank on 2009-09-15
> **hipporhinostricow said:**
> Oh, i forgot to add; No, the drivers do not want ot load in Xorg. They cant be found...

Ok I am assuming you are using Jaunty 9.04. The geforce 2 maybe to old. After you installed the drivers ( I assume again from the hardware drivers under system, administration) you may try and boot into recovery mode and use xfix option. Recovery mode is usually the second choice when booting from the grub. After selecting and completing xfix you should be given 4 options and choose to boot normally.

---

### Post by hipporhinostricow on 2009-09-18
The hardware drivers told me there are no proprietary drivers...
But! Ive found the correct driver on the NVIDIA site.
However, it cant be found by shell when on the terminal.
Also, the gdm seems to have stopped working...
It says its successfully stopped, even when the display is still running...
Any ideas?
Thanks

---


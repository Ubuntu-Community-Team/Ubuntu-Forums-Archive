---
title: "ATI causes Ubuntu to freeze when 3D is used"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Wark on 2007-05-27
Hello

I've been trying to install Ubuntu Feisty Fawn for a few days now, and I keep running into the same problems. After installing the ATI proprietary drivers, the system invariably freezes up after attempting to do anything with 3D. So far, I've tried running Google Earth and trying a screen saver, and they both cause it to freeze. I have tried both of the methods on [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), as well as simply enabling it through Ubuntu's restricted hardware program. The driver installs just fine without any errors, but it still locks up the system when I actually go to use it. Any ideas why this is happening?

I'm currently using an ATI Radeon 9600xt with an AMD Athlon XP 2500+. Let me know if you need any other specs.

---

### Post by Lucifiel on 2007-05-27
> **Wark said:**
> Hello

I've been trying to install Ubuntu Feisty Fawn for a few days now, and I keep running into the same problems. After installing the ATI proprietary drivers, the system invariably freezes up after attempting to do anything with 3D. So far, I've tried running Google Earth and trying a screen saver, and they both cause it to freeze. I have tried both of the methods on [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), as well as simply enabling it through Ubuntu's restricted hardware program. The driver installs just fine without any errors, but it still locks up the system when I actually go to use it. Any ideas why this is happening?

I'm currently using an ATI Radeon 9600xt with an AMD Athlon XP 2500+. Let me know if you need any other specs.

Flgrx = piece of rubbish that should never be installed on your system. 

I'm not too sure what other drivers you can try but you really should uninstall flgrx as soon as possible.

---

### Post by Wark on 2007-05-27
I uninstalled fglrx, and (as before I installed the ATI drivers) everything is completely stable. However, while I can test the screen saver just fine, it seems Google Earth does not like the old drivers at all. And while Google Earth is not an absolute necessity (I have a Windows laptop as well as the desktop I'm testing Linux on), it kinda defeats the purpose of installing Linux if I still have to depend on Windows.

[EDIT] And by "not liking the old drivers", I mean, does not seem to use them, as the 3D is extremely choppy. [/EDIT]

---


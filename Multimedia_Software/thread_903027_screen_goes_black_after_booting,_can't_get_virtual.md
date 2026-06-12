---
title: "screen goes black after booting, can't get virtual terminal"
date: 2008-08-27
forum: Multimedia Software
---

### Post by bcrowell on 2008-08-27
I have a machine with xubuntu on it. It was working with a particular monitor. Now I have a different monitor, and when I boot, I get the xubuntu flash screen, but then it goes black and there's no gdm login screen. Hitting control-alt-F1 doesn't give me a virtual terminal; the screen just goes black. I tried swapping in a different monitor (probably not the original one, I don't even know at this point), and it still didn't work.

Any suggestions on how to handle this? It seems like I can't accomplish much unless I can interrupt the booting process before it tries to display the login screen.

---

### Post by ghoster on 2008-08-28
If you watch carefully while your computer starts up, you will see Grub gives you a couple of seconds to hit the escape key and select different start up options. Select recovery mode, which will then give you a choice to try and automatically repair your xorg.conf, drop to a shell, etc.

---

### Post by Mister.Vash on 2008-08-28
Do you have a 'vga=' option in your /boot/grub/menu.lst file?  That can cause issues getting to the virtual terminal.

---

### Post by bcrowell on 2008-08-28
Hi all,

Thanks for the suggestions!

I think this is actually a hardware problem, not an xorg misconfiguration. I can't even successfully boot from the live CD without getting the black screen. This machine has a video card with a DVI connector, which I have to use through a converter, and I think that's probably what's causing the problem. I'm going to try swapping in another video card to see if that fixes the problem.

  Ben

---


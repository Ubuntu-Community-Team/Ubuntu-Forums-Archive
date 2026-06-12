---
title: "Monitor goes stand-by when entering the text consoles"
date: 2008-04-23
forum: Multimedia Software
---

### Post by syraxes on 2008-04-23
Hello,

Here are the facts: 
1. Ubuntu 7.10 
2. The video card is detected as "intel 915" using the
   driver "intel - experimental modesetting ..." 
   (i've left the configuration exactly as detected at install)
3. The graphical interface is working fine in 1280x1024 , 60hz
4. When pressing Ctrl+Alt+F(x)  the monitor goes black. 
   The keyborad is functional and i can type in commands "blindly".
   I also can come back to X with Ctrl+Alt+F7 .

5. With vga=0 or vga=normal   I can initially see (in text mode)
   the messages written while the different daemons are being started.
   But after Xorg starts ,  the consoles become inoperable. 

6. With vga=791/795/775/etc  I can see the splash screen. 
   But the text consoles are still black. 

7. I'm not sure whether framebuffer is working properly : 
   fbset says "/dev/fb0: No such file or directory"
   (with  vga=795 or 791)

My impression is that the cause of the problem is Xorg or 
or the video driver , that is setting a broken video mode 
when I press Ctrl+Alt+F1 . 

My question is : does anyone happen to know some trick that
might fix the video mode used when switching from Xorg to
the text console?   Preferably, I'd like to use a "real"
text mode , not framebuffer. 


Thanks,
Adrian M.

---

### Post by efe-0001 on 2008-05-03
Hi Adrian,

as You already guessed, there is a problem with the frame buffer: it is simply deactivated due to stability considerations. Must say I never had a problem with that.

How to activate (found that some time ago in another forum):

- Add a line containing "vesafb" to the file /etc/modules
- Comment out ("#") "vesafb" in the file /etc/modprobe.d/blacklist-framebuffer
- set "vga=somewhat" in /boot/grub/menu.lst.
- Reboot. 

And you should be done. 

Maybe you also want to de-activate the spash screen in /boot/grub/menu.lst ("nosplash nosilent"). I prefer to see the messages during boot and shutdown... 

On the other hand, i had hangs at shutdown/reboot because of the splash screen.

btw: what do you mean with "real text mode"? I dont know another console method than the frame buffer. OK, you can have a console via serial line on an ASCII terminal, but i think, those times have gone...

Hope it helps,

Edgar F.

---

### Post by syraxes on 2008-05-12
Edgar,

I've disabled gdm so that it is not executed automatically and
my consoles are fully functional. However, after starting Xorg
the consoles become unusable: the monitor goes to stand-by
when pressing ctrl+alt+Fn.  Also, if I stop Xorg the consoles 
remain unusable.  
So in conclusion: the xorg driver does not restore the video
mode properly . 

About what i mean by "real" text mode :  yes, i want my consoles 
to be ASCII.

---


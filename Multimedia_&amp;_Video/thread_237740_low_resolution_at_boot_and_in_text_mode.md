---
title: "low resolution at boot and in text mode"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by arvs on 2006-08-16
Somewhere in the course of trying to find a way to power off my laptop-monitor, the resolution at boot up dropped to what seems like 800x600, while it's native resolution is 1400x1050. 

I'm not sure what caused the problem, either the 'vbetool dpms' command that I tried in X or the nvidia driver that wouldn't install right. I've managed to install the driver and get my monitor to power off now, but I'm stuck with a hideous resolution at boot and in text mode. Only when the x-server starts the resolution gets back to its normal size.

Does anybody have any idea how to go about changing this back again? I have an Inspiron 8000 with a Geforce2 Go graphics card.

Thanks for any suggestions.

---

### Post by carontis on 2007-01-30
Well, I'm searching for something similar, but I can help you with this:

sudo nano /boot/grub/menu.lst and when in it, check for lines 

[I]## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda1 ro quiet splash [COLOR="Sienna"]vga=791[/COLOR]
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault 
boot[/I] 

where the last part "[COLOR="Sienna"]vga=791[/COLOR]" results the boot at 1024x768 and this can be something better for you. You'll have to apply in all rows ending with splash so the system will read it for all configurations you have (norma, safe, memtest etc). Now: as told I have the same problem 'cause now I need too to change the resolution in my booting, but I don't know what kind of number (decimal or what) I have to write in it, so I'm checking for it too...

I hope this will help you to start to fix the problem 'cause to my pc worked well.

---


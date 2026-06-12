---
title: "usplash / framebuffer issues with widescreen"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by cleric23 on 2007-09-12
Hi guys,

I just got my new computer with monitor and though I should give ubuntu a try. I have been using Debian for about 5 years before.

When I booted the LiveCD, the bootup was black. Then, gdm started and all was fine. Okay, I didnt think about it much. Then I installed the system to my hard drive and everything works great.. Sound, ethernet, video card, etc.. I am using a Nvidia GeForce 8600 GT and even the nvidia binary driver works great. I have a Samsung 226bw Widescreen Monitor with a native resolution of 1680x1050.

So, here is the problem. When I use the default kernel that came with the installation, after booting, I see the grub menu. I choose the kernel and then the screen goes blank, but the system boots. As soon as gdm starts, I see the nvidia logo from the binary driver and everything is fine.

There is no "vga=..." or "video=..." kernel parameter, just a "splash" parameter from what I think is "usplash". However, if I remove the "splash" from the menu.lst of grub, the screen does not go blank, but the framebuffer does not start either (I see the bootup, but the resolution is very low).

I started playing around with the framebuffer stuff but even without usplash, I could not get it to boot at any higher resolution (not my native one, not even anything else like 1024x768 or 800x600).

I tried adding nvidiafb, but I read that its not a good idea to use nvidiafb with the nvidia binary driver for Xorg, so I switched to vesafb, but still, it does not change the resolution.

Is this a common problem? I am not sure if it is the video card or maybe the monitor, I right now dont have another monitor to test it with.

I really would like to have 1680x1050 in the console with a nice splash.. Thanks in advance!

---

### Post by cleric23 on 2007-09-13
anyone? :(

I read a lot about blank screen while booting.. it seems to be a common problem.. doesnt anybody know a solution?

thanks

---

### Post by cleric23 on 2007-09-13
I justed removed "vesafb" from the modules blacklist in /etc/modprobe.d/ and now its all working.. Not with 1680x1050 like I wished, but with 1280x1024, which is fine..

---

### Post by nvteighen on 2007-09-13
A thought: my computer (a Toshiba Satellite A110) had a "fullscreen" feature at the BIOS that made anything look a bit wider than it had too, including Windows startup. I disabled it and everything looks great (but smaller). Maybe that could be related.

---


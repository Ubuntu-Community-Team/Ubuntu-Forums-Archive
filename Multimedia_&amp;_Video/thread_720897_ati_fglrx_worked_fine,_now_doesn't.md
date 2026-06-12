---
title: "ati fglrx worked fine, now doesn't"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by freestyla on 2008-03-10
Hey,

I've been using an Asus M2A-VM HDMI mobo with the fglrx drivers, of all versions, with 7.04 and 7.10 just fine using the svideo out.  Apart from the known bugs (ie video tearing), its been faultless.

Now with a new plasma, I've tried using the HDMI connection.  Using aticonfig i queried the connected monitors, and saw two connected, tv and tmds2...beautiful.  I enabled the tmds2 output and low and behold, there was an 800x600 screen on the HDMI plasma input (albeit a bit small).

Knowing this worked, i set aticonfig to force enable the tmds2 and do notv.  I unplugged, the svideo, restarted...and...I get just a black screen.  Fair enough I thought, some more tweaking is needed, so I overwrite the 'tmds2' xorg.conf with my previously backed up WORKING xorg.conf, and switched back to svideo.  Restarted, and again once after the progress splash screen, it goes to black, I hear the ubuntu start up sound, but thats it.

Going back to the vesa driver, there are no problems, both svideo and hdmi work fine, its just as soon as I enable fglrx now, no matter if its hdmi or svideo, I get a black screen.

It feels like theres some other persistent fglrx storage, other than whats in xorg.conf? I installed the latest 8.3 drivers hoping it would go from fresh, but the same problem occurs.

Any ideas? Either to fix it in one hit, or completely remove every fglrx component and persistent storage (then fresh install)?

Thanks

---

### Post by Jenxie on 2008-05-05
I'm having almost the same problem, but i don't have to go back to vesa.

A fresh install of ubuntu, dvi and hdmi to tv works flawless, but installing ati drivers (tried manual and envy) and the hdmi output stops working (bios/grub/ubuntu loading screens works) but after ubuntu loading screen goes to 100% screen goes black

The regular dvi monitor works when this happends. Trying to find a solution about this but i'm unsuccesful, btw, i have a M2A-VM HDMI to, with ATI Radeon Xpress 1250 integrated graphics.

---

### Post by Jenxie on 2008-05-05
I plugged TV with the VGA cable instead of HDMI cable for now.

Really strange that everything works with vga/dvi/hdmi before ati install but only vga/dvi after ati install.

I wan't my HTPC runnit sweet sweet HD =/

---


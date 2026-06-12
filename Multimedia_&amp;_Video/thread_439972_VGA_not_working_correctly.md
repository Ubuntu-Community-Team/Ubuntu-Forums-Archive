---
title: "VGA not working correctly"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by tomlj on 2007-05-11
Hi 

I'm new to Ubuntu and Linux in general, and am trying to get my install working and I'd appreciate any help you guys can give me.
I have an agp video card with a Cyber 9397DVD chipset (I'm using this because it's the only thing that can drive the lcd that I need to use, or I would change this, but unfortunately I'm stuck with it). I can get 7.04 (as a live cd so far) to display correctly in 'graphics safe mode' and everything looks fine. In the normal mode though it boots but there are lots of strange patterns/rubbish on the screen and windows leave strange trails etc. 

I've searched the web and come up with these three pages that I think may help. However, they don't mean a lot to me and I definitely don't know how to implement them, even if they are the solution: 

[http://www.eol.ucar.edu/homes/oncley/micron/XF86Config2](http://www.eol.ucar.edu/homes/oncley/micron/XF86Config2)

[http://bellet.info/XVideo/trident.html](http://bellet.info/XVideo/trident.html)

[http://www.sanpei.org/Laptop-X/Lapto...Notebook_CN620](http://www.sanpei.org/Laptop-X/Lapto...Notebook_CN620)

Any suggestions appreciated, I'd love to get Ubuntu up and running!

Thanks
Tom

---

### Post by spamking2000 on 2007-05-11
Yeah... I get the same with my NVidia card. Had the same problem with Freespire, Fedora and Ubuntu upon installation and for whatever reason, although my video card will support the mode, it doesn't come up looking nice... weird lines, rubbish on the screen... I know what you're talking about.

Try this:

goto /etc/X11
sudo gedit xorg.conf

under Section "screen" and DefaultDepth, change the 24 to 16, save, close, restart. That got rid of it for me... 'course I don't know about your chipset, but once I get the REAL nVidia drivers... I can bump it back up to 24 and it works just fine.

Oh jeez! Trident... WOW! How old is that? I thought they went out of business like 10 years ago! Yeah... I didn't catch that before, you may have to go down to like 8-bit.. or worse 4 in order to make that work. My last Trident card had 2 MB of RAM... great card back then on OS/2 Warp 4, but it was also limited to 16k colors in 1024x768 resolution.

Good luck!

---

### Post by tomlj on 2007-05-11
Thanks man! Yeah, I'm using some pretty old stuff here, but I've got to get it working somehow.. 

Cheers! 
Tom

---


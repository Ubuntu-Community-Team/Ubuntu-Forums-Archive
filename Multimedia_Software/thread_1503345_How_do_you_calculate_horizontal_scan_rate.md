---
title: "How do you calculate horizontal scan rate????????????"
date: 2010-06-06
forum: Multimedia Software
---

### Post by rainbowagent7 on 2010-06-06
Hey all. **I need to know how to calculate the horizontal scan rate and the vertical synchronization rate for my monitor**, It's a Dynex DX-LCDTV19. If anyone has these #s or knows how to calculate them that would be awesome. I have the manual, have looked at the manufacturer's website, on the back of the TV, and done an exhaustive Google search, but have come up with nada. I cannot get above 800x600 and have tried many, many suggestions from these forums and elsewhere, and have run out of time. School starts for me tomorrow and I need to achieve 1024x768 to meet the requirements of my blackboard system. I basically need to know these factors to properly configure an xorg.conf file. I'm going to follow the instructions on the FreeBSD Handbook on X11 Configuration @ [http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html) because after reading the man pages to Xserver, Xorg, and xorg.conf, not to mention countless hours of research in these forums and on the web, I've come to the conclusion that Lucid can still use xorg.conf, it just doesn't to make room for the new auto detection features. Anyway, all I need is to obtain these #s so I can get crackin', I still don't know all the commands but am getting very acquainted with Ubuntu and can obtain any info someone may need to help me. Thanks in advance, rock on!


:guitar:

---

### Post by tgalati4 on 2010-06-06
Most lcd's are 60 Hz, some are 55 or 50 Hz for the vertical refresh.  So, open a terminal:

tgalati4@tpad-Gloria7 ~ $ gtf 800 600 60

  # 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
  Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync


tgalati4@tpad-Gloria7 ~ $ gtf 1024 768 60

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync


Try different refresh rates (60, 55, 50) with your desired resolution and cut and paste the modelines in the appropriate place in your xorg.conf.  That would be in Section "Screen".

man gtf

To learn more about the command.

---

### Post by rainbowagent7 on 2010-06-06
Thanks for the quick reply. Does it matter that my display has a 16:10 aspect ratio? Also, what's the difference between cvt and gtf? It's not really important, just wanted to add it to my memory bank.

---

### Post by tgalati4 on 2010-06-06
I was not aware of the cvt command.  VESA is an older video standard.  It's now a fail-safe video mode that most video cards support.  For a custom aspect ratio (non-4 by 3) and non-standard pixel resolution you would need a custom modeline in your xorg.conf.  

Try generating modelines with both and compare.  Try them all and post the one that works.  It's tedious, but sometimes linux requires that to drive your hardware.

---

### Post by rainbowagent7 on 2010-06-07
Understood. I'll be up all night on this one, and I'll be sure and post my results. Thanks for your time!

---

### Post by tgalati4 on 2010-06-07
Also realize that TV's are TV's first and not really PC monitors.  So the supported, maximum resolution may only be 1024x768 at 60 Hz.  It's the VGA rendering engine (also called the scaler) that determines what resolutions you can use on your TV.  I prefer Samsung's because they have better scalers and often you can address the full resolution of the screen.  I have a 23" that my powerbook can drive the full (1920x1080p) resolution.

If you have a DVI port or HDMI, use that to get higher resolutions.  VGA tends to be limited to 1600x1200.  But do post the results to help others with a similar display.

---

### Post by rainbowagent7 on 2010-06-10
I'm back. Sorry it's been so long, but between school and this video issue I've been swamped. I've tried tons of things to resolve this including adding modelines with xrandr using the cvt and gtf commands, tweaking my new xorg.conf file (which by the way Lucid does read from it once it is created, and here's a link how to make one: [http://ubuntuforums.org/showthread.php?p=9431354#post9431354](http://ubuntuforums.org/showthread.php?p=9431354#post9431354) ) in pretty much every way logical, and many, many other things. As it turns out I came across some info about my chipset ( SIS630 ) and apparently there are some major compatibility issues with it. So I finally decided to switch back to Hardy Heron and now everything works great. If you right click on "Applications" then click "Edit Menus" then "other" from the list on the left then "screens and graphics" and close out, you will have "screens and graphics" in the applications menu, click it and from there you have tons of options to custom pick your video card driver, screen resolution, and monitor type. What makes it really neat is you can test it before you choose those options (if you hit test and a grey grid pattern appears with the mouse you're ok). Be forewarned this is a little finnicky and you may have to do it a few times before it accepts your settings, but once it's done that's all she wrote. I am now running with the r128 driver and a widescreen resolution of 1280x768, which is fine with me until I get a new system in the fall. Hope this helps someone, this thread is solved!:p

---


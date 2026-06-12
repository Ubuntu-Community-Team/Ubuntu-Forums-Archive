---
title: "Screen Position Problem"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by ekard14 on 2006-09-12
Hello all,

I have a minor, but annoying problem. I have a dual boot (XP/Ubuntu) system. When I switch from XP to Ubunutu, my screen is shifted about 30 pixels to the right, so the far right side gets cut off and there is some black space on the left. The auto adjust on my monitor fixes the problem, but when I switch back to windows, the screen is shifted too far to the left and I have to use auto adjust again.

I have my monitor connect via VGA and I read on another thread that using DVI might fix this problem, but I'd like to keep my DVI open so I can hook up my laptop.

Like I said, it's not a huge problem, but if anyone has a solution, it would be greatly appreciated.

Not sure if it's of any consequence by my graphics card is an ATI X300 SE 128MB.

Thanks.

---

### Post by jgbiggs on 2007-10-19
My problem is even more severe.

I have a 20" dell widescreen lcd, that I share with vista over a KVM switch.  I tried to install 7.10 last night to the second pc, and the screen position is shifted 3" to the right.

So much over that the lcd controls will not push it over enough, and when I try to use xvidtune to create a custom modeline, it errors out stating that my settings are out of the monitors range.  (even when i try to move the image just 1 pixel over)

Any ideas?

---

### Post by richardhsu on 2007-11-10
I am having the same problem (use both Windows XP and Ubuntu 7.10).

My monitor : Dell E228WFP (22" Widescreen whose optimal resolution is 1680 x 1050 at 60 Hz)
Details: [http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-5205](http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=320-5205)

My graphics: NVIDIA GeForce 6150 (motherboard GPU)
Details: [http://www.nvidia.com/page/gpu_mobo_features.html](http://www.nvidia.com/page/gpu_mobo_features.html)

Using the 'auto-adjust' option in the monitor works but I have to do it everytime I switch. I can live with this but would like it to be resolved.

---

### Post by HydrantHunter on 2007-11-10
Same problem here.  Toshiba Portege 3500 Tablet Notebook.  Trident (?) CyberBlade (of some sort) 32MB video.  12"-13" TFT screen.

I'm gonna dig around in the configs and see if there are any offset or other adjustment values I can toy with.  If I have any success I'll post back...otherwise I'll be quietly lurking, :popcorn: hoping someone has the answer (or an update fixes it).

---

### Post by carlinuxlearner on 2007-11-10
@ jgbiggs
Do you have Ubuntu set to use a wide screen resolution? And make sure the aspect ratio is set to the correct one (16:9), this might fix your problem.

C@RL

---

### Post by carlinuxlearner on 2007-11-10
@ ekard14 + @ richardhsu
Do you have your graphics driver installed on Ubuntu? If you have it installed on windows and not on Ubuntu that will happen.

C@RL

---

### Post by HydrantHunter on 2007-11-11
Well I reviewed the man entry for xorg.conf and found that there are horizontal and vertical 'skew' options.  Unfortunatley the section required to use them can't use just the skew entries - it requires pixel clock entries (according to the man doc).  So I skipped that.

I tried editing the xorg.conf manually to set my display to LCD (not realizing there was a 'Screen and Graphics' tool in Preferences), and at the same time tried to define the external VGA output (yeah, I know - one thing at a time...my bad).  I restarted X (ctrl-alt-backspace) and ended up in failsafe mode which threw me to the 'Screen and Graphics' app.  I set it up appropriately (LCD screen, CyberBlade video, 1024x768, secondary disabled) and X ended up being stuck in PnP Display mode with 800x600 max res and generic display driver...although the picture was now perfectly centered. :mad:

The xorg.conf file was configured to start X in failsafe mode, so I replaced the xorg.conf with a backup of my working config and still couldn't get out of PnP/generic mode.  Played around with the 'Screen and Graphics' app and finally got it take after about 5 or so tries.  It seemed to finally take when I deleted /etc/X11/xorg.conf~

Sadly, now my Wacom tablet stylus isn't working (I had it working before messing with trying to shift the screen, just couldn't get screen rotation to work).  The only entries I changed were in xorg.conf and I'm using the copy that worked before I started this charade so I have no clue why that's broken now - guh.  :confused:

It seems that the entries in xorg.conf and the settings in 'Screen and Graphics' aren't a 1:1 match.  So I'm not sure, at this point, exactly what is happening (and where) during the display set up and initialization (since both the conf file and the S&G app seem to affect the GUI).

I'm going back to getting my stylus working, then I'll take another stab at shifting the desktop over a bit.  I'll poke around the Hardware Info and other stuff to see if I can get my pixel clock and other required settings for the section in xorg.conf so I can mess with the skew settings.

One question regarding the 16:9 issue - does 4:3 have to be explicitly stated somewhere or is it implied by the 1024x768 resolution.  My guess is it's implied and thus this isn't related to my issue.

Update: This thread ([http://ubuntuforums.org/showthread.php?t=594356](http://ubuntuforums.org/showthread.php?t=594356)) seems to describe a similar issue.  Apparently it was resolved by installing restricted drivers.  Unfortunately the restricted drivers manager says my system doesn't need any restricted drivers so I'm going to continue with my blind groping for the time being.

Update2:  At some point a second monitor definition was added to my xorg.conf as well as modeline entries for the display (according to man they are compact versions of the Mode section).  The modeline entries had the pixelclock, etc. entries so I tried adding the hskew entry to the end (using both 0 and 10 as values - throwing in negative values seems to send X into failsafe mode).  There seemed to be no effect on my machine, although the man entry did mention that not all drivers use hskew (and kind of implied that they would already be there if they were used).

At this point I'm out of ideas...if anyone else has any other suggestions or solutions that worked for them I'm all ears (and nose, and fur, and...).  The video drivers for my Portege apparently don't work with RandR or much else, so I doubt my experiences are representative of what most others are dealing with - so if any of this works for you please post back...it would be nice to think all this time spent wasn't just to find another 2000 ways how NOT to make a lightbulb.

---

### Post by axiomata on 2007-11-17
> **carlinuxlearner said:**
> @ ekard14 + @ richardhsu
Do you have your graphics driver installed on Ubuntu? If you have it installed on windows and not on Ubuntu that will happen.

C@RL

Enabling the proprietary ATI driver in Ubuntu fixed it for me instantly upon reboot.  Thanks.

---


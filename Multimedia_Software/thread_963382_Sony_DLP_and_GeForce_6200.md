---
title: "Sony DLP and GeForce 6200?"
date: 2008-10-30
forum: Multimedia Software
---

### Post by wizard10000 on 2008-10-30
Hi, forum  :)

I just moved my media server downstairs and am having a heck of a time getting the thing working with my 50" DLP set - at either 1920x1080i or 1080p the screen's bigger than the TV is and I had to remote into the box with kdrc to adjust the width of the top panel so I could get to Gnome menus at all.

Anyway, here's the hardware list.

TV = Sony KDS-50A2020 50" DLP set.

Video = Nvidia GF6200 over HDMI.  On this set if I go in the VGA port I get 1360x768 - that's the best the TV will do.  If I use the s-video port best I can do is 1024x768.

OS = Intrepid  :)

I'm *not* running mythtv on this box.

Anyway, xvidtune complains about the modeline being out of spec if I try to make *any* adjustments.

I'm at the office and the TV is at home so I can't post an xorg.conf but X autodetected the TV and configurated itself for 1920x1080p @ 60Hz just like it was supposed to - but as I said the picture's about an inch bigger than the TV on all four sides.

Anybody got any ideas - or better yet, a working config?

thanks muchly -

---

### Post by wizard10000 on 2008-11-03
I never did get a working modeline or a custom resolution and have pretty good search skills.

I ended up wiping the drive, installing Windows XP and the current Nvidia drivers and had a custom resolution set up less than five minutes after the driver install.  Nvidia's windows drivers even detected the fact that I was connected to a TV and gave me this cool utility where all I had to do was move a horizontal and vertical slider to get the desktop to fit the screen.

I heart Linux but I needed for this to work.  

Nvidia, are you listening?  Your Linux utilites are nowhere near as advanced as your Windows utilities.  It's a shame because I really wanted to keep Linux on the media server.

:(

---


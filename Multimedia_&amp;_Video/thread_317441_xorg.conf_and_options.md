---
title: "xorg.conf and options"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by tkman on 2006-12-12
I'm very confused over something with xorg.  From what I gathered all your settings for the gui environment are configured in xorg.conf.  For example you set your resolution, power management, color depth, and etc all in the xorg.conf file.

I had everything working pretty ok until I installed some game on my system.  I blew up my xwindows environment.  I started to mess with my xorg.conf file and I discovered a few weird things.  I started over with a basic xorg.conf file, but my monitor still respected my previous power management settings by turning off after 5 mins.  But there is no "Offtime" "5" in the xorg.conf, how is this happening?  Is there another file that really controls things?  Maybe there are 2 layers?](*,)  It appears to me that maybe there is another config file that loads setting after the settings in the xorg.conf file are loaded.

---

### Post by tkjacobsen on 2006-12-12
xorg.conf doesn't control power-management.. Go to system -> preferences -> power management

---

### Post by n_hendrick on 2006-12-12
you might want to

---

### Post by n_hendrick on 2006-12-12
umgh....excuse me....you might want to uncomment the dpms option in the monitor section.

---

### Post by tkman on 2006-12-12
After having a little time to experiment I have narrowed things down to one line in my xorg.conf file

  Option "Metamodes" "1280x1024,1280x1024"

As long as I keep this option to just one choice I'm ok. I used to have:

  Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"

When it was like this it would shut the second monitor down right after I logged in.  This all started right after I installed the 3D game trigger.
Any suggestions?

---


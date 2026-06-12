---
title: "ATI Radeon HD support + 40 inch Samsung"
date: 2010-02-03
forum: Multimedia Software
---

### Post by jekristiansen on 2010-02-03
Hi!

I'm new in here.
I have this little problem because it looks like there's no overall support for my HD HIS ATI Radeon 5750 card, and only 95% of my 40 inch Samsung's screen are beeing used...
I don't really know so much about Linux, but i allways manage somehow.
But in this case, there is a note on bottom right that says "AMD Unsupported hardware"
Does anyone know what i can do to solve this problem?
I can't even start XBMC mediacenter...:confused:

---

### Post by NetDruggie on 2010-02-13
Greetings, I also have a Radeon 5750 with a 40" HDTV. 

 System - Preferences - ATI Catalyst Control Center (Administrative)
Display Manager - DTV(1) - Adjustments - Scaling Options - Overscan: (0%) [Move the bar all the way to the right]

---
If you scale with your HDTV instead of this way - you will experience horizontal and vertical pixel boxes all over your screen
---

Also, on another note I don't know if you have enabled Compiz 3D (extra effects) but if you have you might notice that everything LAGS.  This is how you fix it:
 
Open a terminal and type “gstreamer-properties”. Press Enter. o Click the Video tab.
 o Under Default Video Plugin select “X Window System (No Xv)”.
 o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
 o Click Close


-- 


Note: you Need to have the Proprietary Drivers installed prior to all this:
visit ATI's website (which is down for maintenance atm otherwise I would give you more details) and search for your model number and Linux OS Drivers.  You will then sh drivername_x_x_x.run --listpkg

then you will sh drivername_x_x_x.run --buildpkg Ubuntu/karmic

then just navigate to the directory where the debians (.deb) were created and run them all.  You will then sudo aticonfig --initial -f

then sudo aticonfig --input=/etc/X11/xorg.conf --tls=1 
then fglrxinfo

shutdown -r now

(should be good to go)

I recommend VLC for your video playback, however since these drivers arent opensource and you will experience tearing of the video (horizontal lines when there are a lot of frames per second)

Maybe one day AMD will get their heads out of their butts and release opensource drivers for their ATI GPUs like Nvidia did.

If any of these instructions were misleading or confusing I apologize and here are some reference URLs: 

[http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by SeanFromIT on 2010-06-09
I have this same problem, but the Scaling Options slider is grayed out no matter what options I choose. Any ideas?

---

### Post by NetDruggie on 2010-06-09
Are you running the catalyst control center administratively? "Ati catalyst control center (administrative)

---

### Post by SeanFromIT on 2010-06-09
Yes, and I type my password correctly ;-)

---


---
title: "Resolution Issues"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by crocco on 2006-07-10
I just installed Ubuntu 6.06, and spent a lot of time trying to get my resolution set.  It was a pain, and everytime I ran sudo dpkg-reconfigure -phigh xserver-xorg, it still would only show the three lowest resolution options via the ubuntu gui.  Then I read one thread that solved the problem.  I just wanted to post a howto so others with this issue could find an answer more quickly...so here it is:

1. From command line:  sudo dpkg-reconfigure -phigh xserver-xorg
2. Go through the menus and just accept everything as is autodetected
3. when you get to the page that lets you put a '*' to select the reolutions you want to have as options ONLY SELECT THE HIGHEST REOLUTION YOU WANT, AND DESELECT ALL OTHERS! (BTW, you toggle these on and off with your space bar)
4. Reboot, and you will see all resolutions, from the highest you selected down to the lowest available as options (even though you did not select them).  

Hope this saves you some time. :KS

---

### Post by txdmb on 2006-07-10
I did that, but I didn't get to any screen where I could input resolution. Instead this popped up...

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060710192932

I'm on a Samsung 920N (19 inch LCD analog monitor), geforce 6100 onboard graphics. I'm trying to bring the resolution from 76hz to 60. 

Do you know what I need to do? Install nvidia drivers? Thanks for any help.

---

### Post by it_self on 2006-07-11
It sounds like you misconfigured xserver-xorg. If you backed up xorg.conf, try activating that one and working things out from there. If you didn't, I recommend going ahead and installing the nvidia drivers (sudo apt-get install nvidia-glx), running 'nvidia-xconfig,' and when that fails, give one more shot at 'dpkg-reconfigure -phigh xerver-xorg.'

---

### Post by tseliot on 2006-07-11
> **txdmb said:**
> I did that, but I didn't get to any screen where I could input resolution. Instead this popped up...

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060710192932

I'm on a Samsung 920N (19 inch LCD analog monitor), geforce 6100 onboard graphics. I'm trying to bring the resolution from 76hz to 60. 

Do you know what I need to do? Install nvidia drivers? Thanks for any help.

Install the Nvidia driver (follow my guide)

Then try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by Max Roswell on 2006-07-11
> **crocco said:**
> I just installed Ubuntu 6.06, and spent a lot of time trying to get my resolution set.  It was a pain, and everytime I ran sudo dpkg-reconfigure -phigh xserver-xorg, it still would only show the three lowest resolution options via the ubuntu gui.  Then I read one thread that solved the problem.  I just wanted to post a howto so others with this issue could find an answer more quickly...so here it is:

1. From command line:  sudo dpkg-reconfigure -phigh xserver-xorg
2. Go through the menus and just accept everything as is autodetected
3. when you get to the page that lets you put a '*' to select the reolutions you want to have as options ONLY SELECT THE HIGHEST REOLUTION YOU WANT, AND DESELECT ALL OTHERS! (BTW, you toggle these on and off with your space bar)
4. Reboot, and you will see all resolutions, from the highest you selected down to the lowest available as options (even though you did not select them).  

Hope this saves you some time. :KS

Fixed my problem like a charm.  Nicely done.  Thanks!

---

### Post by benduenga on 2006-07-11
I was following this thread in an effort to set up my own screen.  After following the left instructions the refresh rate is 60 hz(desired from 76), but the screen resolution in the drop down screeen reads 1024x780.  

This seems to be at odds with my xorg.conf whose section "screen" reads 1280x1024.

---

### Post by Baladahn on 2006-07-11
I too am having refresh rate issues.  I, however, am using a Mitsubishi Diamond Pro 2070sb and am attempting to do 1600x1200x100hz (the monitor specs state it can do 109hz at that resolution) and I've used this resolution in Windows.  I can only get it to do 85hz in Ubuntu, however, and have tried using Modeline as well as inserting the HorizSync and VertRefresh parameters into "Monitor".  Does anyone have any experience with this monitor or know what could be holding it back? The windows driver allows 100hz with the newest monitor drivers; with older drivers you would have to display refresh rates that were not "supported" to select it ( at 1600x1200 ).

---


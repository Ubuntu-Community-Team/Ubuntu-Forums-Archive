---
title: "FIXED: Intel i810 video &amp; ViewSonic VG1930WM widescreen"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by TonyS on 2007-05-11
Hi all,

I impulsively bought a widescreen LCD for one of my staff without considering the possible pain in making her low powered Intel i810 (82845G/GL) graphics (and feisty) talk to it...

It really was a hassle, but I've solved it and thought someone, somewhere, sometime might benefit from knowing how.

Just a wee note first that the "915resolution" solution described in the "FixVideoResolutionHowto" on the wiki did NOT work. After fiddling for ages I got the mode installed and the GUI would come up OK, but the display was corrupt, with the left edge missing in action off the edge of the window, the top inch or so blank and the right hand side two inches peculiarly munted. Hopeless.

OK, here's what solved it for me...

If (like me) you've already broken X at this point and are staring at a blank screen you need to reboot (I had to use the power button hold-for-5-seconds trick), hit "escape" at the first mention of Grub on reboot, and choose to boot in Safe Mode. This boots to a command prompt. Scary for many for sure, but its not TOO painful from here, so stay brave.

First, install the newer Intel drivers. I'm not sure why these aren't installed by default, sure should be. I think you'll need Universe enabled:-

sudo apt-get install xserver-xorg-video-intel


It asks if you want to replace the old drivers. Yep, you sure do.

Then run the xserver video autodetect thingy:-

sudo dpkg-reconfigure xserver-xorg


Choose all the autodetected and default settings it offers, with these exceptions:

1. At one point it asks about allocating system memory to the video card, making specific mention of the the i810. I'm not sure if it made any difference, but I set this to 64000 KB.

2. When it lists the resolutions you want enabled MAKE SURE your monitors native solution (in my case 1440 x 900) is checked.

Now you must reboot. You can do this by typing (wait for it...) "reboot". Nice.

This time let it boot as normal. With any luck it'll pop back up beautifully. In my case it came up 1024x768, so I went to System | Preferences | Screen Resolution and chose 1440x900, which worked perfectly.

Beautiful! I very much wish I'd known all this five hours ago, but with any luck its saved you from that fate!

Cheers all,

Tony

---

### Post by jlanaway on 2007-05-11
THANKS!!!

You fixed my problem with this guide...  :KS

---


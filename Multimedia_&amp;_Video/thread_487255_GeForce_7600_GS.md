---
title: "GeForce 7600 GS"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by dondizzle on 2007-06-28
My resolution during boot and load is 1024x768 but after i type in my login and password, the resolution switches to 800x600 and when i goto change the resolution, 640x480 and 800x600 is all thats available. I added the following line to my xorg.conf 
# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 

But now i can switch it back to 1024x768 on the list but only at 50hz after i log in. So it seems that modeline only added 1024@50hz.  Any help would be appreciated.

---

### Post by dabl on 2007-06-29
What driver are you using?

If you're not afraid of a little re-install task after Ubuntu kernel upgrades, I recommend using the Envy script installer to get the latest Nvidia proprietary driver.  Read the installation instructions, download Envy and install it, then if it happens not to run in GUI mode (like it doesn't for me), you just open a console window and type ```
sudo envy -t 
```and it runs great in text mode and installs the driver, and restarts the x server for you.

Here's where you get it:  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the latest version which is envy_0.9.5-0ubuntu5_all.deb

:popcorn:

P.S. it requires some package to run, and you might need to install them first.  Here are the ones that I was missing:


fakeroot
python-glade2
python-qt3
dh-make

---


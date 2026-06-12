---
title: "Nvidia and Ubuntu - At my wit's end!"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by jackpetrilli on 2007-12-06
Okay, I've spent about 6 hours on this already and I finally have to ask for help...

I installed Ubuntu 7.10 on my laptop a few weeks ago and liked it enough to decide to put it on my desktop in a triple-boot arrangement (Vista, XP, and Ubuntu).

Everything installed okay until I logged out to activate my latest graphics changes, as instructed to do by the OS.  I then get a blank screen with a "sync. out of range" message.  I can then only get to the terminal (with a reboot).  I have then tried adding the myriad "Option etc. etc." flags (that I researched online) to my xorg.cong, without any successful result.  (the new lines are there but they don't help.)

I have re-installed the OS 3 times, with the exact same result.  I've been forced to do this, as I can't get back into gnome to change my driver, etc.  I've tried installing WITH the proprietary Nvidia drivers and WITHOUT, all with the same result.  The last time, I installed all updates, and even downloaded the ENVY package, all to no avail.  I still only have access to my 1280x1000 gnome desktop until I logout or reboot.  (I've even completely destroyed the Linux partitions before re-installing to make sure ubuntu wasn't reading an old graphics driver.) 

I'm at my wit's end.  I really want to make this my main desktop system but I've run into this iron wall.

Right now I'm considering over-writing my xorg.conf with the one that comes on when you boot to the liveCD.  Should I do this?

One other thing, I've been using Screens and Graphics to try and activate my 2nd monitor (which just flashes on and off like a neon sign when gnome first comes on.)  Should I avoid using this control (especially when using the Nvidia proprietary driver)?

I have a Nvidia 5600 built into an Asus P4P800 motherboard.  1.5 g ram.  Samsung 1st monitor and Viewsonic 2nd, both flat-screen.  Both can accept 1280x1000 at 60mz.

ANY help would be greatly appreciated...

- Jack

---

### Post by prodigalson666 on 2007-12-06
@ the start up choose safe mod kernal, when its done loading alot of of info it will put you at a command line, type  "sudo dpkg-reconfigure xserver-xorg". After a few steps you would be able to configure the resolution of you monitor...
After that, run "sudo /etc/init.d/gdm restart"

This happens to me every time I do a clean install and install my nvidia drivers and reboot, this solution though works every time.

---

### Post by jackpetrilli on 2007-12-06
> **prodigalson666 said:**
> @ the start up choose safe mod kernal, when its done loading alot of of info it will put you at a command line, type  "sudo dpkg-reconfigure xserver-xorg". After a few steps you would be able to configure the resolution of you monitor...
After that, run "sudo /etc/init.d/gdm restart"

This happens to me every time I do a clean install and install my nvidia drivers and reboot, this solution though works every time.

Thanks a bunch.  This at least got me back into gnome.  Should I even attempt to activate my 2nd monitor?

- Jack

---

### Post by prodigalson666 on 2007-12-06
Thats out of my realm of knowledge, my computer is hooked up to my 42" lcd tv, so I've never tried dual monitors, sorry. Try a new thread on dual monitors if no one else answers this thread.

---

### Post by jackpetrilli on 2007-12-06
Just like to say that I was able to solve all of my problems, thanks to help from this forum.

I now have Ubuntu working on a dual-monitor system with a resolution of 1280x1000.

BTW If you have a Nvidia monitor, DO NOT USE the Screen and Graphics control under System/Administration.  That is what was screwing my system.  Follow the instructions for using TwinView instead.  (Install nvidia-settings ---> sudo nvidia-settings.)

- Jack

---


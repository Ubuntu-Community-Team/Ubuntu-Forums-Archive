---
title: "xv video output problem (black screen)"
date: 2011-09-27
forum: Multimedia Software
---

### Post by gawryl77 on 2011-09-27
hi all,

i am  trying to watch a movie with my favorite mplayer but i've got only black screen (window), since sounds works nice. After passing an extra argument to the mplayer, namely -vo x11 (or -vo vdpau) i can see the movie. 

i am sure that it's not only mplayer problem, because other software doesnt work right (still black screen on Skype (incoming video), chees (also black screen, camera works nice because i can do a photo clicking photo button in Chees!), vlc (black screen during a movie) and others). In some of those softwares i can pass additional argument (like -vo x11 in mplayer) and it helps (solve the problem). But i dont know how to do this in others apps, so i think i have to solve main problem - xv driver.

How to reinstal xv drivers? witch packages? or any other ideas? (maybe gstreamer-property? but i've tried... )

p.s.
i am running UB 10.04 with 2.6.39-3 kernel on Asus 1201n with nVidia ION

---

### Post by WasMeHere on 2011-09-30
Did you try this thread: [_[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=766683")?
It may take some time to do the tasks in the first post 'the how-to', but the result is very good, you will get a solid multimedia system.

Or you may have a general problem with the video driver. What graphics card/chip do you have? Run the following terminal command ```
sudo lshw -businfo | grep display
``` Use the output of the command to make a search string for your internet browser: *_linux_  _your video card/chip name and number_*
With good luck or hard work you will find out how your video card/chip works with linux :-)
> UB 10.04 with 2.6.39-3 kernel 11.04 natty?

---


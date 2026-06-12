---
title: "ATI Radeon 4850 HD Dual Monitor Setup need help"
date: 2009-07-15
forum: Multimedia Software
---

### Post by fwaokda on 2009-07-15
I've had this setup working correctly before but due to some unfortunate things (Computer Janitor) my drivers/settings/something got messed up.  So I attempted purging all the drivers and then reinstalling them but this time by using the "Restricted Drivers" offered by Ubuntu.  So I got those and then during the next boot up I logged in and noticed that it was running very slow. Well it appears xorg.conf was hanging at 100% on the CPU, so I did runlevel 3 and then found a site that offered these PPAs(?) and I added those to my software sources and then proceeded with the Update Manager.  After installing the updates everything appeared to be working, except that my primary monitor that is capable of supporting a resolution of 1920x1080 was only showing in "Display Preferences" a max resolution of 1650x1050 (the max resolution of the second monitor).

So, I edited my xorg.conf from this -- [http://pastebin.com/m4c48e25f](http://pastebin.com/m4c48e25f)
to this -- [http://pastebin.com/m1e49d39f](http://pastebin.com/m1e49d39f)

I then relogged and was able to see the proper 1920x1080 resolution for the primary monitor. So I switched it to that one. Well, the secondary monitor would not receive a signal so I rebooted to see if that would help. It didn't. So I pressed Alt+Ctrl+F1 then went back to X by pressing Alt+F7. This fixed the problem... except I have to do it everytime I log in.  Also the secondary monitor after doing that has a distorted set of pixels at the top of the monitor.

If anyone can please help in any way it would be greatly appreciated.

---


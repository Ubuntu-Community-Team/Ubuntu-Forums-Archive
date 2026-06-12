---
title: "nvidia 8800 + 2.6.20-16 +envy = no opengl"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by theboredone on 2007-07-01
I currently have compiz installed, although its no longer enabled. I had been using the .15 kernel, but because of some other drivers I needed I decided to start using the .16.  I figured it wouldnt be a big deal upgrading.
I installed the new headers, the new restricted modules, etc. When I booted to the new kernel, X failed cuz the driver is no longer for the right kernel. So I ran envy(before I had installed it by hand because synaptic didn't install it right) for the first time and it ran fine with no errors that I caught. 
I rebooted and everything worked except when I try and reenable compiz it doesnt crash but no titlebars and such(so I went back to metacity works fine). 
So oh well, not the end of the world. Except now quake4 wont load, and ut2k4 plays uber-slow.
Also at the top of the GL desktop(an app for managing compiz/xgl) it no longer has my vid card name, it just says Videocard1.
Q4 errors out with:
¨Fatal Error: Unable to initialize OpenGL¨

Glxgears runs, but when I run the command to see if direct rendering is enabled, it says no.

I realize theres a lot of posts here of a similar manner, but none of the solutions seem to work for me.

I recently tried reinstalling the driver manually off the nvidia site(after apt-get removing nvidia-kernel-common, and nvidia-glx-new) which just caused x to not load. 

I tried this guide:
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)
to no avail, just a dead xserver.

So I ran envy again, and Im back to not having opengl acceleration. Any help? A compiz compatible solution is preferable, if not I like fluxbox better anyway.

FYI:
Ubuntu version: Feisty
Vid Card: 8800GTX

---

### Post by Jordan777 on 2007-07-03
I'm in the same boat.  I think I'm just going to install Kubuntu or maybe just reinstall and stick with the .15 kernel.:(

---

### Post by theboredone on 2007-07-04
Come on, don't make me put windows on this comp to run games. I just killed off my last windows install. I thought I was free :(

---

### Post by topsites on 2007-07-04
There exist three (3, III) drivers for envideo.

Latest Version: 100.14.11
Latest Legacy GPU version (1.0-71xx series): 1.0-7185
Latest Legacy GPU version (1.0-96xx series): 1.0-9639

You need to figure out which is teh correkt driver for your kard.
Then, with envy from omg this sucks, how do you do envy from the commandline?
envy -g 
I think

Uninstall, re-install.

You could do what I did, which is:
Start over, install Ubuntu Dapper, upgrade to edgy, upgrade to feisty, do NOTHING else!
Get envy and get the video working RIGHT AFTER it's feistied.
Then do whatever.

Lodes of fun, the mighty Xorg who controls teh Xserver, ahhh yes.

---


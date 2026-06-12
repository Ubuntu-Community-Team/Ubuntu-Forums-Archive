---
title: ":confused:  3D Acceleration-Intel 810 &amp; 3Sfx Voodoo2"
date: 2005-12-24
forum: Multimedia &amp; Video
---

### Post by quincunx on 2005-12-24
Alrighty, here's my situation...

I'm recently returning to Linux, and hoping to stay.  I just used Ubuntu to over-write a Fedora install my friend put on my system hoping this distro would take care of my issue, but it appears to be the same.
 
I have installed Wolfenstien Enemy Territory, but it will not run since my 3D acceleration appears to not be installed.  After launching "et" I eventually get:

***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************

When I run the game with that option the opening menu is so slow it takes me 10 minutes just to exit.

I have an Intel 810 motherboard with onboard video (with AGP).  I do have an old 3D accelertor card which I think is a 3Dfx (Diamond) Voodoo2. 

I'm assuming my onboard video might be better.  Either way, I'd just like to get the game running (with framerates that were at least as good as it was on my Win98 install).

From the research I did with the last distro I had, I need to install Glide (which I don' t think I installed correctly), then download/recompile Mesa to use Glide (don't know how that's done).  After that I'm not sure if there are any other steps, since I haven't made it that far.

I just found the SynapticPM, but didn't see Glide.  There were some mesa-like files, but it looks like they're already installed.

Please Help!  There's an XP CD on my monitor that I'd love to throw away!

;)

Quincunx

---

### Post by quincunx on 2005-12-24
Also....

glxinfo returns:

-----------------------------
name of display: :0.0
display: :0  screen: 0
direct rendering: No
-----------------------------

---

### Post by shof2k on 2006-01-06
freedesktop.org has a snapshot list of updated i810 drivers.  I installed the July versions and this got direct rendering working for me (fps ~600), but be warned the December ones aren't compiling.

Hope that helps,

---


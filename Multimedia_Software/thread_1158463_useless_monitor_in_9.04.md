---
title: "useless monitor in 9.04"
date: 2009-05-13
forum: Multimedia Software
---

### Post by GWBouge on 2009-05-13
I'm running a dual-monitor setup, and since I upgraded to 9.04, it doesn't seem to be working right.  running seperate x-screen config, the programs I try to start on the left screen no long run on that screen ... all programs are now loading on the main (right) screen.  it's extra-aggrevating because I finally got around to getting my Hauppauge 1600 to work right, and it does me no good with the TV hiding behind open windows or on another workspace   =oX

_System config_:
Ubuntu 9.04 32-bit
2.6.28.12-generic
nVidia 8600 GTS
Driver Version 180.44
Seperate X-Screen configuration

need more info, just lemme know.

I've tried disabling the screen, restart, then setting it back to a seperate x-screen ... but no luck.  I'm sure I'm probably just missing something small.  any ideas?

---

### Post by GWBouge on 2009-05-14
ok, so TwinView is almost what I want.  at least is lets me use the left screen, however I don't like having my workspaces span across multiple screens ... I'd like the TV, IM's, web browser, etc, to remain on the left screen while I can have multiple projects in multiple workspaces on the right screen ... the way I had the Seperate X screen set up before 9.04.

I've tried several restarts, changing the config around (seperate, twinview, Xinerama, etc) and back again, hoping it would straighten itself out, but still no luck.  I guess I'll stick with TwinView for now unless someone has some ideas about what I might be doing wrong.

---

### Post by gefenm11 on 2009-05-17
what output you get from **xrandr**?

---

### Post by davidbessire on 2009-05-17
i've got the same problem as the original poster.  i just set up dual monitors under 9.04 as separate X screens.  Main difference in my case is that i'm using two video cards, but the behavior is the same.  Windows for applications started on the second display appear on the first display.

Only two exceptions to this behavior that i've noticed: Firefox and Google Earth, if started on the second display, will appear there as well.

@gefenm11: can you post the exact xrandr command line you'd like me to use?  Default output appears to be just a list of display modes.

-db

---

### Post by davidbessire on 2009-05-19
At the direction of the following thread:

[http://ubuntuforums.org/showthread.php?t=1137206&page=3](http://ubuntuforums.org/showthread.php?t=1137206&page=3) 

i enabled the nvidia driver version 173, but it didn't correct the problem of applications starting on the X screen 0 instead of screen 1, where i started them.  

It did, however, allow me to run the second monitor at its full resolution without display artifacts.  Previously (nvidia driver version 180) i had to run the second monitor at the same resolution as the first.

Google search ultimately led me to some bug tracker entries wherein this problem was reported by several other people and blamed on, alternately, nvidia drivers, or gnome-panel, or something.

i hope this issue is resolved before my next upgrade at 9.10; everything else is very slick and i have a clueless Windows-devotee boss at work who's been crowing about Windows dual-monitor support - "it just works."

-db

---

### Post by GWBouge on 2009-05-22
```
Screen 0: minimum 320 x 175, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      50.0* 
   1024x768       51.0     71.0     72.0     73.0     74.0     75.0  
   1440x900       52.0  
   1400x1050      53.0     54.0     55.0     56.0     57.0  
   1360x768       58.0     59.0  
   1280x1024      60.0     61.0  
   1280x960       62.0     63.0     64.0  
   1152x864       65.0     66.0     67.0     68.0     69.0     70.0  
   960x600        76.0  
   960x540        77.0  
   840x525        78.0     79.0     80.0     81.0  
   832x624        82.0  
   800x600        83.0     84.0     85.0     86.0     87.0     88.0  
   720x450        89.0  
   720x400        90.0  
   700x525        91.0     92.0  
   680x384        93.0     94.0  
   640x480        95.0     96.0     97.0     98.0     99.0    100.0  
   640x400       101.0  
   640x350       102.0  
   512x384       103.0    104.0    105.0  
   400x300       106.0  
   320x240       107.0    108.0  
   320x175       109.0 
```

yeah, just appears to be available modes, and only on the main monitor (the one the terminal is on).  i'm guessing had it loaded on the left monitor it'd just show me that ... too bad it won't start there   =o\

I did try firefox on the left monitor, and that actually loaded there as david had said, although I've never had the resolution problem.  I've always been able to run 1600x1200 on the main, and 1280x1024 on the left.

on a totally unrelated note,  the Sound Blaster X-Fi ALSA drivers I gave up on a week ago finally decided to start working sometime today, ha.  maybe that Computor Janitor doohicky I ran last night actually helped something out.  OSS4.1 worked fine in 9.04, but I'll see if I can't keep tinkering with this ALSA/SB X-Fi restricted drivers and break something again   =oD

*EDIT*
Something I had noticed before, but forgot about, which I just noticed again ...
I set it to Seperate, and set my second monitor "Left Of" my main screen ... save, restart ... but after a restart, it always shows up "Right Of" the main monitor, even though I still have to move the cursor off the left side of the main screen to get to the second one ...

---


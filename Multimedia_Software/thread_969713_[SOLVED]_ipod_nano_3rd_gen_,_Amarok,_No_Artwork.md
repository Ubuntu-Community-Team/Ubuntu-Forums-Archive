---
title: "[SOLVED] ipod nano 3rd gen , Amarok, No Artwork"
date: 2008-11-03
forum: Multimedia Software
---

### Post by castudil on 2008-11-03
Hi Guys, this is my situation:

I'm using

1.- ipod nano 3rd gen
2.- Ubuntu 8.10
3.- Amarok
4.- last.fm

situation:

1. database collection working (external HDD)
2. every album has its artwork. 
3. able to connect my ipod and transfer music.
4. last.fm working good

problem:
1. doesn't display artwork in ipod after transfer. 
2. when i connect the ipod and play song from it, the CONTEXT menu in amarok menu doesn't show info about the song being played.

a similar problem was posted here: 

[http://ubuntuforums.org/showthread.php?t=737261](http://ubuntuforums.org/showthread.php?t=737261)

but apparently no solution was found.

any input will be much appreciated!

---

### Post by castudil on 2008-11-04
ok guys, problem solved

FYI:

thispage has info about what to do

[http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working](http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working)

I followed the steps, though that the packages were already installed, but one:

GdkPixbuf has to be available (including development package) 

I do not remember the exactly name of the package but I did this:

1.- copy the "GdkPixbuf" text onto the clipboard
2.- open synaptic ... select search ...and paste the text
3.- you will see some packages called GdkPixbuf or something like that... and one of those has the text  "-devel" at the end. install it
4.- done, now after tranfering the music from amarok to my ipod i choose "Transfer artwork" or (something like that) and done

hope this info may be helpful

---


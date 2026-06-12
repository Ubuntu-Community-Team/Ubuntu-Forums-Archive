---
title: "mplayer video issues..."
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by amphibious on 2007-06-06
My girlfriend put ubuntu on her laptop, everything worked right out of the box, although I had to mess around with the 955resolution thing (or whatever the number is).  The only other issue is playing DivX/XviD/DVD files... the default media player won't play them.  I installed the version that says that it works with DVDs and it didn't work.  So I installed my preferred media player, mplayer.  It'll play DVDs just fine, but it doesn't correctly play DivX or XviD files when I open it by clicking the icon in the menu... they display as black and white with the image either greatly compressed horizontally, tiled, or just static.

However when I go to the command line and simply type "mplayer <filename>" it works just fine.  Since running it with the command line doesn't load the GUI I can't see what settings it's using to play correctly.

Anyone experienced this?  Anyone know how to fix it?

Thanks!

---

### Post by eggdeng on 2007-06-06
> the default media player won't play them
Do you mean totem-gstreamer? Totem-xine will play all of those file types, check out  'How to install DVD playback capability' at [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

> running it with the command line doesn't load the GUI
```
gmplayer
``` launches the gui.

Purists don't recommend it but Automatix2 will install players and required codecs for you.

---

### Post by amphibious on 2007-06-08
> **eggdeng said:**
> Do you mean totem-gstreamer? Totem-xine will play all of those file types.

No, I mean mplayer... I installed the totem version that supposedly supports DVDs and followed that guide and it still didn't work, so I installed mplayer because I know that works correctly... except from the menu it doesn't work.  Only when I launch it from the command line does it play correctly.

---

### Post by Bablefish on 2007-06-08
I know what some are going to say but let me tell you from experiance it aint going to work. What you need to get your player to run DVDs (I reccomend downloading from Add Remove the Kaffiene player) is a add on that gives you all the plugins and codecs you need and it's found here [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

But one thing you should know first you need to install Medibuntu first.

---

### Post by Chappy7777 on 2007-06-08
what the hang is medibuntu? Ubuntu for Doctors? I know there is a Christian version of Ubuntu which I think is just Ubuntu w/biblical software. 

Seriously, what is medibuntu and what is it for? Can it be installed thru Synaptic and/or Add-Remove?

Chappy

---

### Post by Bablefish on 2007-06-08
The best I have figured out it's where Ubuntu stores all the media codecs and plugins. To find the install instructions look for How to Enable multimedia found on this site or search for Medibuntu

---


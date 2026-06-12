---
title: "DVD playback not working"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by nflp1999 on 2007-03-01
I've tried everything to get a DVD movie to play.  I try it under Totem and I can play the intro (like the Columbia logo) then it says the content is restricted and it needs toe libcssdvd files.  I have those.  I've triple checked that.  So I tried other players.

Mplayer says :Failed to open dvd://1
VLC doesn't do anything.  I tell it go to to the DVD then I press play and it does nothing.
Xine says there is no input plugin to handle 'DVD:/' Maybe MRL syntax  is wrong or file/stream does not exist.

What am I doing wrong? :confused:   I'm running 6.10 if that matters.

---

### Post by tbroderick on 2007-03-01
Double check that you have libdvdread3, libdvdcss2 and the needed codecs for Xine. If it still doesn't work try using regionset to set the DVD region.

---

### Post by nflp1999 on 2007-03-02
I checked and I did have those packages but apparently the css one was not installed.  I'm brand new to Linux and thought once you checked the package under Synaptic it installed it.  It was checked but I went into the Terminal and installed the css that was under the /usr/share/doc/libdvdcss folder.  It seemed to do the trick...for Totem at least.
    I'm still getting the same error with Mplayer.  It's like it can't find the DVD to play.  Should I change the location of my player to get it to see it correctly?  With Totem playing now, I'm assuming the Mplayer problem is just a software setting.  Any ideas??  Thanks for the help by the way.  So far, Ubuntu is awesome with all the resources I've been able to fine.  I tried MEPIS but found that like swimming through mud trying to get everything to work.  Ubuntu seems much easier.

---


---
title: "Still no DVD playback"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by wajvpitt on 2006-12-21
I really do want to ditch windows now.  All I use it for is watching DVDs, which I do rarely.  
When I first installed Ubuntu (Dapper - 2.6.15-27-386) I installed just about everything possible in no particular order to try and get dvds working.

I have:
libdvdcss2 - version 2.6.15-27-386
w32codecs
libdvdread3

totem-xine
gstreamer
mplayer
vlc
etc etc etc. 

It still doesn't work - vlc just does nothing,
mplayer flashes a blue screen then quits.  

Have I installed things in a dodgy order?  
Have I installed too many packages?  
What can I uninstall?  
Any suggestions?  

I'd like to get this sorted...  Would I fare any better in 64 bit Edgy?  
I have an inkling that it may be something to do with my video card - Matrox Mill. G450 as it caused problems in Windows playing DVDs to begin with.

Please help - can supply more information!

---

### Post by bruenig on 2006-12-22
If it is your graphics card then this may not help. But doing this worked for me.
```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine
```

You should be able to open it in totem. Or go into vlc, open file, go to disc, and then select the device name that your disc is in.

---


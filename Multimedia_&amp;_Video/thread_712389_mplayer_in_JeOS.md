---
title: "mplayer in JeOS"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by Hendrixski on 2008-03-01
I'm toying with Ubuntu JeOS to possibly make a virtual appliance for multimedia stuff.  I installed mplayer, xorg, and every codec I could get my hands on: w32codecs, gstreamer0.10-plugins good bad and ugly sets.  Yet I still get an error when trying to play AVI files.

Because it's JeOS there's no drivers installed so I'm running mplayer -vo x11 filename ... and it works on wmv files, and some streams.  But when I try to run AVI files I get
```

Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll 
```

Now, before I would get that error with .ram files, which I could run by adding a -playlist parameter,  but these are not playlists, they're avi's.   I've even converted the files to .ogg with  ffmpeg -i file.avi file.ogg  but I still get the same error. Which is strange because I figured ogg wouldn't use those codecs.

If anybody can shed some light on this I would REALLY appreciate it.  Thanks :-)

---

### Post by thegnuguru on 2008-03-01
Do you have w32codecs installed?

---

### Post by Hendrixski on 2008-03-01
:-) Yes, I mentioned I installed those in the original post.

I would suspect that it's a driver problem (since Ubuntu JeOS doesn't ship with any drivers... and why should it, it's for virtual appliances)  except that some videos do work... the ones in the Microsoft formats, so videos *do* play in the VM using Ubuntu JeOS.  it's the AVI ones that don't.

---


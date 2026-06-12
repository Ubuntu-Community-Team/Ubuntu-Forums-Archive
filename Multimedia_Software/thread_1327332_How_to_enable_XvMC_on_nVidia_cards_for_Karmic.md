---
title: "How to enable XvMC on nVidia cards for Karmic"
date: 2009-11-15
forum: Multimedia Software
---

### Post by ticket on 2009-11-15
This is for accelerating DVD and mpeg file playback on older equipment with nVidia cards that don't support VDPAU.

Older nVidia video cards (e.g. 6*** series) don't support VDPAU but do support XVMC.  XVMC can only be used to accelerate the decoding of DVD and mpeg type streams.

In karmic, attempting to enable XVMC in mplayer produces the error ```
XvMCCreateContext failed with error 2 
```

The fix doesn't require the download of any new packages in Karmic. The ffmpeg and mplayer packages that come with Karmic are just fine.  The fix is to edit the file "XvMCConfig" found in /etc/X11   

```
gksu gedit /etc/X11/XvMCConfig
```

That file currently contains the text 
```
libXvMC.so.1
```
Replace this with 
```
libXvMCNVIDIA.so
```

Close the editor.  To test the fix, insert a DVD into your drive and in the command line type:

```
mplayer -vo xvmc -vc ffmpeg12mc dvd://1

```

:popcorn:

Would be nice if mplayer gui could be told to do this automatically when playing DVDs.

Would be interesting to see if this allows playback of HD mpeg streams on older PCs.

---

### Post by ticket on 2009-11-22
Just to report that using XvMC definitely improves mpeg playback performance.

I can now watch standard resolution DVDs with compiz enabled.  Previously, under compiz, they stuttered terribly.

(Alas, compiz is still a killer of flash playback performance).

---


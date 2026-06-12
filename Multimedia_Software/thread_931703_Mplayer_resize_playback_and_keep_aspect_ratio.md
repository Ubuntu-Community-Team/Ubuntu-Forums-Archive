---
title: "Mplayer resize playback and keep aspect ratio"
date: 2008-09-27
forum: Multimedia Software
---

### Post by jimmy the saint on 2008-09-27
When the playback window is resized, the video is stretched to fit.  THis can result is some pretty ridiculous aspect ratios.  Is there a  setting to force mplayer to maintain aspect ratio when resizing the playback window?  I have searched, but have found nothing.  Also, if it is a command line argument, how would I go about forcing the system (ubuntu) to respect that setting when opening media with mplayer?

Thanks

JTS

---

### Post by jimmy the saint on 2008-09-28
dang, so either there is no solution, no one knows about it and has seen this thread, or no one else cares about this issue!

---

### Post by cbaoth on 2009-05-21
Old thread but ...

Try using output driver 'gl' instead of e.g. 'xv'.

```

$ mkdir -p ~/.mplayer/
$ vim ~/.mplayer/config
```

Add (or change):
```

vo=gl
```

If you don't experience any other problems using the gl driver, this should prevent the aspect from changing when scaling the mplayer window.

An other solution (e.g if you want to use XV for some reason) is to set a static monitor aspect in the mplayer config.

```

monitoraspect="16:10" # wide screen display
#monitoraspect="4:3"
```

This should tell mplayer to always take the monitor's aspect ratio into account and thus preventing mplayer from stretching the video in some weird way.

You may have to recalculate the monitor aspect ratio if you use TwinView (multiple displays merged to one big display).

---


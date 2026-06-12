---
title: "Totem Not Playing back .avi/other video files"
date: 2010-07-09
forum: Multimedia Software
---

### Post by The_Pheonix_Project on 2010-07-09
Hello, I recently upgraded from Intrepid to Karmic...Prior to upgrade I could play back almost any video file with totem-mplayer and others never really worked.  Now it is playing back the file but all that the screen shows is a black screen with white white through the middle initially and then when the video starts it turns to solid white but I can still hear the movie.  I know that it isn't an issue with the files themselves because they played just fine in totem under Intrepid.  Can anyone help me diagnose and correct this problem?

---

### Post by mc4man on 2010-07-09
Well don't have karmic anymore and use nvidia here, you may want to post what your display adapter is
```
sudo lshw -C display 
```
This will also provide some info, only first dozen lines or so
(need mesa-utils installed
```
glxinfo
``` 

in the meantime maybe try setting the video out to X11 from 'Autodetect'

```
gstreamer-properties
```

Under the video tab -> Default output - plugin, choose 'X Window system (no Xv)' and see if that helps

---

### Post by santhilalsubhash on 2011-12-11
Thanks a lot. The below code worked for me.
gstreamer-properties

and
Under the video tab -> Default output - plugin, choose 'X Window system (no Xv)' and see if that helps

---


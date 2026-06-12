---
title: "convert a PAL DVD to NTSC DVD"
date: 2010-03-08
forum: Multimedia Software
---

### Post by linuxhippy on 2010-03-08
I was just given a PAL DVD that was bought in Australia and asked to burn it to a DVD that could be played in the USA on NTSC players.  I searched this and found this link:

[http://www.cromwell-intl.com/technical/pal-to-ntsc.html](http://www.cromwell-intl.com/technical/pal-to-ntsc.html)

I followed the first method with dvdauthor (dvdunathor) and ffmpeg to convert to NTSC and all went well and gave me 110 new vob files.  Unfortunately dvdauthor won't create any autostart points or menus when I did this:

dvdauthor -o newdvd -T 

dvdauthor -o newdvd -x dvdauthor.xml

I was able to get 3 VOB files in a new VIDEO-TS directory after using ffmpeg and dvdauthor but dvdauthor ended with a segmentation fault so those files may not work and there is nothing in the audio_ts directory.

So, I may have a bunch of files that don't work now and I'm not sure how to burn these to DVD to check.  Is there a single gui program that will take a pal dvd, convert it to ntsc and then burn it to a new dvd?

---


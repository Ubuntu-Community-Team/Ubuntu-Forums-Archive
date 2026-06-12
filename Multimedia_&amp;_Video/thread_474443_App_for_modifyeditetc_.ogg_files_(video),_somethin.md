---
title: "App for modify/edit/etc *.ogg files (video), something like avidemux or best for ogg?"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by hecato on 2007-06-15
I there.

Im using gtk-capturemydesktop, the output of the app is an ogg file.

**1)** I will like to insert some subtitles or something more like sound, or cut out parts of the file or any other things (aparently something like avidemux, but for  ogg will do the work)...

**2)** Also I whant to know to wwich formats after the edition is posible to convert an ogg file?

---

### Post by hecato on 2007-06-16
OK, tought I ahvent found 1 that do the direct work, aparently I have come across to use avidemux

This one will convert ogg to avi and then you can reduce the size with avidemux!!!!! for example (in avidemux open the file, select te mpeg4, configure it if necessary an then in video->filters you can resize or frop parts of the video!!!!)
> 
 mencoder out.ogg -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac mp3lame -lameopts vbr=3 -o output.avi


The following I remember that work 1 time
> 
 mencoder out.ogg -ovc lavc -lavcopts vcodec=mpeg4:vpass=2 -oac mp3lame -lameopts vbr=3 -o output.avi




In fact I havent udnerstanded what encoder, decoder, container mean... or whats combinations are good and work in Linux without much lost of graphic detail!!!!, but this work somewhat OK.

---

### Post by hecato on 2007-06-18
Hey people do you know how I can do a bash script for type some like
> 
memcoderconvert input.ogg output.avi
Instead of the whole line> 
                              mencoder out.ogg -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac mp3lame -lameopts vbr=3 -o output.avi??? that would be very great!!!!

---


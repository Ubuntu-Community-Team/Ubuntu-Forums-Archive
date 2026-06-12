---
title: "Mencoder help is needed"
date: 2009-08-16
forum: Multimedia Software
---

### Post by bushnest on 2009-08-16
With the help of [http://www.swftools.org/faq.html](http://www.swftools.org/faq.html), I cooked up this terminal command- mencoder input.avi -ffourcc FLV1 -oac mp3lame -of lavf -ovc lavc -oac mp3lame -lavcopts vcodec=flv:acodec=mp3:vbitrate=500:abitrate=56 -srate 22050 -o output.swf .  Entering that into the terminal converts an .avi file to an .swf file.  The only problem with it is that the resulting .swf file's framerate is waaaaay  too fast, much faster than the original .avi's framerate.  Could someone please help me modify that above terminal command so that the framerate of the resulting .swf matches the framerate of the original .avi file?  Any help would be appreciated.  Thank-you.

---

### Post by bushnest on 2009-08-16
Guess what!?  I figured it out!  I just added the option -fps to the terminal command so that it now says, for example: mencoder input.avi -ffourcc FLV1 -oac mp3lame -of lavf -ovc lavc -oac mp3lame -lavcopts vcodec=flv:acodec=mp3:vbitrate=500:abitrate=56 -srate 22050 -fps 25 -o output.swf .  Damn, I just loooovvvvveeeeeee Linux!!!    :P

---


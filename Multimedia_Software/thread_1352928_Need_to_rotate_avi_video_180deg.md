---
title: "Need to rotate avi video 180deg"
date: 2009-12-12
forum: Multimedia Software
---

### Post by LanceyD on 2009-12-12
I need a program to quickly edit movies. These will be .avi format and about 350mb each. Specifically, I will need to rotate the image 180 degrees and crop them into small clips. 
 
I'm on Ubuntu 9.10 and I tried a few but none seem to rotate the video. (I have to film with the camera upside down before anyone asks) 
 
So what can you recommend?  
 
Cheers  [IMG]http://www.retrobike.co.uk/forum/images/smiles/icon_biggrin.gif[/IMG]

---

### Post by lovinglinux on 2009-12-12
Avidemux. In the video options there are filters that allow you to crop, flip and make other transformations.

---

### Post by LanceyD on 2009-12-12
Great thanks looks much better than the other i tried :D

---

### Post by Jose Catre-Vandis on 2009-12-12
mencoder (part of mplayer package) can also do this. For example:

> $ mencoder -vf rotate=1 input.mpg -o output.mpg -oac copy -ovc lavc

rotate=0,1,2,3 can be used for rotatating 90 degrees clockwise,
anticlockwise, flipping 180 degrees and so on.

---

### Post by datakid on 2009-12-25
I have video from my iphone that is 180deg upside down. The mencoder option didn't seem to work - not only would none of the rotates get me a right way up pic, but the quality was terrible.

Am still struggling with Avidemux - I can't get a similar quality to the original for some reason. The sound becomes washed out and the video itself is poor quality?

---

### Post by mistypotato on 2010-07-22
I looked at all the options I could find on this site.


Ultimately, I had to go back to WinXP to rotate videos.

One of those rare (but essential) times to still have a WinXP system.

VirtualDub does it for me nicely (and it's free) in WinXP

Too bad they didnt port it to linux.

---

### Post by LanceyD on 2010-07-22
As the OP, i would say that although I could rotate the videos, they were less than satisfactory, with sound and resolution degregation .

---

### Post by FakeOutdoorsman on 2010-07-22
If you like using the command-line you can [rotate a video with ImageMagick and FFmpeg](http://ubuntuforums.org/showpost.php?p=9436397&postcount=5) as I explained in another thread.

---

### Post by Fhernd on 2011-01-20
Is there an app to accomplish that task? Thanks in advance!

---

### Post by Fhernd on 2011-01-20
Is there an app to accomplish that task? Thanks in advance!

---

### Post by FakeOutdoorsman on 2011-01-20
FFmpeg can now rotate video with the *transpose* filter. Unfortunately, as of Ubuntu Maverick Meerkat 10.04, FFmpeg from the repository lacks this filter so it must be compiled:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Example:
```
ffmpeg -i input -vf transpose=2 -vcodec libx264 -vpre medium -crf 22 -threads 0 -acodec copy output.mp4
```

More info: [FFmpeg Documentation - transpose](http://www.ffmpeg.org/ffmpeg-doc.html#SEC93)

---


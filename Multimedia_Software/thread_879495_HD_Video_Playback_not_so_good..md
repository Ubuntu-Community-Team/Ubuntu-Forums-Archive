---
title: "HD Video Playback not so good."
date: 2008-08-04
forum: Multimedia Software
---

### Post by Yarbo on 2008-08-04
This is the very last thing thats keeping windows on my hard drive.   If someone can please point me in the right direction to resolve this issue, I would be in their debt,

In Windows XP and Vista, with the proper codecs (AC3 Filter, Haali Splitter, ffdshow and xvid) I am able to playback any video I throw at my PC.  No matter the resolution or codec it plays everything back flawlessly.  

I run XP and Ubuntu on the following:

Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
2 gb of ram
NVidia GeForce 8800 GTX
Asus P5K Motherboard
On board sound

In Ubuntu, I've used subversion to download the latest mplayer trunk, and i've compiled it with the gui enabled using the documentation on the mplayer home page.

After configuring the fonts and adding a skin, I can open mplayer, and play video's.   They play fine, but if I try to resize the video, or fullscreen I get an error saying cropping and scaling is not enabled on the video output mode i've selected. 

Due to the video card I am using, the documentation says that CVIDIX is the best vo mode to use.  But when I use this mode, I get an error stating that the vo mode selected can't initialize or something.  Sorry I don't have the exact error message as i've just reformated and have yet to retry installing mplayer.

I hope I've been descriptive enough, but if more information is needed I will do my best to provide it.

Thanks!

---

### Post by ramjet_1953 on 2008-08-04
You could try adding these lines to your /etc/X11/xorg.conf file in the device section:

```
Option "VideoRam" "65536"
Option "CacheLines" "1980"
```

Don't forget that this will have to be done in sudo mode and you should back-up your xorg.conf file first.

Regards,
Roger :cool:

---

### Post by Yarbo on 2008-08-04
thanks for the suggestion, but the above had no effect what so ever.

I've compiled mplayer again since having reformated, and I added the lines mentioned above to my xorg.conf file.

When ever I try to play a video with any video output mode other then x11, I get an error that states.

Error Opening/initializing the selected video_out (-vo) device.

If ANYONE can please at least point me in the right direction on how to make CVIDIX work.  I've searched the forums and on google, and haven't found a whole lot of helpful information.

---


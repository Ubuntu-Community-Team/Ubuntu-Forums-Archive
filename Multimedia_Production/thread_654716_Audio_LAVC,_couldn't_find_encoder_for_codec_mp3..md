---
title: "Audio LAVC, couldn't find encoder for codec mp3."
date: 2007-12-31
forum: Multimedia Production
---

### Post by AJL on 2007-12-31
I am trying to reencode video to play on my blackberry pearl  and I keep getting the error.
**Audio LAVC, couldn't find encoder for codec mp3.**

I am using this script ... [http://www.blackberryforums.com/linux-users-corner/65660-vid2bb-sh-using-mencoder-create-videos.html](http://www.blackberryforums.com/linux-users-corner/65660-vid2bb-sh-using-mencoder-create-videos.html)

I have lame installed, liblame-devel, ffmpeg, mplayer...

I can't seem to get around the mp3 issue.  Any help, tips, etc would be great.

Thanks in advance, Aaron

---

### Post by Creative2 on 2008-01-02
well the problem i think it's beause 
mencoder use libmp3lame for mp3 codec name with lavc library
instead ffmpeg use mp3 for mp3 codec name 

i think you should replace somewhere libmp3lame the problem of the script is this ,,,when something change after noone,less who wrote script will fix the problem.. 
 use converIT or use Fuoco tools, 
fuoco tools
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)
convertit
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by sharper73 on 2008-02-04
You can see what codecs mencoder has installed like this:
mencoder -oac help

If you install lame you should see one like this:
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame

So just change the script to say "-oac mp3lame" instead of "-oac lavc".  Now convert your porn and watch it on your blackberry!

---


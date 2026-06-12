---
title: "Converting WTV files"
date: 2010-06-01
forum: Multimedia Software
---

### Post by grondinmf on 2010-06-01
Hello,
After years of holding off(for what idk maybe apprehension of going for something less familiar) i am finally making the switch to linux for good. i had to purchase a tv tuner as my existing ati theater 650 would not work(no a big deal) my only issue now is i have all these WTV files that i recorded with windows 7 which will not play in ubuntu at all. how can i convert these to say mkv or mpg that ubuntu/mythtv would be able to play? the few things i have tired most times leave me with no audio or bad video quality. (i tired handbrake and ffmpeg) i would like to go right from wtv to mkv or mpg without have to go to dvr-ms first since that would require more time and space. thanx for any advice on what to try.

---

### Post by FakeOutdoorsman on 2010-06-01
This appears to be a closed and proprietary format that has not yet been reverse engineered by FFmpeg.  I could not get this [WTV sample](http://w14.easy-share.com/1701207119.html) (52 MB) to decode properly with any player.  Right now you may be stuck with using Windows only tools to convert this video which is annoying because according to [Consumption of a WTV file in DirectShow](http://msdn.microsoft.com/en-us/library/cc963726.aspx), it appears that the video and audio are familiar formats, but the WTV container itself is the culprit.  This may force you to re-encode the video and audio instead of simply copying them to a new format and therefore reducing the quality.  Unfortunately, or perhaps fortunately, I don't have much experience with Windows only media formats and maybe someone else will have some more useful input.

---


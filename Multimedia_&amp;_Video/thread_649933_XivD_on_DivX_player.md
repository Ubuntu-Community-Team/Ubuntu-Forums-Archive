---
title: "XivD on DivX player"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by ahaslam on 2007-12-25
Happy holidays ;)

My dad got himself a fancy HD entertainment system, so I thought I'd encode a movie for him, unfortunately the player would not play the file. 

Here's the player: [http://www.pioneer.co.uk/uk/products/42/125/501/DVR-LX60D/index.html](http://www.pioneer.co.uk/uk/products/42/125/501/DVR-LX60D/index.html)

Here's my mencoder command:
```
mencoder matrix.mkv -vf eq2=1:1:0:1:1:0.95:1:1,scale=1280:528 -ffourcc DX50 -oac mp3lame \
-lameopts cbr:br=160:aq=5 -ovc xvid -xvidencopts pass=1:bitrate=5000:vhq=4 -o /dev/null
mencoder matrix.mkv -vf eq2=1:1:0:1:1:0.95:1:1,scale=1280:528 -ffourcc DX50 -oac mp3lame \
-lameopts cbr:br=320:aq=0 -ovc xvid -xvidencopts pass=2:bitrate=5000:vhq=4 -o matrix_720p.avi
```
Resulting in:
> VIDEO:  [DX50]  1280x528  12bpp  23.976 fps  4174.6 kbps (509.6 kbyte/s)
AUDIO: 48000 Hz, 2 ch, s16le, 320.0 kbit [mp3lib] MPEG layer-2, layer-3

Any one got an idea as to what the problem could be?

:-k
[I]
EDIT:[/I] nvm. it seems many divx players have the following limitations:
> : Maximum resolution:
720 x 480 @30fps
720 x 576 @25fps
: Maximum bitrate : 4Mbps
To reduce both br & resolution would result in sub-dvd quality...

:(

---


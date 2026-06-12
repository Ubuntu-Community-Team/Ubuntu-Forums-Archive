---
title: "mplayer full screen audio video sync way off, video lags"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-08-23
makes no diff if oss esd or alsa sound selected. I cant try xv, get nothing then,  so it is on x11.

I am talking mostly about full screen video clips from cbs  or anywhere else you might be able to use mplayer. It even lags the video in DVD playback.

sound will forge ahead, video moves so slow it will be off by about 30 seconds after a 3 minute video clip.

IF, I take it off full screen, the video will play fast forward to catch up to the sound.

---

### Post by Gremlinzzz on 2007-08-23
you could try smplayer i use it and have no problems at all.
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)

---

### Post by tseliot on 2007-08-24
do you use an ATI card?

---

### Post by kerry_s on 2007-08-24
mplayer is crap these days, try vlc
sudo apt-get install vlc

---

### Post by sdowney717 on 2007-08-24
yes it is an ATI card. 9600 with 64 mb

I would particularly like to be able to full screen some of the online news video clips. And have the sound stay in sync. If I watch a DVD( rare occurance), I can use totem or gxine.

---

### Post by tseliot on 2007-08-24
it's the fglrx driver then :-(

---

### Post by sdowney717 on 2007-08-24
might have come up with an answer. Edit /etc/mplayer/mplayer.conf and set framedrop from no to yes.  At least it seems to be keeping the a/v synced up at the slight expense of the video stream in full screen.

# Drop frames to preserve audio/video sync.
hardframedrop = yes

(for some reason, just framedrop was giving me weird looping on movie trailers)

you can try this out at this site if you are using mplayer-plugin for real streaming video.
[http://www.cbsnews.com/](http://www.cbsnews.com/)

while it is ok for online news video to drop a few frames, I would not wish to do this watching a DVD movie. So it would be totem-xine or xine or vlc which I have not tried out.

---


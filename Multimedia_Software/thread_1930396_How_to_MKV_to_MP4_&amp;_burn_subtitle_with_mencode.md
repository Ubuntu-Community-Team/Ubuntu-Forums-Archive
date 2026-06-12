---
title: "How to MKV to MP4 &amp; burn subtitle with mencoder by same input quality ?"
date: 2012-02-23
forum: Multimedia Software
---

### Post by zerround on 2012-02-23
Now
I have file .mkv (included 3 streams)

1.Video
2.Audio
3.Subtitle

I want to convert from MKV to MP4 by **Mencoder** Program with requirement on list

1.subtitle and video blend together in 1 stream
2.video same input quality
3.file target size same input too

How to write command for render this project ?

ps. Sorry for bad English

Thank you

---

### Post by zerround on 2012-02-24
Help me please

---

### Post by shantiq on 2012-02-24
well i think you have to strip your sub then add it afterwards to your new mp4 file  [check **ps** at bottom of page first]





1.   **copy mkv to mp4 [sub will not copy]**```
mencoder -oac pcm -ovc copy -o final.mp4    filename.mkv
```

2.   **strip sub**


> First, use mkvmerge to list the MKV file&#8217;s contents:

```
mkvmerge -i MovieFile.mkv
```

You&#8217;ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/***)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)

Next, use mkvextract to extract certain tracks / attachments based on the output from the above command:

```
mkvextract tracks MovieFile.mkv 1:thesubtitles.srt
  2:theaudio.mp3 3:thevideo.mp4
```   of  course here you only need to extract the sub make sure to change to the number you want

 


3.   **then finally add your sub to mp4**



 > mencoder -sub file.srt -subcp iso-8857-9 -ovc xvid -xvidencopts bitrate=1419 -[COLOR="Red"]oac copy[/COLOR] -o filewithsub.mp4 file.mp4




**this works but there might be more direct routes:KS**


[B]==========================================================

ps[/B]    maybe try this first    i tried it too but it did not copy the sub   although my test file had 2 subs    it might be worth trying if there is only one see if it copies it

```
mencoder -oac pcm -ovc copy [COLOR="DarkRed"]-sub copy[/COLOR] -o final.mp4    filename.mkv
```

---


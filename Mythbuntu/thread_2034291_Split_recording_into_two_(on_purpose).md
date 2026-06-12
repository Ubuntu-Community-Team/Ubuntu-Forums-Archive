---
title: "Split recording into two (on purpose)"
date: 2012-07-28
forum: Mythbuntu
---

### Post by Quadari on 2012-07-28
Hi All,

I'm wondering if there's a way to take an existing recording (of TV) and split it into two at an arbitrary point.  E.g.,  say I have a recording that's two hours long, I'd like to break it up into (for example) two one-hour recordings.

I ask because I sometimes have really long recordings (e.g., Olympics broadcasts) and it would be nice to break them down into smaller chunks ex-post.   I suppose I could set up the scheduler to just record the four hour broadcast in four, one-hour chunks, but that seems like a less optimal solution than being able to do it after the fact.

Thanks!
Q

---

### Post by klc5555 on 2012-07-28
1) Just about any Linux video editing software can do this. I've done similar with OpenShot. I suppose avidemux can do it --whatever you want. See articles such as: [http://helmipunya1.blogspot.com/2012/07/5-linux-video-editor-software.html](http://helmipunya1.blogspot.com/2012/07/5-linux-video-editor-software.html) and give it a go.

2) If you're transcoding to some other format that nuvexport handles, you can use that in a pinch: 
Use mythtv's internal editor to make a cutlist where the entire 2nd half of the video is cut. Nuvexport the video somewhere transcoding to some format and choose "honor cutlist".
When complete, go back to the video in mythtv's internal editor, clear the previous cutlist and make a new one where this time its the 1st half of the video that's cut. Nuvexeport again, and again with "honor cutlist". Voila, two half-videos.

3) If you prefer lossless transcode, you can also do it that way in a pinch with mythtranscode from a prompt:   
Use mythtv's internal editor to make a cutlist where the entire 2nd half of the video is cut. Run mythtranscode from a prompt: ```
mythtranscode --mpeg2 --honorcutlist -c[channel-id] -s[starttime]
```Or, if you've determined what the actual recording file is, you can substitute -i [/path/filename] for -c -s

When mythtranscode has completed, there will remain the original recording and also a file that has the name original-recording-name.mpg.tmp This .tmp file is the 1st-half recording. Move/rename it someplace safe. Go back into the mythtv editor for the recording, clear the cut list, make a new cutlist where you cut the 1st half of the recording keeping the 2nd half, and run mythtranscode again as above. This time the .mpg.tmp file will be your 2nd half recording. Rename/move it and you're done (depending on whether you want to keep the original recording and clear the cutlist for it).

Those are 3 ways that immediately spring to mind; there are likely several others. In each case, since you're ending with two videos with no metadata where you originally had one recording, the resulting half-recordings will all end up going into your mythvideo directories, of course (or wherever you keep your non-tv videos).

---

### Post by Quadari on 2012-07-28
Thanks for the ideas!   I will give them a try and report back.

:)

---

### Post by nickrout on 2012-07-28
> **klc5555 said:**
> 1) Just about any Linux video editing software can do this. I've done similar with OpenShot. I suppose avidemux can do it --whatever you want. See articles such as: [http://helmipunya1.blogspot.com/2012/07/5-linux-video-editor-software.html](http://helmipunya1.blogspot.com/2012/07/5-linux-video-editor-software.html) and give it a go.

2) If you're transcoding to some other format that nuvexport handles, you can use that in a pinch: 
Use mythtv's internal editor to make a cutlist where the entire 2nd half of the video is cut. Nuvexport the video somewhere transcoding to some format and choose "honor cutlist".
When complete, go back to the video in mythtv's internal editor, clear the previous cutlist and make a new one where this time its the 1st half of the video that's cut. Nuvexeport again, and again with "honor cutlist". Voila, two half-videos.

3) If you prefer lossless transcode, you can also do it that way in a pinch with mythtranscode from a prompt:   
Use mythtv's internal editor to make a cutlist where the entire 2nd half of the video is cut. Run mythtranscode from a prompt: ```
mythtranscode --mpeg2 --honorcutlist -c[channel-id] -s[starttime]
```Or, if you've determined what the actual recording file is, you can substitute -i [/path/filename] for -c -s

When mythtranscode has completed, there will remain the original recording and also a file that has the name original-recording-name.mpg.tmp This .tmp file is the 1st-half recording. Move/rename it someplace safe. Go back into the mythtv editor for the recording, clear the cut list, make a new cutlist where you cut the 1st half of the recording keeping the 2nd half, and run mythtranscode again as above. This time the .mpg.tmp file will be your 2nd half recording. Rename/move it and you're done (depending on whether you want to keep the original recording and clear the cutlist for it).

Those are 3 ways that immediately spring to mind; there are likely several others. In each case, since you're ending with two videos with no metadata where you originally had one recording, the resulting half-recordings will all end up going into your mythvideo directories, of course (or wherever you keep your non-tv videos).

the trouble with all this is that you end up with 2 video files but only one entry in the database for it. You could then put the files into mythvideo, and add metadata for them. 

Also the easiest way to split an mpeg ts file such as those myth creates is to use a utility like split on the command line. 

I can't see a reason for splitting a show into two parts though. It takes the same space...

---

### Post by klc5555 on 2012-07-28
In my post I mentioned that the resulting files would likely have to go into mythvideo. 

(Unless of course, he wants to try something like myth.rebuilddatabase.pl, to add the needed metadata for the extra recordings. I've used the script without problems recently in 0.24.2, but can't confirm still works in 12.04/0.25 with the upgraded MySQL 5.5.)

Split sounds like a good choice if the break can be exactly at the half or quarter points (or other regular points). Except taking into account Olympic sporting events and their irregular commercial placement, the video segments may not be exactly even nor easily placed "blind" without having the video in a viewable video editor.

I've not used split with an mpeg ts file, so I don't know: since split doesn't segment at keyframes, does it introduce audio sync errors in the second and following segments?

---

### Post by nickrout on 2012-07-28
> **klc5555 said:**
> 
 since split doesn't segment at keyframes, does it introduce audio sync errors in the second and following segments?

Doesn't matter much for a TS transmission, don't forget you start any recording at a random pont, not necessarily a keyframe.

---

### Post by klc5555 on 2012-07-29
> **nickrout said:**
> Doesn't matter much for a TS transmission, don't forget you start any recording at a random pont, not necessarily a keyframe.

Right you are --I hadn't thought of it.

Well, then, if the OP is OK with segmenting his Olympics recordings at regular intervals, split is clearly the simplest solution.

---

### Post by nickrout on 2012-07-29
A better way might be to work out what point you want to split at and then

```
mplayer --dumpstream --dumpfile firsthalf.mpg -endpos 1:10:00 originalfile.mpg
mplayer --dumpstream --dumpfile secondhalf.mpg -ss 1:10:00 originalfile.mpg
```

---

### Post by klc5555 on 2012-07-30
> **nickrout said:**
> A better way might be to work out what point you want to split at and then

```
mplayer --dumpstream --dumpfile firsthalf.mpg -endpos 1:10:00 originalfile.mpg
mplayer --dumpstream --dumpfile secondhalf.mpg -ss 1:10:00 originalfile.mpg
```

Now this appears to be the best method of all --it's simple and does everything the OP seems to need.

---

### Post by Quadari on 2012-07-30
> **nickrout said:**
> 
```
mplayer --dumpstream --dumpfile firsthalf.mpg -endpos 1:10:00 originalfile.mpg
mplayer --dumpstream --dumpfile secondhalf.mpg -ss 1:10:00 originalfile.mpg
```

This didn't quite work for me.   Am I doing something wrong?  I have a 5 hour recording (~32GB).  I tried splitting it at the four hour mark.  So I did:

```

mplayer -dumpstream -dumpfile second.mpg -ss 4:00:00 5666_20120729175700.mpg 

```

It took a little while to complete, which is fine.  But then when it completed the resultant file (second.mpg) was exactly the same size as the original file.  When I play second.mpg it appears to just be a copy of the original.  I.e., I can play it from the beginning - it doesn't start from the four hour mark.

I tried the same thing, but with the -endpos option, with the same results.

I have: MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team

---


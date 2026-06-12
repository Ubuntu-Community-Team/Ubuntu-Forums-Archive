---
title: "Cinelerra Question - What Are &quot;In&quot; and &quot;Out&quot; Points Used For?"
date: 2011-03-30
forum: Multimedia Software
---

### Post by umechanism on 2011-03-30
I've read some How-to's with Cinelerra and they all talk about using the "In" and "Out" points in the video but they never say what they are used for or why anyone would use them.  Does anyone know?  :confused:

---

### Post by wildhostile on 2011-04-04
umechanism,

"In" [ and "Out" ] points permit you to select a portion of a video (along the time) in the "Drag and drop editing mode" for the selected track(s). 

You can then add an effect to only that portion of video (or audio)... or cut it, or copy it, or paste it, or render on that portion of time etc etc.

For example: Load a video, insert in and out point, add an effect between them, render only this part by choosing "In/Out Points" as "Render range" in the render dialogue window (File -> Render).

---

### Post by no2498 on 2011-04-04
see if this helps you any


[http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html)

---

### Post by umechanism on 2011-04-06
Thanks for the links.  I think those will help me but after reading briefly, the in/out points may not be what I was looking for.  

I have a 1 hour long video that I took of a sporting event and I'm trying to grab all the highlights from the video in order to make a, "highlight real" for a friend of mine.  So I sit back and watch the video looking for a highlight.  When I see one, I write down on a sheet of paper where the highlight begins and ends on the time line.  I then have to manually highlight everything before and after the section of video I want to keep then delete it.

This is very cumbersome so I was hoping I could use in/out points or some other method of marking the beginning and ending of the segments I want to delete leaving only the good stuff.  So, if in/out points can be used in this manner, please explain how.

Thanks!

---

### Post by mcduck on 2011-04-06
> **umechanism said:**
> Thanks for the links.  I think those will help me but after reading briefly, the in/out points may not be what I was looking for.  

I have a 1 hour long video that I took of a sporting event and I'm trying to grab all the highlights from the video in order to make a, "highlight real" for a friend of mine.  So I sit back and watch the video looking for a highlight.  When I see one, I write down on a sheet of paper where the highlight begins and ends on the time line.  I then have to manually highlight everything before and after the section of video I want to keep then delete it.

This is very cumbersome so I was hoping I could use in/out points or some other method of marking the beginning and ending of the segments I want to delete leaving only the good stuff.  So, if in/out points can be used in this manner, please explain how.

Thanks!
Yes, they can be used for that. Actually such cutting of video into clips is one of the main uses for in/out points in video editing.

The thing is that you need to do pretty much the exact opposite of what you are now doing. Instead of deleting parts from the full video to get the highlight clips you want you should be selecting the clips you want and copying them into new clips.

So, when you are watching through the full video and run into a section you want to include in your highlights reel, just set it's in and out points, and then copy it into a new clip. In the end you'll have the original full-length video and all the highlights as separate clips.

---

### Post by umechanism on 2011-04-06
So I use the points to clip out what I want to keep, save those clips, then use those clips to create a new video?  That is just the opposite of what I was trying to do.

So how can I remove the points after I am through with them?  I place them but I can't seem to get rid of them.

Thanks for the help!

---

### Post by mcduck on 2011-04-06
> **umechanism said:**
> So I use the points to clip out what I want to keep, save those clips, then use those clips to create a new video?  That is just the opposite of what I was trying to do.

So how can I remove the points after I am through with them?  I place them but I can't seem to get rid of them.

Thanks for the help!

You don't need to create a new video, only clips (which are more like bookmarks for positions in your original full-length video).

Like I said, the easiest  (And most commonly used) way to do what you are trying to do is pretty much by working the opposite route of how you are now trying to do it. ;)

---

### Post by umechanism on 2011-04-09
I got it figured out.  I was trying to start with the entire raw video that I captured from tape then selectively remove the parts I didn't want leaving only the good stuff.   That is just the opposite of what I needed to do.  So now I have created the highlight video by using the in/out points to mark the beginning (in) and the end (out ) of clips.   I saved these clips then dragged them to the timeline in the order I wanted.   I repeated this process until I had all the clips I needed.  I added a audio track.  Rendered it then posted it to YouTube.  Done!



Thanks for the help.

---


---
title: "Commercial flagging and transcoding jobs runs but commercials are still in recordings"
date: 2008-11-18
forum: Mythbuntu
---

### Post by thusgaard on 2008-11-18
Hi 

My mythbuntu setup runs nicely.
I have a few things left to fix and I'm taking them one by one. 

First off. 

According to the Infocenter log my commercial flagging and transcoding jobs runs. But I still have commercials in my recordings. Is there anyway to see if the flagging is done correctly? 

Please let me know if I can post any additional information!

Kind reagrds J;-)

---

### Post by dmfrey on 2008-11-18
Commercial Flagging produces a cutlist of commercial breakpoints.  This cutlist needs to be loaded on the recording before you transcode it.  To do this, start viewing the recording, bring up the menu and select that you want to edit the recording.  Press the 'z' button on your keyboard (or look for its mapping on your remote control) and exit out of the edit view of the recording.  Now you can transcode it, but you have to be sure you tell transcode to -honorcutlist.

In my opinion, you should be able to tell the recording to load the cutlist either automatically, or from the play menu in the recordings listing.  I don't think that you should be required to play the video in order to tell it to load the cutlist.  Just my opinion, however, and it may be possible to do so elsewhere, but I haven't had the time to look :).

I hope this helps you out.

---

### Post by thusgaard on 2008-11-18
I thought that running the transcoding would remove the commercials, once they were flagged. I agree, there has to be a way to load the cutlist and run transcoding automatically!

J;-)

---

### Post by Caps18 on 2008-11-21
My system doesn't remove the commercials, but then again maybe I don't have that setup the best way.

Right now, if I watch something that has been recorded, it will automatically skip the commercials, but if I fast forward during the normal TV show, it will continue to just fast forward through the commercials.

Less than 1 a month, it gets the wrong spot and I have to rewind to watch the part of TV show that was mistakenly clipped off, so I'm kind of glad it doesn't totally remove it I guess.

---


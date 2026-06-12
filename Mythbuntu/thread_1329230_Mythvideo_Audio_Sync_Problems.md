---
title: "Mythvideo Audio Sync Problems"
date: 2009-11-17
forum: Mythbuntu
---

### Post by uncle hammy on 2009-11-17
I have just started having an issue Mythvideo since one of the last 2 or 3 daily build updates.  All (and I mean all) my videos the video runs almost like it's at 1.5 speed, and the audio is WAY behind.  The audio will then run at warp speed from time to time because the video is running so fast that it doesn't have time to get it all in. The issue is ONLY MythVideo....TV (live or recorded) is unaffected.

All I have to do to fix it is MENU>ADJUST TIME STRETCH and move it off of 1X and then back to 1X. Once I do that, it back to normal.

I haven't made any playback setting changes in eons, so I doubt that's what has introduced the issue.  However, I have tried toggling OpenGLVSync, Extra Audio Buffering, Use Audio As Timebase, Audio Upmixing, etc.

Just to add into the mix, the issue is only present on my remote front end.  My backend/frontend (where the files would be local) seems unaffected.

---

### Post by uncle hammy on 2009-11-17
I also forgot to add another issue I have noticed with MythVideo.  One of the things I tried was changing Playback profiles.  Any profile I tried that wasn't a VDPAU profile (ie CPU++) won't play videos.  All I get is a black screen, and a message "Must change your video renderer" when I finally 'esc' to exit the black screen.  These profiles all work fine with TV (recorded and live).

---

### Post by williammanda on 2009-11-17
> **uncle hammy said:**
> I have just started having an issue Mythvideo since one of the last 2 or 3 daily build updates.  All (and I mean all) my videos the video runs almost like it's at 1.5 speed, and the audio is WAY behind.  The audio will then run at warp speed from time to time because the video is running so fast that it doesn't have time to get it all in. The issue is ONLY MythVideo....TV (live or recorded) is unaffected.

All I have to do to fix it is MENU>ADJUST TIME STRETCH and move it off of 1X and then back to 1X. Once I do that, it back to normal.

I haven't made any playback setting changes in eons, so I doubt that's what has introduced the issue.  However, I have tried toggling OpenGLVSync, Extra Audio Buffering, Use Audio As Timebase, Audio Upmixing, etc.

Just to add into the mix, the issue is only present on my remote front end.  My backend/frontend (where the files would be local) seems unaffected.

I'm having a similar problem. When I ripped an iso of a video today the audio was leading the video on playback. I used the adjust time stretch to get the audio & video in sync. But what was interesting was that I could play the video perfectly on a windows computer running xbmc via a samba connection to my master backend.

---

### Post by uncle hammy on 2009-11-17
Yes, they all play just fine for me using anything but Myth.  VLC, etc, no problems.

Like I say, even in Myth, they'll play fine.  I just have to adjust the time stretch off of 1x and then put it back to 1x.

---

### Post by uncle hammy on 2009-11-17
Another tidbit.  Of all my rips, I have 2 that were ripped using the MythTV DVD Ripper, so they are a single .vob file.  They are NOT affected by this issue.

It only seems to be affecting my VIDEO_TS and ISO rips.  I am not using storage groups.

---

### Post by uncle hammy on 2009-11-17
I am fairly certain this is the same problem as mentioned here

[http://ubuntuforums.org/showthread.php?t=1308222&highlight=iso+audio+sync](http://ubuntuforums.org/showthread.php?t=1308222&highlight=iso+audio+sync)

---

### Post by uncle hammy on 2009-11-19
There is apparently a patch posted for this issue here [http://svn.mythtv.org/trac/ticket/7067](http://svn.mythtv.org/trac/ticket/7067)

My questions are....

1.  How would one actually do anything with this patch?
2.  Will this eventually make it's way into the daily builds?

Thanks,
Scott

---

### Post by larsolav on 2009-12-03
In the ticket page accessible via Uncle Hammy's link above, the last post says this: 
> (In [22947]) Refs #7067. Patch from Davin McCall?. It should resolve dvd playback issues and not affect live tv playback. patch tested by other users. **will commit to 0.22 fixes in a week or 2 if no further issues are reported. **
Does that mean that in one or two weeks I can update MythTV (0.22 in 9.10) and the fixes will be applied? If so, do I do that update like the other 9.10 updates (a yellow triangle with an "!" appears on the upper right corner of the desktop)?

---

### Post by &lt;mike&gt; on 2009-12-20
<bump>

I'm also having this problem, which started after upgrading from jaunty to karmic (and from version 0.21 of myth to 0.22). 

I'd also be **very** keen to know how to apply the patch. Anyone??

btw: I found out that if I ff ('>' on the keyboard) and then pause and play (both ctrl+p on the keyboard) then this also fixes the sync, just like adjusting the playback stretch.

---

### Post by larsolav on 2009-12-31
> **uncle hammy said:**
> There is apparently a patch posted for this issue here [http://svn.mythtv.org/trac/ticket/7067](http://svn.mythtv.org/trac/ticket/7067)

My questions are....

1.  How would one actually do anything with this patch?
2.  Will this eventually make it's way into the daily builds?

Thanks,
Scott

According to [http://svn.mythtv.org/trac/log/branches/release-0-22-fixes/](http://svn.mythtv.org/trac/log/branches/release-0-22-fixes/) the patch referenced above was committed to 0.22 fixes 9 days ago. How do I see if this patch has been applied to my system or not? And if it hasn't does a regular update (by clicking the update notice symbol on the top right of the Ubuntu desktop) apply the patch? I am not quite sure I understand what is meant by "fixes" and "trunk" etc and how it all applies to my Mythbuntu setup....

Happy New Year everyone!

---


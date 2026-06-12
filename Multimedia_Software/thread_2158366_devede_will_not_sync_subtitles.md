---
title: "devede will not sync subtitles"
date: 2013-06-28
forum: Multimedia Software
---

### Post by nkbatsi on 2013-06-28
I' ve been ripping movies with devede for along time in order to make them play on a home DVD-player, it was just fine. But lately with no obvious reason devede has started to have problems in synchronising subtitles with the movie. 
I almost always use .AVI movies combined wity .SRT subtitles
Subtitles start a few seconds before they should  in each and every movie. Note that I always try the synchronization in VLC before ripping any movie and they work fine there.
Is there anybody that ever had this problem before to help me, please!

---

### Post by mtu on 2013-07-15
I also had the same problem. I had been using devede for over a year  before upgrading to version 3.23 and then this problem started. 
It's  almost like there is a drift between the subs and the audio. At the  beginning of playback there is only a slight time difference but
then this quickly grows to something like 5 minutes after two hours of playback.
Like you, the subs work just fine for me on VLC.

The  reason for this is Frames Per Second (FPS) and the encoding standard  used (whether PAL or NTSC). In my experience, the reason
for the  out-of-syncness is when the video files are encoded in NTSC (24 FPS) and  DeVeDe re-encodes them to PAL (25 FPS). I think the
subtitles count times using frames so the final result is that playback is faster for the subs than for the video.

**A possible fix**:
   Before telling DeVeDe to proceed with generating the DVD, select the title with the troublesome video file.

   Click on the video file of interest under ***Files*** then click on the ***Properties*** button to display the ***File Properties*** window.

   If under ***File info*** it says "Frames per second: 24", then go ***Video Format*** right below it and click on the radio buttons
   to change the Video Format selection from ***PAL/SECAM*** to ***NTSC***.

   Click ***OK*** and you're good to go. But just to be sure you can always use the ***Preview*** button under the ***File*** section to
   check if the subtitles and video are now in sync.
 
This worked for me so I hope it works for you too.

---

### Post by mhm770 on 2013-10-14
i have the same problem . any help ?

---


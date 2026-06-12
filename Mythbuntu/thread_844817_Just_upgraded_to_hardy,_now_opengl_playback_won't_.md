---
title: "Just upgraded to hardy, now opengl playback won't work in myth"
date: 2008-06-29
forum: Mythbuntu
---

### Post by McQuaid on 2008-06-29
This box was previously gutsy running .20.  Then I used the mythbuntu reps and upgraded to .21.  Just recently I finally got around to upgrading to hardy and now using the .21 packages provided in hardy's reps.

The majority of the time, video playback (whether recordings or video) will fail if I use opengl playback.

I changed it to xv and now all videos work everytime.

With opengl I see this error a lot:

Timed out waiting for free video buffer

and
AddAudioData():p1: Audio buffer overflow, audio data lost!

What will happen with opengl selected, the video will start up as I can hear the audio, just no video.

My card is a nvidia 6200, using the provided binaries in the ubuntu repositories.

I use opengl playback in mplayer and haven't noticed any issues, but haven't used it much yet so I'll test opengl video playback in other apps more.

I also tried the updates available from updates but same thing.


***********
A little update, I found it is a nvidia issue from what I understand, and it still exists in ver 173 of the nvidia drivers.

It's discussed here:

[http://www.nvnews.net/vbulletin/showthread.php?t=111308](http://www.nvnews.net/vbulletin/showthread.php?t=111308)

It seems to be some issue with GLX1.3 api/calls.  Glx2 works fine.  Someone on that thread supplied a patch to get myth to use glx2 as a workaround.  Don't really feel like compiling myth from src right now, but it's an option for others dealing with this.

As I mentioned, I have a nvidia 6200.  I'm thinking on settling with the nvidia-glx ver 96.43, cause given the age of my card, I don't think I'm getting much benefit off using the latest.

*************

I went to 96.43 and the problem is gone.  Not sure what regressions are due to using the older driver, but afaik, it's fine for older hardware.

---


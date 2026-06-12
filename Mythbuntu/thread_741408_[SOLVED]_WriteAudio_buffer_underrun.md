---
title: "[SOLVED] WriteAudio: buffer underrun"
date: 2008-03-31
forum: Mythbuntu
---

### Post by a_posse_ad_esse on 2008-03-31
I upgraded to Mythbuntu Hardy (prematurely I admit), and am having playback problems for recorded programs.  The video looks fine when in the "preview" box when the recording is selected, but when it goes to full screen, the audio plays normally, but the video itself is only displayed as a few frames here and there.

/var/log/mythtv/mythfrontend.log shows the message WriteAudio: buffer underrun.  I assume that this is at least related to the problem.  I have the additional audio buffer option enabled, but would this be detracting from the video buffers?

Any suggestions would be appreciated.  Thank you.

---

### Post by foxbuntu on 2008-04-01
check "top" from the terminal with video playing

```
top
```

Check CPU % and see if it at or near 100%, if so you probably need to change you playback deinterlace settings (0.21 is more CPU intensive by default than 0.20.2 was) and when you upgraded to 8.04 from 7.10 Mythbuntu you got 0.21 MythTV as well.

---

### Post by a_posse_ad_esse on 2008-04-01
Wow.  All of the settings (CPU++, CPU--, Normal, Slim) give about the same result, with one or both of the processors at 80% or above at any given time.  Are there any other settings that can be turned down?

---

### Post by a_posse_ad_esse on 2008-04-02
I was thinking that this might have been a kernel issue (misallocation of resources?) but the results are the same with the new 2.6.24-14-server release.

---

### Post by superm1 on 2008-04-03
Make sure you have the proper video drivers installed and functional.  If you are on an AMD graphics card, make sure the video overlay is turned on.

---

### Post by a_posse_ad_esse on 2008-04-03
It is a fglrx card, and adding the line to the video card section in /etc/X11/xorg.conf 

```

Option "VideoOverlay" "on"

```

and rebooting fixed the issue.  The video looks better than ever.

Thanks

---


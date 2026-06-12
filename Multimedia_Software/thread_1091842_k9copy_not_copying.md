---
title: "k9copy not copying?"
date: 2009-03-09
forum: Multimedia Software
---

### Post by FraggedLocust on 2009-03-09
I open a DVD to back up with k9copy, and select the titles i wish to copy in ISO format. The preparation window with the preview runs fine, but once the burning window appears, the animation starts, and continues to just play over. No spinning of the drive, and no processor working light.

I guess sometimes the best solution is to wait.

Still waiting...now it's sitting at 99% and the timer isn't moving.

---

### Post by mc4man on 2009-03-10
Haven't used k9 in a long time, though it tended to do that occasionally in the past (99%)

You could first go ck. and see if your .iso is any good, may be fine.

Otherwise k9 will create a video_ts in /tmp/'username'-kde/dvd. 
You could go retrieve it there, copy to home or somewhere and use something else to create an .iso (or use something else for .iso creation accessing at /tmp/..... location.
As soon as k9 starts the 'burning' process you can abort and retrieve the video_ts or use other app to create .iso

The video_ts will remain till you start k9 on another project.

Keeping the above in mind you need a min. of 9Gb free before using k9 (4.3 for both /tmp and .iso and some overhead

Edit: or as I remember you can just have k9 output to file (video_ts folder) if it continues to be unable to create an .iso

---


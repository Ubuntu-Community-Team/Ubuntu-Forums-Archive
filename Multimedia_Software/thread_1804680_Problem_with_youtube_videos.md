---
title: "Problem with youtube videos"
date: 2011-07-15
forum: Multimedia Software
---

### Post by Karthik1985 on 2011-07-15
I have been downloading youtube videos by copying the open stream through 
lsof | grep -i flash.

I have noticed a change in youtube. While watching cracle videos on youtube, lsof does not show any open streams. I thought this might be due to the fact that cracle videos doesnt use flash, I manually searched through all files in /proc/ for any open linked files.  But I am still unable to find the stream. 

I then tried to download using youtube-dl. This is the output 
[youtube] Setting language
[youtube] 61cfjfFPRuc: Downloading video webpage
[youtube] 61cfjfFPRuc: Downloading video info webpage
[youtube] 61cfjfFPRuc: Extracting video information
[youtube] RTMP download detected
[download] Destination: 61cfjfFPRuc.flv
[rtmpdump] 0 bytes
ERROR: rtmpdump exited with code 1

youtube-dl -version
2011.01.30


Is there a workaround this situation? 
I am using Ubuntu 11.04

---


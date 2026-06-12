---
title: "gPodder gives I/O: Connection refused error while downloading videos"
date: 2010-04-15
forum: Multimedia Software
---

### Post by shredder12 on 2010-04-15
Hi everyone,

I recently installed gPodder in karmic using Thomas' PPA. Although it can easily download the podcast list and update it, it gives this weird error while downloading videos.

```
Failed: I/O Error: Connection refused: None
```

Take a look at the attached screenshot.

I am using a proxy server to access the web. And the environment variables are set correctly. Actually thats why gPodder is able to download the podcast lists. But somehow it gives this I/O error while downloading the videos. The gPodder version I am using is 2.4.

Any suggestions?

---

### Post by shredder12 on 2010-04-16
Well, I guess the youtube feeds I was using didn't have any direct media link. So, it was not possible for gPodder to download the videos. But apparently the issue persists. When I subscribed to a valid feed (with media links) 

like this [URL="http://www.defcon.org/podcast/defcon-17-video.rss"]http://www.defcon.org/podcast/defcon-17-video.rss
[/URL]
gPodder successfully downloaded the list and identified the media but wasn't able to download the video and gave this error
```
Failed: I/O Error: (111, connection refused):None
```
I don't know what does this error means but (I am just guessing) could that be due to my university's firewall, if gPodder tries to directly connect to the server instead of the proxy or tries to use a port that is banned.

I am really confused here. Please help..

---

### Post by shredder12 on 2010-04-16
Ha.. there seems to be something wrong with those media links in defcon 17 feeds, they are https, so either something is wrong on the server side or my campus proxy server doesn't handle https protocol very well. 
Anyway I tried cnn daily podcasts with regular http links and they worked like charm. gPodder rocks.. :D

---


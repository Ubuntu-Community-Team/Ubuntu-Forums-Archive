---
title: "flv to xvid audio sync problems"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by douga on 2006-08-06
Hi:

I'm trying to encode flv to xvid for my particular mobile device (Zen Vision:M). While I can get it encoded, I have a problem with the audio syncing up on some clips. I use mencoder with this command line:

mencoder calsun.flv -vf scale=320:240,harddup -ovc lavc -lavcopts vcodec=msmpeg4 -oac mp3lame -o calsun.avi

Can anyone point out what I'm doing wrong? Thanks.

Doug

---


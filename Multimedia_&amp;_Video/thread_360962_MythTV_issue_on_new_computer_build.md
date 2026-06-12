---
title: "MythTV issue on new computer build"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by theanswriz42 on 2007-02-13
I'm trying to configure MythTV and after following the steps over at [http://www.djlosch.com/article_How-to%3A_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150](http://www.djlosch.com/article_How-to%3A_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150),  the mythtvfrontend segfaults when I try to access the program guide and when I try to watch tv, the app tells me that it is already set to watch/record a show (though it's not). Here's the output for restarting the backend which I think has a lot to do with the problem.

[http://pastebin.ca/354482](http://pastebin.ca/354482)

---

### Post by NeoFax on 2007-02-13
Please provide answers to the following questions, so I can help:

1. Post the output to the following:  dmesg | grep Initialized

2. Can you see any channel by doing mplayer /dev/video0?

3. Re-run mythtv-setup and add your video cards at step 3 and do steps 4 & 5 as well in the mythtv-setup program.

Thanks!

---

### Post by theanswriz42 on 2007-02-14
Thanks for the reply. I actually got everything working so far besides mythweb hopefully I'll get that one figured out.

Cheers

---


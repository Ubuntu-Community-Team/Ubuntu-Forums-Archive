---
title: "DVD Problems"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by guitarthrasher on 2008-04-14
I am having some SERIOUS trouble with playing DVDs. 

I'm pretty sure I've installed everything for the DVD playback (all the libdvd stuff) but still cannot get it to work.

I get these messages from the programs.

Totem-
"There is no plugin to handle this movie."

Gxine
"No demuxer found - stream format not recognized."


Any help will be highly appreciated.

---

### Post by roach-hunter on 2008-04-14
Three months ago, I tried to install Ubuntu and had a horrible time with getting some AVIs, DVDs, and web videos to play. After installing everything I could find and still not being able to play back DVD and other video, I gave up.

A week or so ago, I decided to give it one more try after reading some posts on this forum, and now EVERYTHING plays. I am sure there are different ways to skin a cat, but these are the steps I took to get things working:

1. install (or reinstall) Ubuntu 7.10

2. If you have a movie in AVI format, try to play it in mplayer. You will get a message that the video cannot be played back and Ubuntu will offer to go out and look for codecs. Let Ubuntu do this. After a few minutes, Ubuntu will come back with 3-4 codecs. One of the codecs will have a 4-star rating and the other ones will have 1 or 2 or 3. Go ahead and install ALL the codecs that Ubuntu finds, even though they may have just 1 or 2 stars. One of these low-star codecs is one that is necessary for the videos to play, but Ubuntu for some reason will not let you install it by itself when you attempt to install it from the install/remove programs.

3. After installing ALL the codecs that Ubuntu finds, restart Ubuntu

4. Install the GXINE backend for DVD playback

5. Install the latest libdvdcss2.x.x.deb package for your system (386/64?) from [http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)

6. All DVDs as well as AVIs and web videos should now play

Hope this helps....

---

### Post by guitarthrasher on 2008-04-14
I still get nothing. 

I can play AVI's though. I have Family Guy playing right now. 

Any other suggestions?

---

### Post by aquaxbat on 2008-04-15
I play any sort of media file except DVD playback. I get all the same errors where it says there is no playback or codec issues. I have done the same as well, gotten as many players/codecs as possible. I have recently installed Hardy on here and was having no problems before. I understand it's still beta but I should be able to get it to work.

Is there anything that I can do?? I don't think reinstalling is going to work here since this is a fresh copy as of last week.

Gonna bug my brother tonight and see if he can help me. If i get things figured out i'll post a reply here.

Thanks

---


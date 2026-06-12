---
title: "Video Playback: Pixilated &amp; Tears"
date: 2008-08-14
forum: Multimedia Software
---

### Post by ksomething on 2008-08-14
OS: Ubuntu 32bit 8.04
System: MacBook Pro 2.16Ghz 128meg ATI X1600 2 Gig RAM

Problem: When I play back video, typically XVID .avi's, in any media player the video is pixilated and image tears (vertical sync not correct). 

Pixilation occurs especially around defined shapes such as peoples faces or bodies. Playing the same video file in OSX or Windows gives no such problems - beautiful quality.

Screenshot (1440x900) [http://i34.tinypic.com/ohlt1h.png](http://i34.tinypic.com/ohlt1h.png) - Be sure to Zoom to the right resolution to see the noticeable pixilation. 

This kind of problem happens in Windows when there is no video acceleration.

How can I fix this? I want to view movies on my laptop.

Thank you

---

### Post by alexvorn2 on 2008-08-14
Maybe this is the quality of the video.
I don't see anything bad in this!:popcorn:

---

### Post by cyberdork33 on 2008-08-14
if you have compiz / desktop effects turned on, try turning them off... There are known issues with video + ATI Proprietary drivers + Compiz.

---

### Post by ksomething on 2008-08-15
Thanks cyberdork. It helped but i had to install MPlayer and change codecs to get rid of the pixilation:

Mplayer > Preferences > Video > GL2 (OpenGL Multi-textured)

Then to help fix the vertical sync I opened the Catalyst Control Centre and under 3D and More Settings I swtiched Vertical Refresh to always on. Dunno if this step helped, will hope it does. Definitely fixed the pixilation though thank god.

---

### Post by overdrank on 2008-08-15
Moved :)

---


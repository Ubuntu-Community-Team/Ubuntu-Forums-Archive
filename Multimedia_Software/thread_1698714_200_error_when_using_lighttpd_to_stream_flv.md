---
title: "200 error when using lighttpd to stream flv"
date: 2011-03-02
forum: Multimedia Software
---

### Post by csolit on 2011-03-02
We are trying to setup a video server using Ubuntu 10.10, lighttpd, flowplayer (basically the way it is setup in the link below).
 
[http://www.howtoforge.com/build-your-own-video-community-with-lighttpd-and-flowplayer-ubuntu-9.10-p2](http://www.howtoforge.com/build-your-own-video-community-with-lighttpd-and-flowplayer-ubuntu-9.10-p2)
 
We are able to stream the video fine from while the flv file is located in the /var/videos/flv folder. We have a second volume that we formatted and mounted as /media/data/videos/flv. We have changed the path in the lighttpd config file to match this. When we play the video we are receiving:
 
200, Stream not found, NetStream.Play.StreamNotFound, clip" "[Clip]"/media/data/videos/flv/test.flv"
 
Any ideas?

---

### Post by csolit on 2011-03-03
I turned out to be a permissions error on the 2nd volume.

---


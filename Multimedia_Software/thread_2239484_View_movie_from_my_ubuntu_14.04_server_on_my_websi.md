---
title: "View movie from my ubuntu 14.04 server on my website"
date: 2014-08-14
forum: Multimedia Software
---

### Post by joakimr2 on 2014-08-14
Hi there! 

Since I am new in this area so I would like some advice =) 

What do I need to do to set up my ubuntu server so I can link my movies, which is located in a folder on my server, to my wordpress website? 

That is, when you're on my website, one should just push the film's link so it plays from my server. 

If the description is unclear, so feel free to ask as I'm very new in this field. 

Thanks in advance! 

MVH Joakim

---

### Post by TheFu on 2014-08-14
Video playback over the web is non-trival and special setup is needed for the HTML and the files must be encoded so that the player can handle the codecs for both the video and audio.

For most people in a home environment, doing this is not what they want. There is an easy-to-install solution called **Plex Server** (in the software center).  For years I used XBMC, but almost a year ago, I switched to Plex.  Wish I would have changed 3 yrs ago. It has a web interface that will tell the server to transcode the videos as necessary for the different playback devices - browser, android, smart-TVs, Bluray players, whatever.  There is NO NEED to signup for any Plex account for this to work.  The web interface is really slick.  The server is also a DLNA server, so any DLNA client and Renderer can be usedm (Roku, Chromecast, etc.)

Of course, if you want to develop your own web video playback server - the learning curve will be steep - check out HTML5's "video" tag and use mp4 containers with h.264/aac encodings. Those are the most standard in the world these days, though there isn't any guaranty that any specific web browser will support any video at all.

---

### Post by joakimr2 on 2014-08-15
Thanks for your response! 
My thought is that I will be able to link these videos to my website, where I want to be able to share these videos with everyone who visits my page and what I have gathered is that this wont work using plex? 

Should not it be possible to just "add media" in WordPress from my server through URL?

---

### Post by TheFu on 2014-08-16
So ... plex is not a good choice for this - sorry.
We don't use php programs on the internet - due to security concerns, sorry. Downloading a video file is different from streaming a video file - plus there are huge bandwidth requirements that most people don't understand clearly.

Streaming video is very different from just making a file available. There are optimizations for the server-side that are needed. For small videos, apache can probably be made to work with HTML5 and a larger buffer, but most people just embed youtube or vimeo playback into their websites to handle that extra complexity.

BTW - I wanted to do the same thing you do, but refused to have mp4 containers (I prefer mkv) and did some research "video streaming server" was the google term. Very eye opening.

---


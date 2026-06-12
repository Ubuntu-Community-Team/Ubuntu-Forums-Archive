---
title: "How do I configure mplayer play streaming videos?"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by kris2pe on 2006-07-12
I find playing videos in the website [www.gametrailers.com](www.gametrailers.com) difficult bcoz I can't play the quicktime vids.
Alot of ppl say I should use mplayer to handle quicktime streams. 
How do I configure mplayer to play quicktime streams?
I find also that playing totem-xine annoying bcoz it pops-up another window just to play the video. 
How do make the player xine play streamed videos on one window?

---

### Post by Paerez on 2006-07-12
use EasyUbuntu to get all the codecs in place:
easyubuntu.freecontrib.org/

---

### Post by kris2pe on 2006-07-12
I've already done that but xine crashed whenever I want to play quicktime videos & the stream the videos from [www.gametrailers.com](www.gametrailers.com)
PLs someone answer my quesitions

---

### Post by Paerez on 2006-07-12
hmm I can watch quicktime in mplayer. Install the firefox mplayer plugin package in synaptic (just search for firefox, I don't remember the exact name). It will tell you you have to uninstall the xine plugin, if its installed, and then firefox will use mplayer when you restart it.

---

### Post by kris2pe on 2006-07-12
Is it the firefox gstream plugin? 
Coz it did uninstall gstream xine plugin!!!
But it still plays in xine pls b specific!!!

---

### Post by Paerez on 2006-07-12
sorry I was at work so I couldn't be specific. Actually there isn't an mplayer plugin, I use totem-gstreamer-firefox-plugin.

---

### Post by kris2pe on 2006-07-12
I did install that totem-gstreamer-firefox-plugin. Problem is that its still plays on Xine & still crashes when playing streamed quicktime videos.

---

### Post by Ipsissimus on 2006-11-16
The only way I could get streaming videos to play from ALL internet sites was to use mplayer. 

Just run Synaptic and install 'mplayer' and 'mozilla-mplayer'.  I did this but still had problems playing streaming videos. Then I noticed the 'totem-mozilla' package was installed for some reason. I removed this a perfect video, even from sites that wouldn't play on my XP partition :)

For out-of-browser videos I prefer Xine, for firefox Mplayer plays all.

-- Ipsissimus

---


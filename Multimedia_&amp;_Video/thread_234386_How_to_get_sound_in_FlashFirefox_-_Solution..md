---
title: "How to get sound in Flash/Firefox - Solution."
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by orasis on 2006-08-11
If you are having trouble with sound in firefox, when trying to watch a google or youtube video - this is the solution to the problem. 

As for Opera, I am not sure - but I bet you it is somewhat similar (Maybe the forum, should make a special section of proved solutions as a repository? :) 

sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=&#8221;aoss&#8221;

---


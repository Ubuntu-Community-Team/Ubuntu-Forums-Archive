---
title: "mencoder flv to avi audio-video sync issue"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by ananke on 2007-12-30
Hi everyone,
I'm trying to convert .flv videos to .avi using comand line mencoder under Ubuntu Dapper AMD64. The comand line I use is 

mencoder file.flv -ovc lavc -oac lavc -o file.avi 

but I'm having audio-video sync truble: video runs faster as if its speed is setted to 2x. Am I missing some settings? May this depende on the fvl video codec? I say that because mplayer is unbale to open flv video streams, a static white screen is returned. Audio is good but Mplayer starts and freeses playing flv videos and I have to use force quit in order to terminate it. 
Anyone can please tell me how to fix this. 
Thanks a lot.

---

### Post by srmantis on 2007-12-30
try:
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 fileinput.flv -o fileoutput.avi

---

### Post by ananke on 2007-12-31
I tried using the comand you wrote but it said that Mplayer is not compiled with mp3lame. So I used the same settings you reccomended with lavcopts but i had the same result. Is it the lack of mp3lame lib or something else?
Thanks

---

### Post by srmantis on 2007-12-31
the mencoder use the codec from mplayer, you need to install mplayer and your codecs to mp3. Play a song (mp3) on media player and the mplayer will install the codec.

---


---
title: "Video player that supports 1,5x speed playback with working audio"
date: 2008-07-16
forum: Multimedia Software
---

### Post by Zarok on 2008-07-16
Greetings

I know this has to be one of the most random questions and features people need, but I'm trying to hunt for a video player software, that supports faster than 1x playback without messing up audio.

Most players either have NO audio when playback is at faster speeds, or the audio sounds like Alvin&Chipmunks. I'm looking for a player that speeds up the video and audio, without it losing sync or making the audio sound utterly messed up. PowerDVD in Windows can do this, and I'm seriously missing that feature. I even tried getting PowerDVD to work under Wine, but I had no luck with that. If someone can help me with that , that works too. :P

I know this is a very random feature to look for on a video player, but I love the ability of speeding up stuff like mixed martial arts shows between fights, not having to miss any of the between-fight interviews etc, but saving time while doing it. So if anyone can recommend me one, I'd appreciate it very very much.

---

### Post by nycste on 2008-07-16
this is a good question, look foward to an answer or some feedback since i havent tried doing so but it would be cool to know

---

### Post by briwood on 2009-04-14
I'm looking for the same thing.  I was inspired by this post:  [http://joshua.schachter.org/2008/11/overclocking-lecture.html](http://joshua.schachter.org/2008/11/overclocking-lecture.html) Which describes Perian, a MacOS X app that can do this.

I've read that this might be in a future release of VLC.  Currently when I use "play faster" (the little double arrow button) in VLC I loose the audio.

I looked into re-encoding the audio using ffmpeg. Here's strategy.  I was hoping for something easier. [http://archives.free.net.ph/message/20080701.205926.55a3c289.es.html](http://archives.free.net.ph/message/20080701.205926.55a3c289.es.html)

---

### Post by briwood on 2009-04-14
Might try the newest version of vlc first: [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

[http://ubuntuforums.org/showpost.php?p=4279163&postcount=3](http://ubuntuforums.org/showpost.php?p=4279163&postcount=3)

[http://article.gmane.org/gmane.comp.video.ffmpeg.user/13920](http://article.gmane.org/gmane.comp.video.ffmpeg.user/13920)

[http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/](http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/)

---

### Post by andrew.46 on 2009-04-14
Hi briwood,

If you get yourself a copy of the svn MPlayer you will be able to do this using the syntax:

```
mplayer -af scaletempo -speed 1.5 myfile.mp4
```

When using this filter (without additional options) it is possible to increase and decrease playback speed *while the clip is playing* using the '[' and ']' keys and audio pitch and synchrony is maintained.

If you are interested there is a guide for Hardy Heron [here]("http://ubuntuforums.org/showthread.php?t=558538").

Andrew

---


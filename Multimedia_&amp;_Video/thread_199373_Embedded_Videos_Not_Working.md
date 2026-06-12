---
title: "Embedded Videos Not Working"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by Permafrost91 on 2006-06-18
I have trouble watching embedded videos such as those at fifaworldcup.com ... I can only see them using the mplayer-plugin and I have to set the cachesize to 50 and cache-percent to 1 to be able to see about 80 or 90% of a video before mplayer loads the next video on the list without finishing the first one I selected. When I increase the previous cache variables the amount I get to see goes down so I have the feeling this might be related to a session timeout with the site? Can anyone help me with this? It's annoying not being able to watch all 2:28 minutes of a good soccer game when I wasn't able to watch it live to begin with. 

I don't know of any other sites with embedded videos so I can't test this anywhere else but I will if you point me to another site.

---

### Post by jazzmuzik on 2006-06-18
I hope somebody can help you, but video is a real nasty choke point currently with somebody's fist around the collective neck of Linux users.

---

### Post by holomorph on 2006-06-19
yea, major frustration.  Anyone manage to get these highlight clips to work?  I've had success playing other embeded media, but the fifaworldcup site seems to be particularly badly implemented.  I even had trouble getting them to play in windows, unless I used Internet Explorer.  I'm surprised you managed to get at least part of the clip to play.

---

### Post by Permafrost91 on 2006-06-19
well, like I said ... I can only view them if I reduce my cache to almost nothing. Here's my mplayerplug-in.conf:

```
vo=x11
cachesize=50
cache-percent=1
dload-dir=/home/felboe
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
rtsp-use-tcp=1
```

does this improve your viewing experience too? perhaps I'm just having a load of luck ...

---

### Post by jazzmuzik on 2006-06-19
I'm using mplayerplug-in and Firefox and they play fine for me. I don't know if the videos are cutting off too soon. How would I know? It looks like about 15 seconds of highlights and then some drums, then that repeats a bunch of times with different highlights.

Are you using the high speed video drivers? If not that can help a lot of situations where latency is a problem. I use the noembed option also and my video is in its own window. That allows me to 'f' to make it full screen. No problems that I can tell.

noembed=1
cachesize=1024
enable-mpeg=0
enable-mp3=0

---

### Post by Permafrost91 on 2006-06-19
Thank you jazzmuzik for your suggestions. The noembed option is cool, I like that. But it still doesn't help me. The videos at fifaworldcup.com are 2:28 minutes long and I don't get to see all of those before the next video already loads.

---

### Post by holomorph on 2006-06-19
well, I got stuff working w/ the mediaPlayer Conectivity plugin, problem with that is it was trying to use gmplayer, which was somehow busted (now is fixed)  but then i installed the mplayer plugin and those don't always get along great;  Anyway, I have it working w/ the mplayer plugin now too, only it cuts out early like you said.  Except I think I found a trick for getting it to do the whole thing.  I watched the highlights, it cuts out early, and goes on to the next, but then i hit the little back arrow, and I think it went all the way through the second time; not positive though.

---

### Post by Permafrost91 on 2006-06-19
What's the mediaPlayer connectivity plugin? And, rather unfortunately, doing the back and forward buttons did not help. This is really frustrating ...

---

### Post by holomorph on 2006-06-19
[https://addons.mozilla.org/search.php?q=media&app=firefox](https://addons.mozilla.org/search.php?q=media&app=firefox)

hmm, cept it's still a hassle.  Wierd thing is, it doesn't detect the embeded media *unless* you have the mozilla-mplayer plugin installed, and then it seems that they both want to play it, so the video is choppy.  so if I click play on the mediaplayer conectivity window, so it opens a gmplayer window with the clip, and then click the little 'x' in the upper right of the mediaplayer conectivity box to close it, the mozilla-mplayer is revealed, so I can right click-> stop. and then play the video in gmplayer.  

hopefully I can figure out how to tweak it so the mozilla-mplayer plugin doesn't auto-play by default. . .

---


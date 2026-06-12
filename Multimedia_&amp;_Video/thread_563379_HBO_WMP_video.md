---
title: "HBO WMP video"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by robobart on 2007-09-29
Hi, 

I want to view WMP video - specifically, say the ones at [www.hbo.com](www.hbo.com)
(What I really want to do is watch the WMP videos from netflicks - but figured that the videos from HBO would be a good test of my hardware)

I tried to set up mplayer using the directions from 

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-feisty-fawn.html)

But no dice. The player starts and then says "stopped"
I did install the w32 codecs


maybe I should try to install windows media player under wine...

Ideas?

Thanks!

-Bart

---

### Post by jrib on 2007-09-30
I assume you mean the embedded videos on the web page.  Did you:
[LIST=1]
[*]Install the "mozilla-mplayer" package?
[*]Remove all other video player plugin packages (including the default totem-mozilla)?
[/LIST]

By the way, I'm fairly certain the netflicks videos have DRM.  I doubt you will get anything with DRM to play

---

### Post by pbcartwright on 2007-09-30
I got the previews to play from hbo.com . 
I have mediaplayerconnectivity 0.8.3 installed into firefox, and it opens a separate window for mediaplayer and plays the video just fine.
note I said firefox.. and mplayer

---

### Post by jrib on 2007-09-30
If the videos open in mplayer, then they will open in with the mplayer plugin (hbo.com previews work here).  mplayer and the mplayer plugin are different packages however.  Also, there isn't a nice way to tell firefox which plugin to use which is why I asked if you removed all the others.

Glad you got it to work though!

---

### Post by robobart on 2007-09-30
I ( the originator of this post) still do not have it working...

Thanks for reading the posts and I'm glad it can be done, but I am still lost.

Here is what I did to try to make it work:

# aptitude install mplayer mozilla-mplayer

Moreover, I edited my /etc/apt/sources.list and got

# aptitude install w32codecs libdvdcss2

This is all I have done. 

I do mean the embedded videos at [www.hbo.com](www.hbo.com)

And when I try to watch them, the player opens and then just says "Stopped"

Don't really know what you are talking about with the "totem-mozilla" stuff.
Nor do I know what you are talking about with the "mediaconnectivity"

Thanks!

---

### Post by jrib on 2007-09-30
By default, ubuntu has totem-mozilla installed.  If you have both the totem plugin and the mplayer plugin, firefox may be using totem instead of mplayer to play your videos.  Check if the "totem-mozilla" package is installed and remove it.  Then restart your browser.  If it is still not working, visit "about:plugins" in your browser and paste the contents here.

---

### Post by robobart on 2007-09-30
Ah!

I did

# aptitude remove totem-mozilla

and it worked !!!

Thanks so much!

---

### Post by robobart on 2007-10-12
Ok - Now I need a follow up question...
This does work - but there is an issue that I don't understand. 

My S-Video out dies when it tries to play the video from the Mplayer.

(Basically, I have an old laptop with a bad screen. So I took the s-video out and plugged it into my tv. Now I have a way to watch shows from NBC and the Comedy Channel) 

I wanted to watch the videos from HBO too - but they require M-player and then kill my screen again.

Also - I just picked the videos from HBO as an example that everybody could go to, 

When try to watch a cd with AVI's on it, my S-video also dies.

I know it is kinda an off the wall question,

Thanks!

---


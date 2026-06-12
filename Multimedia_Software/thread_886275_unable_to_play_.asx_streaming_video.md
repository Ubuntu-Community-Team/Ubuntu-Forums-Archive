---
title: "unable to play .asx streaming video"
date: 2008-08-11
forum: Multimedia Software
---

### Post by afeasfaerw23231233 on 2008-08-11
i tried real player, totem, mplayer, vlc and smplayer and all failed. the live streaming video i want to play is : [http://2008.i-cable.com/asx/2008_live2_1028547.asx](http://2008.i-cable.com/asx/2008_live2_1028547.asx) it played in properly windoze xp. thanks in advance.

---

### Post by faintscrawl on 2008-10-20
I have a similar problem. Have found no solution yet.

---

### Post by faintscrawl on 2008-10-20
Ok, sort of found a solution.

When I clicked on the link a window popped up. It never would play. I took a part of the url of that window and pasted into Amarok under 
add radio streams", then LOAD, then PLAY. It works.

Here was the original url of the popped up window:
[http://www.cbc.ca/radio2/cod/codPlayer.html?http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah](http://www.cbc.ca/radio2/cod/codPlayer.html?http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah) McLachlan performs solo at BC 150|Play All Tracks

Here's the part I put into Amarok:

[http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah](http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah) McLachlan performs solo at BC 150

Hope that helps.

---

### Post by DaGrimReefah on 2009-11-21
> **faintscrawl said:**
> Ok, sort of found a solution.

When I clicked on the link a window popped up. It never would play. I took a part of the url of that window and pasted into Amarok under 
add radio streams", then LOAD, then PLAY. It works.

Here was the original url of the popped up window:
[http://www.cbc.ca/radio2/cod/codPlayer.html?http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah](http://www.cbc.ca/radio2/cod/codPlayer.html?http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah) McLachlan performs solo at BC 150|Play All Tracks

Here's the part I put into Amarok:

[http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah](http://www.cbc.ca/radio2/media/20080804sarah/all.asx#Sarah) McLachlan performs solo at BC 150

Hope that helps.

Um, the name of this thread is "unable to play .asx streaming VIDEO", not "unable to play .asx streaming MUSIC". Amarok is no solution to this thread. I am having a similar problem to the OP. I am trying to watch certain channels on tvweb360.com, and the mplayer, gecko-mediaplayer, vlc, xine, and totem plugins won't work. I only had 1 plugin installed at a time, so plugin conflicts couldn't be the problem. Any help?

---

### Post by DaGrimReefah on 2009-11-22
OK, I found an effective, but slightly cumbersome alternative.

Certain .ASX playlists, particularly those within TVweb360.com, just won't work correctly using linux players. I've tried the VLC plugin, the gecko-mediaplayer plugin, the xine plugin, all with totem-mozilla uninstalled to no avail.

The only player I found that will actually play those certain channels on TVWEB360 is the obsoleted mplayer codec. You can get it like this:

```
sudo apt-get install mozilla-mplayer
```

But be sure to remove totem-mozilla first, as they will not work together, even if you disable totem-mozilla. If you decide to apt-get remove totem-mozilla, don't worry if it removes the gnome package as well. You will still have gnome, you just won't have that gnome package.

```
sudo apt-get remove totem-mozilla
```

Make sure you also have the w32codecs installed as well.

```
sudo apt-get install w32codecs
```

Then, when you decide to play one of those funky channels, it will tell you it's connecting, then it will say "Stopped". Keep pressing play until you see the yellow loading circle and you get sound. Although you get sound, you won't have any video yet. Press play again, and you'll see video flickering. If you press pause before it can load again, then viola. You can actually watch the video with sound in your browser. After you are done watching, go into console and type

```
sudo killall mplayer
```

Do that a couple of times, as you had to open 2 instances of mplayer, 1 for sound and 1 for video. See, I think the problem is that TVweb360 sends it's ASX playlists in 2 streams: audio and video, through the IPV6 protocol. However, unless you specifically compile these players to disable IPV6, they cannot play the ASX. Therefore, you have to trick mplayer into allowing you to watch the video using mplayer's overlay screen. All linux players have overlay, but there's something about mplayer's that will allow you to watch these videos. So remember, press play, then when you hear sound, press play again, then press pause after you see the video show up. Then when you're done, type
```
sudo killall mplayer
```
a few times in console, or else you'll wind up with a shlt-load of mplayers running. I hope a real solution to this problem turns up soon, but I hope this will allow you to enjoy watching all of TVWeb360's channels on Ubuntu!

---


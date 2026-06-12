---
title: "Increase buffer time of a streaming video?"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by schnupi on 2007-05-15
Heya

Just one little question.. whenever I am watching a video online with totem (mainly .divx stage6 videos) the video only buffers 10 seconds .. when I pause the video for instance so it loads for a bit longer and i can watch the movie without waiting on buffering it stops. Totem just seems to buffer a online video whenever I play it and then only with 10 seconds... 

I hope this was not too unclear now ;).. Its just something that has been annoying me for a while..

Would that be a totem or a gstreamer problem? and how can  i change it, preferably so it loads it all and not just 10 seconds so i can load the whole video before i start?

---

### Post by dfreer on 2007-05-15
I hated that about totem, so I used the mozilla-mplayer plugin instead. Mplayer will stream and if you pause the movie it will continue buffering until it gets the entire movie.

---

### Post by schnupi on 2007-05-15
yea i use mplayer as well but its just .divx (stage6 vids) dont seem to work with mplayer yet... ://

---

### Post by dfreer on 2007-05-15
hmmm hadn't noticed, sorry. tried vlc-plugin?

EDIT: googling around it seems that gxine plugin for totem (using xine instead of gstreamer as the backend) may resolve this issue, I'll see if I can find a .divx and try it out.

---

### Post by schnupi on 2007-05-15
ok i ll try that now.. might just as well as i am probably not gonna do any more study.. silly uni exmas :P

edit: ok just tried it and it doesnt seem to change anything. i uninstalled totem und installen totem-xine through synaptic. when i click on about in totem it says "Movie Player using xine-lib version 1.1.4 and GNOME" .. so i suppose i didnt do much wrong........ oh yeah and its not 10 secs its 7 seconds :P

---

### Post by Praill on 2007-09-17
OK, I know this post is old but through google (and internal) searching, this was the only post I found regarding this subject, so I'm going to post my solution here.

Assuming you already have w32codecs and the mediaplayerconnectivity plugin the solution is to download and use GXINE as your streaming agent. Gxine is the only program (that I found) that would actually show you your position in the stream, how much was buffered ahead, and let you fast forward. I still have yet to find a program that will let you rewind even a second into the stream... so if anyone does.. please, please post.
Solving the 10 second problem in gxine is actually done through solving a problem with the xine engine. In gxine click on File-->Configure-->Preferences-->engine-->buffers. You can fiddle around with the numbers here to set the buffer limit higher. I personally set both audio and video buffers to 2000 and got a 1:27 buffer size from the stage6 videos.

---

### Post by zeusalmighty on 2008-01-14
It works for me! One thing, you need to change the experience level of the GUI to "**Master of the known universe**" to get every single option and tab, including the **Engine** tab.

And for some reason, only the first time I click on the link does it get transferred to gxine correctly.

PS. Gxine is butt ugly, but it's configuration options are waaaaay better than totem!

---


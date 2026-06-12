---
title: "help me run imbedded video in firefox"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by 4KvRMU7Nnv on 2007-04-21
Ok, I'm running my brand new copy of Feisty and I installed everything I could find about firefox plugins, totem plugins for mozilla, gstreamer stuff.  I have w3codecs installed as well, but when I try to watch imbedded movies, like the kind that will show up in a mininture windows media player on windows, i just get a little black X, and no video.  Am I doing something wrong?  I know its possible becuase it worked on PCLInuxOS by default, but i couldn't ever use anything but ubuntu.  I would like to get this working so if you have any suggestions, please tell me.

---

### Post by Sanchopinky on 2007-04-21
I also downloaded all the codecs on feisty and when I try to see a video, the thing pops up and it says loading. It just stays 'loading' forever.

---

### Post by mcduck on 2007-04-21
I recommend using mplayer plugin for firefox.

---

### Post by desmondo on 2007-04-21
I had the same problem: Windows media streams wouldn't play in Firefox even with the gxine plugin and w32 codecs installed.

The solution was to uninstall *totem-mozilla* using package manager, which must have been installed by default with my Ubuntu desktop. Once I did this Firefox successfully used the gxineplugin.

Note that I use the gxine plugin because I like that the streams open in their own window, but you should be able to have success with the mozilla-mplayer plugin once the totem one is removed.

Hope this helps!

---

### Post by eyelessfade on 2007-04-21
In my experience the firefox plugin MediaPlayerConnectivity is the best. You can play any media in the player you wish. [MediaPlayerConnectivity]("http://membres.lycos.fr/sethnakht")

---


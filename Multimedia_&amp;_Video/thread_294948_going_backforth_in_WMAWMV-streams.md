---
title: "going back/forth in WMA/WMV-streams"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by lodp on 2006-11-07
I've tried several programs that supposedly can handle wmv streams (kmplayer, mplayer firefox plugin, kaffeine, VLC), but only VLC seems to have a limited ability to go back and forth in WMA and WMV-streams.

Now, I would use VLC, but VLC happens to play back those streams very skippy, there's stuff missing like every 10 seconds.

Any suggestions?

[whine]I pretty much have to use a different player for every format, and I wouldn't mind, if only I wouldn't have to choose between skippy playback and not being able to jump to postions in a stream[/whine]

---

### Post by sebastfr on 2006-11-07
Have you tried using the "-forceidx" switch to mplayer? That forces rebuilding the index and might do the trick... (I understand this is a poor solution as it takes some time to build the index!)

Seb

EDIT: and btw you can fix those videos permanently by using mencoder (made by the mplayer team)

---

### Post by lodp on 2006-11-07
I tried

> mplayer -forceidx <stream>
but that doesn't seem to change anything -- when i hit the up/down key, or the page up/down key, mplayer stops saying

> Stream not seekable!

Anyway, can run options be integrated at all when using the GUI? I was looking for a way to do that with the "-ao=esd" option for playing back sound on a remote host (audio dongle+speakers on my router), but I couldn't figure out how to do it in either kmplayer or gmplayer...

---

### Post by sebastfr on 2006-11-07
> **lodp said:**
> I tried


but that doesn't seem to change anything -- when i hit the up/down key, or the page up/down key, mplayer stops saying



Anyway, can run options be integrated at all when using the GUI? I was looking for a way to do that with the "-ao=esd" option for playing back sound on a remote host (audio dongle+speakers on my router), but I couldn't figure out how to do it in either kmplayer or gmplayer...

editing '~/.mplayer/config' should do the trick?

sorry the forceidx switch didn't work, I don't know what else could do...

seb

---

### Post by lodp on 2006-11-11
thanks for that -- seems like the config file is the place for that. couldn't get it to go back and forth in streams, though (like you can when you use windows media player for instance). looks like i have to deal with it.

this really sucks when you're like half into a 2h webstream, and your connection breaks for some reason. you have to start at the beginning again..

anyway, i figured out how to include options in kmplayer, so i can use the  "-ao esd:192.168.1.1" option and have sound on my speakers that are attached to the router. pretty cool. i also discovered how to make the xine engine's esd output plugin play back sound on a remote host (just type "export ESPEAKER=192.168.1.1" before starting the player). i think i'm going to write a howto on playing sound from your router's usb port..

---

### Post by lodp on 2007-08-13
Anybody know anything about progress in this area (going back and forth, or pause playback in streams?)

I just discovered that you CAN go back and forth with mplayer in .divx streams. but that's about the only one i discovered so far. if you do it when watching a RealMedia or WMV, playback just stalls and you have to start over from the beginning.

---

### Post by dixon on 2007-09-23
I've found on the internet, that the latest svn mplayer is able to seek in wm streams, but I didn't try it yet....

---

### Post by lodp on 2007-11-12
i couldn't find anything to that effect in the release notes for the 1.0rc2 version -- you remember where you read it?

---


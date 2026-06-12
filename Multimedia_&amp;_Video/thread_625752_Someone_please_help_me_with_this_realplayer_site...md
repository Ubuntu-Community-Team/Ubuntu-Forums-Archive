---
title: "Someone please help me with this realplayer site..."
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by spotdog14 on 2007-11-28
Can someone please help me with this site: [http://www.house.mi.gov/video.ram](http://www.house.mi.gov/video.ram)

I cannot get the video to work, i have the mplayer plugin for Firefox, also i have Movie Player, Mplayer, and VLC players and none of them work. The only thing i can get to work is the audio in the mplayer plugin for firefox. 

If i could get some help that would be great! Thanks!

---

### Post by ron999 on 2007-11-28
Hi
Right-click on that link [http://www.house.mi.gov/video.ram]("http://www.house.mi.gov/video.ram")
and Save Link As...
and download the file to your hard drive.
The file name is **video.ram**.
Open up the file with a text editor.
You'll see it says inside:-
**rtsp://realserver.house.mi.gov:80/broadcast/video.rm**

That is the link you need.

I can get this to play with Real Player 10 using
File > Open location
Then paste it in.
Or alternatively type in the monitor:-
realplay rtsp://realserver.house.mi.gov:80/broadcast/video.rm

I'm watching it now. It's live from the Michigan House of Representatives.

I can also get it to run with Totem, but there's no sound.

So Real Player is the one to go with imho.

I've attached a screenshot.
:cool:

---

### Post by nick_h on 2007-11-28
It worked for me in mplayer.  Type:
```
mplayer rtsp://realserver.house.mi.gov:80/broadcast/video.rm
```
If it doesn't work check that you have the appropriate codecs installed.  Look [here](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by spotdog14 on 2007-11-29
Sweet thanks guys, works great after i downloaded realplayer 10.

---


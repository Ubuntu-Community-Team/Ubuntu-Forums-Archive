---
title: "Smplayer, mplayer intel video possible tip"
date: 2015-04-28
forum: Multimedia Software
---

### Post by Rob Sayer on 2015-04-28
This isn't a support question, just something I tried.  It's on a Mint 17 install (I like Cinnamon) but I don't see why it wouldn't be worth trying in ubuntu.  It should work for any other mplayer front end, and it's exceedingly easy to undo in smplayer.

Smplayer is my default video player on the laptop I use for that but some videos showed a bit of tearing.  The bit rate didn't seem to have anything to do with it, and it usually happened on mpeg4 ASP (ie. divx/xvid), which is easier to decode than AVC/h.264.  So it did not look like a performance issue.

Machine has an intel i3-380m cpu with intel integrated video.  For some reason no matter what command I use to get the video card I've never been able to get a better answer than "intel integrated hd video" or something like that.

Smplayer version is 0.8.6, mplayer2 version is 2.0-701-gd4c5b7f-2ubuntu2.

What I did was make smplayer output video to adapter 1 (intel textured video) instead of adapyter 0, as in this link:

[http://unixangst.com/blog/?p=23](http://unixangst.com/blog/?p=23)

Note that link is from 2009.  Usually I wouldn't use something that old but it's easy to undo.

Funny thing is, if you're in smplayer and you go to preferences to change the video output module there is one for xv textured video which they call intel video sprite or something ... I'm on another machine now.  But if you select it it doesn't work at all with some formats, and at all times it doesn't play nicely with the window manager at all.

However, the solution in the above link works *extremely* well after testing it for a week or so.

In smplayer you don't have to assign the video to whatever port # the intel textured video adapter goes to.   Just add "vo=xv:port=<whatever port on your hardware>" to preferences > advanced > options for mplayer.  I'd put it first in the list if you have other args there. 

Hope this helps.

---


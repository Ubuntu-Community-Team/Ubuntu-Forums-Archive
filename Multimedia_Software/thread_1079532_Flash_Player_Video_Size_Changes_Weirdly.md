---
title: "Flash Player: Video Size Changes Weirdly"
date: 2009-02-24
forum: Multimedia Software
---

### Post by valtemar on 2009-02-24
Recently, when playing flash video (e.g. YouTube clips) the size of the video can suddenly shrink inside the plugin window, then get back to normal. It kind of... blinks or whatever you may call it. Sound is ok, but it looks dreadful.

**Here's a screenshot, see for yourself: [http://bayimg.com/hanDoAaBM](http://bayimg.com/hanDoAaBM)**

This has been going on for some time now, however it wasn't there right after I installed xubuntu-restricted-extras. I removed flashplugin-nonfree and did a manual reinstall, but no good. So suggestions appreciated. Thanks.

---

### Post by gandaran on 2009-02-24
are you sure it's adobe flash firefox is using or something else? could be gnash or swfdec!
right click the flash video window, if it's adobe it should say adobe flash player 10 or 9

---

### Post by valtemar on 2009-02-24
> **gandaran said:**
> are you sure it's adobe flash firefox is using or something else? could be gnash or swfdec!
right click the flash video window, if it's adobe it should say adobe flash player 10 or 9

Yes, it's Adobe Flash Player 10.

---

### Post by gandaran on 2009-02-24
is your ubuntu 32-bits or 64-bits?
if you don't know type this command **uname -m** and post here

---

### Post by valtemar on 2009-02-24
> **gandaran said:**
> is your ubuntu 32-bits or 64-bits?
if you don't know type this command **uname -m** and post here

```
lvr@lvr:~$ uname -m
i686
```

To rule some options out, I downloaded an .flv Flash video file and tried playing it in mplayer. Played beautifully.

---

### Post by gandaran on 2009-02-25
okay, your system is 32-bits and you have adobe flash 10 32-bits installed, should work fine! but it doesn't, could be a problem with your videos card driver! if you are running special effects/compiz try disabling them then try the flash videos again, and you can also try disable hardware acceleration option by right clicking the flash video window » configurations. 
you can play any flash video in mplayer, vlc or totem but it has nothing to do with the adobe flash plugin, the players use different codecs.
totem has a youtube plugin, enable it in edit » plugins, you can browse and play any youtube video.

---

### Post by valtemar on 2009-02-26
Thanks for the reply gandaran. I didn't know the plugin uses it's own codec for decoding. Thank you also for the Totem plugin tip.

As for debugging the problem:

[LIST]
[*]I'm running on rather old hardware, so no composite effects are in use.
[*]Switching hardware acceleration off in Flash configuration has no effect.
[*]Changing video card driver from proprietary (nvidia 96.*) to open source has no effect.
[/LIST]
Puzzling.

Edit: Oh, I forgot to mention the problem persists when switching from Firefox to Epiphany.

---

### Post by peter.o on 2009-03-11
i have the same problem under windows xp
flash version 10.0.12.36

---

### Post by valtemar on 2009-04-12
This bug has been reported to Adobe's bug database a couple of months ago and they appear to be working on it:

[https://bugs.adobe.com/jira/browse/FP-1537](https://bugs.adobe.com/jira/browse/FP-1537)

Another discussion here:

[http://help.youtube.com/group/youtube-issues/browse_thread/thread/87529ea96170f9ca/](http://help.youtube.com/group/youtube-issues/browse_thread/thread/87529ea96170f9ca/)

The problem is related to the encoding of the Flash video. Apparently, older systems can't handle the latest video encoding techniques such as h.264 used in Flash nowadays. The links above provide a couple of workarounds for YouTube videos.

---


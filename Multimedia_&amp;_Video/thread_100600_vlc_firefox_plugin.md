---
title: "vlc firefox plugin"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by fast orange on 2005-12-07
i installed vlc and the firefox plugin from package manager.  vlc works great, but no luck in firefox.  i get a black screen with "no picture" labelled on it.  has anyone found a fix for this?  

Oh yeah, i already tried mplayer without any luck.  so don't suggest that, is there any other video players with a working firefox plugin if i cant make this work?

---

### Post by frodon on 2005-12-08
You could try the media player connectivity extension of firefox, i got the same problems than you at the time and now i have no problem with embedded videos using this extension.

---

### Post by underwater on 2006-02-23
Yeah, I have the same problem which sucks because honestly Mplayer and totem can't even begin to play the video in firefox.  I thought I saw it mentioned in passing in other threads so I'm going to keep looking in hopes of finding some type of solution


ugh.  I hate how gnu/linux is awesome at so many things but then falls down when it comes to video.

---

### Post by frodon on 2006-02-23
I think you shouldn't have all the codecs installed. Install all the codecs, try/configure the firefox extension it will solve your issue with embedded videos.

---

### Post by underwater on 2006-02-23
[QUOTE=frodon]I think you shouldn't have all the codecs installed. Install all the codecs, try/configure the firefox extension it will solve your issue with embedded videos.[/QUOTE]

If you are saying I don't have the codec, I do.  All of the media players can play the media if I save it to my hard drive first, but nothing works when embedded into firefox :-/

---

### Post by frodon on 2006-02-24
even with the "media player connectivity" extension ?

It's quite strange, if mplayer, gxine and vlc plugins don't work at all there's something wrong somewhere but i don't see what if you installed all the codecs.
Do you get errors when you try to launch embedded videos or does it just freeze ?

---

### Post by underwater on 2006-02-25
[QUOTE=frodon]even with the "media player connectivity" extension ?

It's quite strange, if mplayer, gxine and vlc plugins don't work at all there's something wrong somewhere but i don't see what if you installed all the codecs.
Do you get errors when you try to launch embedded videos or does it just freeze ?[/QUOTE]


Actually the extension worked perfectly!

I didn't know the extension even existed.  I don't recall seeing it in the wiki or anything like that.   that solved the problem perfectly.  Thanks!

---

### Post by stillingen on 2006-04-22
[QUOTE=frodon]even with the "media player connectivity" extension ?

It's quite strange, if mplayer, gxine and vlc plugins don't work at all there's something wrong somewhere but i don't see what if you installed all the codecs.
Do you get errors when you try to launch embedded videos or does it just freeze ?[/QUOTE]

How do one enable the media player connectivity extention?

---

### Post by frodon on 2006-04-22
Open firefox and go to the tools tab then click on "extensions", click on something like "get more extensions" it will open the mozilla firefox extension page, then all you have to do is to look for the "media player connectivity" extension and install it.

---

### Post by stillingen on 2006-04-27
Many thanks. I've tried the media extension, but without any luck.
vlc player start, but no video. Any idea?

I've also installed media extension and/or Firefox-vlc-plugin on a fresh Dapper install running Firefox 1.5.0.1,  and are experiencing the same problems. Is this a known and common problem?

---

### Post by frodon on 2006-04-28
You could select another player with the firefox extension, i use xine-ui with the extension and i never got any problems. My advice it to do some more tests with the extension changing the player used by the firefox extension.

Hope you will get it working soon ;)

---

### Post by GranpaDan on 2008-04-27
> **frodon said:**
> Open firefox and go to the tools tab then click on "extensions", click on something like "get more extensions" it will open the mozilla firefox extension page, then all you have to do is to look for the "media player connectivity" extension and install it.

I tried this and it says that the "media player connectivity" extension is not compatible with the Firefox version 3.0b5 that came with my upgrade to Hardy.

Right now the Google/Youtube embedded videos do play, though somewhat choppy and not as smooth as they did when I had VLC as the default video player when I had Gutsy. I'm starting to get the opinion that this may have to do more with the new beta version of Firefox than it does with Hardy. My DVD playback on VLC with Hardy is flawless.

---


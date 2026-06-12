---
title: "Totem movie player (gstreamer) doesn't cache streaming videos??"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by sshetye on 2007-07-02
Hi folks,

I noticed something weird with **Totem movie player/gstreamer** on my feisty (7.04)  installation. Streaming movies streamed from the internet are NOT cached by the player. 

Eg. open totem movie player (the default ubuntu player) and load the URL below. (It an advertisement by hoover - and no I have no connection with Hoover but I noticed this issue on their website - feel free to try other mpg if you want)

[http://media.hoover.com/Media/PageImages/home/TTIWTVideo/FeatureMain.mpg](http://media.hoover.com/Media/PageImages/home/TTIWTVideo/FeatureMain.mpg)

Now when the movie ends (and you're in repeat mode) the player tries to download the media again (and you get jitters again :( )

Windows Media Player caches the media on the hard disk so subsiquent playbacks are jitter-free. That's a smart thing to do for 99% of cases.Is there a way totem movie player / gstreamer / xine / vlc can act in the same manner for streaming videos ??

Thanks

---

### Post by dfreer on 2007-07-02
mplayer does cache it by default, it saves it in /tmp/ so your best bet may be to install the firefox mplayer plugin.
VLC does also, but only like 12 seconds of the media I believe.
I don't know why they do this, it bugs me too ;)

The only bad thing about windows media player is that it likes to cache the ENTIRE film to disk before playing, whereas mplayer will start playing the cache after a certain limit is reached, resulting in much quicker playback.

EDIT: I don't believe gstreamer has anything to do with it, as this problem occurs when using the totem with xine.

---

### Post by sshetye on 2007-07-02
> **dfreer said:**
> mplayer does cache it by default, it saves it in /tmp/ so your best bet may be to install the firefox mplayer plugin.

The mplayer plugin also has the same effect i.e. redownloads/ re-streams the content instead of cache playback :(

> 
The only bad thing about windows media player is that it likes to cache the ENTIRE film to disk before playing, whereas mplayer will start playing the cache after a certain limit is reached, resulting in much quicker playback.

Actually WMP downloads just a part of the stream (till it thinks it can stream continuously till the end of stream). It doesn't download the entire file !!

---

### Post by dfreer on 2007-07-02
I didn't try your hoover vacuum link but instead used a file off my local GNUMP3D server.
hmmm. see, in my experience, anytime I click on a media link (not embedded media), in windows it always wants to save the file to my desktop, or open with windows media player. When you open with windows media player, it simply downloads the file to a temporary location, THEN opens windows media player to play the local file.
In linux, clicking on the same file will bring up (in my case, mplayer) where it will load a portion of the file (~1250 Kb's or so) and then begin playing. Afterwards, as long as my browser windows is still open that file is still in /tmp/, so I can either click on the media link again (and play the local file), or I could even just play the file in /tmp.

embedded media for WMP is different, of course. it will then stream it like you said. but straight out *.avi's and *.mpg's always result in the entire file being downloaded on my windows XP clients.

---

### Post by sshetye on 2007-07-02
> **dfreer said:**
> I didn't try your hoover vacuum link but instead used a file off my local GNUMP3D server.
hmmm. see, in my experience, anytime I click on a media link (not embedded media), in windows it always wants to save the file to my desktop, or open with windows media player. When you open with windows media player, it simply downloads the file to a temporary location, THEN opens windows media player to play the local file.

While this is slightly off topic, for me, WMP9,10 as well as 11 on XP as well as Vista (IE only) have been working for the past few years for me the way I've described above (stream -> playback -> cache ->  playback). You need to make sure the file associations are set to WMP and that IE has its default settings. Make sure your filewall isn't blocking WMP access to internet directly too. And yes, this is for stand alone linked AVI/MPG files, not video files embedded inline with HTML (which uses the WMP plugin for playback) Additional details are beyond this thread but can be found online.

> **dfreer said:**
> 
In linux, clicking on the same file will bring up (in my case, mplayer) where it will load a portion of the file (~1250 Kb's or so) and then begin playing. 

... That is true for my setup too.

> **dfreer said:**
> 
Afterwards, as long as my browser windows is still open that file is still in /tmp/, so I can either click on the media link again (and play the local file), or I could even just play the file in /tmp.


Here my feisty setup doesn't behave the way you describe. To state everything that happens, 
1) The HTML page is replaced by a full (browser) window totem movie player screen (controls at the bottom)
2) Totem starts streaming the file (pausing, playing, sometimes pausing again for rebuffering)
3) After the media ends, it RE-streams off the internet and behaves like step 2.

Of course this is inside the firefox window itself, so the browser is open. Also, this happens either with totem gstreamer or totem xine and firefox keeps my cache at ~/.mozilla/firefox/9ub4yy68.default/Cache (I think this is an installation default).

So, since you have it working, could you tell me your software versions as well as any config. setup to make it work "nicely" ?

---

### Post by dfreer on 2007-07-02
hmmm. well, I'm using:
mozilla-mplayer (3.31+main-1ubuntu1)
mplayer (2:1.0~rc1-0ubuntu9.1)
firefox (2.0.0.4+1-0ubuntu1)
All of which are the latest feisty packages.

I can try on a fresh box, but I think I had to uninstall the totem plugin for firefox that way the mplayer plugin would work correctly, but beyond that I didn't configure anything special. Totem does behave like the 3 steps you mentioned, with it having to redownload the video on each subsequent play. I'll test mplayer a bit more throughly to see whether different file types/encodings make a difference, but I think this is a player issue and not gstreamer/ffmpeg/etc.

EDIT:
> **sshetye said:**
> While this is slightly off topic, for me, WMP9,10 as well as 11 on XP as well as Vista **(IE only)** have been working for the past few years for me the way I've described above (stream -> playback -> cache ->  playback).

Ahh, I think this is why it doesn't work for me, I use firefox exclusively in windows :)

---

### Post by MCSE_Crossover on 2007-07-02
You had stated you are using Feisty (7.10)...are you using Feisty 7.04 or Gutsy 7.10? I just wanted to make sure you werent using a development version when experiencing these errors...

---

### Post by sshetye on 2007-07-02
> **MCSE_Crossover said:**
> You had stated you are using Feisty (7.10)...are you using Feisty 7.04 or Gutsy 7.10? I just wanted to make sure you werent using a development version when experiencing these errors...

Oops! My installation is the regular feisty **7.04** release. Accidentally typed gutsy's version number. 

Sorry about that confusion.

Dfreer, thanks for that list of version numbers. So it looks like its not just a setting across any of the video players on ubuntu - its just that no player on ubuntu can stream videos first and then play jitterfree from cache? I'm guessing I need to put a feature request on totem movie player's project page. Sometimes I wish we had a few great apps than many mediocre ones...

So far I've tried (all packages up-to-date with respect to the official repository as of today)...

VLC: Doesn't decode several DivX streams, also doesn't cache steams
Totem Movie Player : plays pretty much all formats, rebuffers often, doesn't cache steams
Noatum : Crashes 100%. "sigsegv" error (segmentation fault?). 
gxine: Plays well, (seldom rebuffers even though it starts playback quickly), doesn't cache streams
mplayer: Always complains of sound device/driver (can't recall), doesn't cache stream

I think I'm running out of ideas ...

---

### Post by sefs on 2007-07-08
gxine is just as bad as totem for me.  It keeps rebuffering too often to provide a good experience.

The mplayer plugin would be perfect but for one bug. It will buffer x% of the movie before starting to play increasing the chance that you can watch the movie with minimal buffering.  x is configurable by righ clicking and going to configurations.  However the movie ever reaches a point where the playing catches up to the buffering then it does the most amazing thing i have ever seen from a linux application.  Instead of pausing while buffering some more and playing from the position where it stopped... the thing decides it needs to restart the entire movie from the beginning.  And at this point one cannot even fast forward the movie  back to where it was cut off.

I hope divx will be releasing a version of their webplayer soon for linux so we can get proper support for streaming soon, with intelligent caching and buffering.

That is based on the speed of your internet connection it should be able to guess how much to buffer before playing, and if you choose to start playing before buffering is completed you just know that you will run into some rebuffers during play, and also caching that you can rewind and fastfoward during watching the movie.  All the linux players seem to lack these basic features.

---

### Post by dfreer on 2007-07-08
> **sefs said:**
> The mplayer plugin would be perfect but for one bug. It will buffer x% of the movie before starting to play increasing the chance that you can watch the movie with minimal buffering.  x is configurable by righ clicking and going to configurations.  However the movie ever reaches a point where the playing catches up to the buffering then it does the most amazing thing i have ever seen from a linux application.  Instead of pausing while buffering some more and playing from the position where it stopped... the thing decides it needs to restart the entire movie from the beginning.  And at this point one cannot even fast forward the movie  back to where it was cut off.

This is exactly what I noticed as well. This is where I mentioned that mplayer stores the movie in /tmp/. I would watch movies/tv shows off of my server, and if the movie caught up to the cache it would restart. Instead of watching the show over again, I would leave the firefox window open, go to /tmp/, and find the movie file (can't remember what the name would be exactly, like mplay379412879 or something like that), and watch it from there. Since it is a local file it allows navigation, so you can move the slider up to the point where you left off. I believe as long as you don't rename the file, it will continue to cache it in firefox so you could even watch the whole movie from /tmp/

Hope this helps sefs!

---

### Post by sefs on 2007-07-08
Hey, I just saw on the gentoo forums that someone may have had luck with the newer version of the plugin.
Version 3.4 sadly there does not seem to be a deb for it, and its in gusty 7.10.  I've downloaded the source from the mplayerplug-in website and am trying to see if i can get it compiled.  Will let you know how it goes.

---

### Post by sefs on 2007-07-08
Failure with the above.  It still behaves in same fashion.

---

### Post by Gremlinzzz on 2007-07-08
[http://ubuntuforums.org/showthread.php?t=478341&highlight=totem](http://ubuntuforums.org/showthread.php?t=478341&highlight=totem)

---

### Post by dfreer on 2007-07-08
Actually, the point isn't "mplayer is better than totem" like your thread seems to try to prove, nor is it a codec issue (that I'm aware of). I think the OP does have a good point, it would be nice to have one player that worked well (for linux). It seems like I have 4 some video players installed (totem, xine, vlc, mplayer), all of which perform seperate tasks that the others can't seem to handle well (xine has great remote support, vlc covers the widest range of codecs, mplayer handles wmv and cache better, and totem seems to intergrate better into GNOME IMO).
I think this would be a good issue to bring up to the developer's of the respective players, along with remote filesystem support (ssh:// smb://), although I'm not sure if that is a problem with nautilus or what.

---


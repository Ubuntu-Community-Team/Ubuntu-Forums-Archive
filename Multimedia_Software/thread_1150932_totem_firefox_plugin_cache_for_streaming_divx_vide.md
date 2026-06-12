---
title: "totem firefox plugin/ cache for streaming divx videos"
date: 2009-05-06
forum: Multimedia Software
---

### Post by macvr on 2009-05-06
hi ,
using jaunty 9.04, updates: up-to-date .

i'v been trying to watch streaming divx videos using totem firefox plugin
but this is very difficult since i dont have the speed required to watch the videos uninterupted, so i try to pause the streaming video ,but the file does not cache, it just loads 9-10 secs of video and stop streaming...

i tried the mplayer firefox plugin, this does allow increasing the cache size, which allows me to pause while the full video loads, but the rest of the streaming files[non divx] do not display properly,i.e: the mplayer doesnt resize to fit into the allocated size in the webpage but rather stays smaller and its not possible to switch to fullscreen mode either.

i tried to use totem and mplayer simultaneously, by only enabling the mplayer divx plugin and disabling all other mplayer plugins. while on the other hand disabling the totem divx plugin alone.

but when i do this the totem divx plugin overrides the mplayer divx plugin. if totem is present mplayer plugins just dont work...

now to my question:
1: is there a way to increase the totem divx player cache size?
2: or is there a way to force firefox to use mplayer divx plugin even when totem is present?

i would hope there is a solution for the first, i like the totem layout...

thanks in advance for any suggestions

---

### Post by djzoid on 2009-08-08
heh same problem this bugs me. ive been searching around and it seems to me that none of the players native to linux are genuinely capable of caching which strikes me as odd. i tried to watch a divx stream and if i pause it then resume playback, well i can not resume playback. it takes me to the beginning of the stream which is a pain in the derriere.

im guessing an alternative would be to use divx player in wine maybe?

---

### Post by HappyFeet on 2009-08-08
> **djzoid said:**
> it seems to me that none of the players native to linux are genuinely capable of caching which strikes me as odd.

This is not true. After 2 1/2 years of using linux, I have never had a problem with caching. I don't have an answer for your problem though.

---

### Post by justsomedude on 2009-08-08
> **djzoid said:**
> heh same problem this bugs me. ive been searching around and it seems to me that none of the players native to linux are genuinely capable of caching which strikes me as odd. i tried to watch a divx stream and if i pause it then resume playback, well i can not resume playback. it takes me to the beginning of the stream which is a pain in the derriere.

im guessing an alternative would be to use divx player in wine maybe?

I use gnome-mplayer (includes firefox plugin). It caches in ~/.cache/gnome-mplayer/plugin, you can just open the file with vlc or other players (or copy it, if desired).

---

### Post by radiofly on 2009-08-18
Hey DJZOID, I'm have the same problem with my player I cannot pause with it not continuing, it just starts over from the beginning. Right now I'm looking for a fix for this and if I find out anything I will let you know.

Radiofly

---

### Post by Katalog on 2009-08-18
> **justsomedude said:**
> I use gnome-mplayer (includes firefox plugin). It caches in ~/.cache/gnome-mplayer/plugin, you can just open the file with vlc or other players (or copy it, if desired).

Same here. Works pretty well.

---

### Post by macvr on 2009-08-18
> **justsomedude said:**
> I use gnome-mplayer (includes firefox plugin). It caches in ~/.cache/gnome-mplayer/plugin, you can just open the file with vlc or other players (or copy it, if desired).

Sure , mplayer has the ability to cache ,but the problem is video does not resize to fit the frame.

If the size of the video is smaller than the frame size, then the video is just a small size! this problem does not arise with totem , which rescales the videos.

A bug regarding this needs to be sent to upstream or launchpad?

if upstream , where ?[bugzilla?]

---

### Post by djzoid on 2010-06-15
Hey dunno if it's worth bringing up but my solution works pretty well for me, i like gstreamer because it has consistently high quality image even on my eee 900.

I use [streamripper]("http://packages.ubuntu.com/karmic/streamripper") to rip divx stuff. streamripper stores everything in ~/Streamripper_rips/incomplete/-.mp3 . You can change the file extension but it doesn't matter, I'm not sure you should be keeping media permanently anyway, this is just a workaround for the lack of caching in totem. Everything else should be cached in tmp or firefox plugin folders.

When you load up a divx movie in firefox simply right click and select 'copy'. Then go into the terminal and type:

```
streamripper $
```Then Ctr+Shift+V to paste the url so it would look like 

this:

```
streamripper $http://www.lionshare/xu895ay57o5u.avi
```and hit Enter!

:wink:

---

### Post by blackaardvark on 2010-06-27
Same headache for me here, there must be a way of disabling totem but I'm guessing that would cause all sorts of undesired repercussions.

> I use streamripper to rip divx stuff. 

This is all well and good if it weren't for the files I'm looking to cache/watch later not having a concrete url (some are hosted on megaupload or rapidshare).

Any suggestions for an alternative, or even getting mplayer working within firefox?

*Just adding the fact that I'm using Lucid at this stage*

---

### Post by djzoid on 2010-07-21
blackaardvark, look in synaptic for mplayer-mozilla or something similiar.

Also if you go into firefox addons menu, you can disable the totetm/gstreamer plugins.

---

### Post by zerojoy on 2010-07-26
yeah, same problem here with totem. For instance, I like to watch videos on stagevu.com. To buffer at times you do have to pause and it always restarts the stream when you press play again. 

I did a test, I watched the network history drops quickly as soon as you pause the stream. It doesn't continue to buffer while paused. 

Is there a fix out there somewhere? I don't like the mplayer plugin. I find that one a bit cumbersome.

---

### Post by the_jlx on 2010-09-21
Mplayer dosent appear to have a plugin anymore?
suggestions?
ubuntu lucid 10.04 64Bit
totem is the worst piece of ***** i have seen and for some reason VLC plugin doesnt work.
even whit a 8Mb down and 1Mb up the movie sites only stream at around 1 to 2Mb speeds and that requiers a decent buffer.

EDIT:Or well i do have the plugins but no way to install them....
Second EDIT: reason being  O_o tried to copy them to all of the ones but dosent show up in FF
/usr/lib64/firefox/plugins
/usr/lib/firefox/plugins
/usr/lib/firefox-3.6.10/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins

---

### Post by the_jlx on 2010-09-21
sudo apt-get install gecko-mediaplayer
Problem solved :)

---


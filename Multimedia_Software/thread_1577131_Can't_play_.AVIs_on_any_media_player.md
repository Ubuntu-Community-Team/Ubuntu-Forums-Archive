---
title: "Can't play .AVIs on any media player"
date: 2010-09-18
forum: Multimedia Software
---

### Post by digitalis_46613 on 2010-09-18
I am running Ubuntu latest revision, but for the last 2 revs I have had the same problem. I have tried removing and uninstalling all media players, codecs and everything with no luck yet.
When I play an AVI it brings up a window saying I need the divx or mpeg-4 codec. Click here to download. When I click it, it tells me it can't find the required drivers. The audio plays but no video. I have installed the codecs from what I can tell.
I have seen errors for DivX MPEG-4 Version 5, X-VID MPEG-4, and H.264.
Any ideas?

---

### Post by SeijiSensei on 2010-09-18
Try [SMPlayer](http://smplayer.sourceforge.net/).  It's in the repositories so you can just run "sudo apt-get install smplayer" (or use Synaptic, KPackageKit or whatever you use to install from the repositories). Everything else you need will be installed as well.

---

### Post by digitalis_46613 on 2010-09-18
> **SeijiSensei said:**
> Try [SMPlayer](http://smplayer.sourceforge.net/).  It's in the repositories so you can just run "sudo apt-get install smplayer" (or use Synaptic, KPackageKit or whatever you use to install from the repositories). Everything else you need will be installed as well.

I tried that already. I got an exit error and it never worked. I 
about ready to just wipe the drive and try again.

---

### Post by wilee-nilee on 2010-09-18
I believe that avi can be a number of formats.
[http://en.wikipedia.org/wiki/Audio_Video_Interleave](http://en.wikipedia.org/wiki/Audio_Video_Interleave)

So I have had a avi once or twice not work but otherwise with the restricted extras and the medibuntu codecs. In vlc or smplayer they always work.

---

### Post by macem29 on 2010-09-18
can't recall throwing anytthing at VLC that it couldn't play, except DRM protected

---

### Post by mordoc on 2010-09-18
> **wilee-nilee said:**
> I believe that avi can be a number of formats.
[http://en.wikipedia.org/wiki/Audio_Video_Interleave](http://en.wikipedia.org/wiki/Audio_Video_Interleave)

So I have had a avi once or twice not work but otherwise with the restricted extras and the medibuntu codecs. In vlc or smplayer they always work.

I would second that recommendation, VLC seems to be able to play almost anything.  Add to the fact that the plugin for FF is an easy way to have online media played within the browser makes it a winner.

---

### Post by mc4man on 2010-09-18
Maybe run a player from the terminal for some useful info, vlc or mplayer are good candidates.

It's very possible the default video output, usually Xv, is unsuitable for your hardware and or video drivers installed, if any.

You could try changing the video output in any of your players, usually thru the preferences menu (vlc - tools -> Pref.'s -> Video, smplayer should be obvious, ect.

For gstreamer the menu item has been disabled for some odd reason - (Multimedia Systems Selector
```
gstreamer-properties
```

Try X11 for starters

---


---
title: "Can't play any WMA files"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Neurasthenic on 2008-11-10
This is probably a very common question - but I have looked around through a lot of solutions and have asked a couple of people to help me, all to no avail. I am trying to enable to support for WMA files in Banshee, specifically - although I can't get them to play in other media players (Rhythmbox, Totem). I have installed:

ubuntu-restricted-extras
w64codecs
gstreamer plugins

I'm talking to a guy who has walked me through installing everything - he says he's walked me through everything he did to get WMA support in Banshee, so it should be working.

When I try to play a WMA in Banshee it just skips the file. In Rhythmbox I get this error: The GStreamer plugins to decode "audio/x-asf-unknown type" files cannot be found

Any ideas?

---

### Post by gandaran on 2008-11-10
are they wma DRM protected files? these encrypted files only work in windows media player

---

### Post by Neurasthenic on 2008-11-10
> **gandaran said:**
> are they wma DRM protected files? these encrypted files only work in windows media player
No, they're files I ripped off CDs. They are lossless WMAs, but I don't know if that should make any difference.

---

### Post by gandaran on 2008-11-10
how did you rip them? with windows media player?

---

### Post by Neurasthenic on 2008-11-10
> **gandaran said:**
> how did you rip them? with windows media player?
Yes. And I used to play them through Foobar in Windows - I don't think DRM is the issue. I could be wrong though.

---

### Post by gandaran on 2008-11-10
look, if I have some time tomorrow I'll rip a cd in windows media player, wma format and try playing the files with rhythmbox, will post back the results
you can also try  download a wma file and see if it works.

---

### Post by gandaran on 2008-11-10
Neurasthenic 
download this wma file [http://s2.orbitfiles.com/index.php?link=454749993&sid=4e37827e47256c213948b985311c95fe&force=1](http://s2.orbitfiles.com/index.php?link=454749993&sid=4e37827e47256c213948b985311c95fe&force=1), try it, you can check and compare the files properties, totem says it's wma version 8, it plays on every player I have installed.

---

### Post by mc4man on 2008-11-10
Amarok, totem-xine, and mplayer can playback *wma lossless* if w32codecs is installed. I'm pretty sure rhythmbox, totem-gstreamer, vlc and probably banshee can't. (not 100% sure on banshee

Unless somethings changed the w64codecs have only some of the codecs available in the 32 bit version

---

### Post by Neurasthenic on 2008-11-11
Bump. I've heard conflicting stories on whether Banshee can or cannot play WMAs - but like I said, I talked to a guy today who uses Banshee all the time to play his WMA files. And he walked me through everything he did to get his working, still no dice.

---

### Post by xc3RnbFO8P on 2008-11-11
Did you install Medibuntu?
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by gandaran on 2008-11-11
Neurasthenic
ripped a cd with windows media player 10, choosed lossless wma
this is what I found out, this lossless wma format doesn't play on any gstreamer based player (totem and rhythmbox) I don't know if banshee is a gstreaner player.
the lossless wma plays fine in xine players, mplayer and audacious!
didn't try vlc as I don't have it installed.

---

### Post by Neurasthenic on 2008-11-11
Thanks gandaran, I guess it's just the fact that they're lossless WMAs. Eh, I guess one of these days I'll have to re-rip them in FLAC, which I should have done in the first place.

---

### Post by gandaran on 2008-11-11
there are other players you can try and better than banshee, exaile is one (don't know if it's gstreamer based or xine, if it uses the xine engine it'll work) the other is songbird [http://getsongbird.com/](http://getsongbird.com/) and many more you can find in synaptic

---


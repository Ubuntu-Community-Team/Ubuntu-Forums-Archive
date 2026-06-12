---
title: "Realmedia in other players"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Pro-reason on 2008-08-27
I have installed the Real Player from Medibuntu, and I can play Real Media in it.  However, other people on the forums seem to be able to play Real Media in MPlayer and VLC too.  How do I make the codecs available to other players?

---

### Post by kostkon on 2008-08-27
> **Pro-reason said:**
> I have installed the Real Player from Medibuntu, and I can play Real Media in it.  However, other people on the forums seem to be able to play Real Media in MPlayer and VLC too.  How do I make the codecs available to other players?
Since you have *Medibuntu* already, then it's really easy for you. You have to install the Windows codecs package called *w32codecs* (or *w64codecs* for 64bit systems).

For *GStreamer* based media players, like *totem*, you should also have the *gstreamer0.10-pitfdll* package installed.

I use *totem-xine* and with *w32codecs* I can play real media files, video and audio, just fine.

*VLC* uses its own embedded codecs, so I don't know how you can make it to play real media.

---

### Post by Pro-reason on 2008-08-28
Yes, I already have all codecs.

The point is that they are supposed to be automatically available to other programs such as *mplayer*, but in my case they are not.  Or rather, all codecs apart from Real are available.

I need to know what to tweak to make other players see the installed codec.

---


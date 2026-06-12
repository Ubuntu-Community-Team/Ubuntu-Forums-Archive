---
title: "General questions about codecs, libraries, plugins and media players"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by mrowth on 2007-10-30
Nothing's broken! Everything works! Ubuntu == video heaven!

But I have questions.

I have:

Video: Kaffeine (using Xine), Totem (Gstreamer) and the Totem plugin for Firefox, MPlayer, VLC

Audio: Amarok, XMMS, used to have Exaile but it crashed

TV, radio: kdetv, kradio

I have also installed the W32 codecs, although I hadn't encountered an unplayable video until then. Just thought I'd better pre-empt any future problems - but I frankly don't know if I need them. (Do I?

My question is: how (roughly) do these things interrelate? 

Do the W32 codecs apply to all media players, or just some?

And: Totem seems to work better as a browser plugin than Kaffeine, even if I use Kaffeine with Gstreamer. For example: I can use Stage6 (video hosting site with embedded divx videos) with Totem... but not with Kaffeine. This was my experience in Feisty, anyway. I'm not going to experiment (and potentially screw things up) now.

Do the Gstreamer and Xine backends, despite their entirely disparate sets of plugin packages, ultimately feed off the same "physical" codec files and where are they? 

For example: I bought a DVD last week. Being TV-boycotting Linux hippie scum, I ripped it with Acidripper (dvdrip or transcode failed to work) into an Xvid .AVI, and can now watch it with all of the aforementioned media players. But are they all using the exact same ...codecs? Or do some (VLC? MPlayer) bring their own? Etc.

Is there any reason to install the Xine frontend (xine-ui or whatever it was) or KMPlayer? They don't seem to bring anything new to the table, besides yet another GUI.

I acquired this present everything-runs-fine functionality by rabidly installling just about anything I could find, and now I feel weird having no idea what anything consists of ;)

---

### Post by por100pre1 on 2007-10-31
Most of your questions are answered with this:

```
kdesu adept_manager
```

Check your media player packages and right click them to see their details. You'll be able to see which packages are recommended, that way you'll see which codecs are used by them.  You can also see which files are installed by any installed package and where the files are located. You can check which packages are recommended by the media players, some are related to the codecs.

---


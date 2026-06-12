---
title: "Xine codec's vanished - won't work again."
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by koonat on 2006-12-26
**Ok, well, I 'fixed' the problem,** but it was a complete stroke of luck, it wasn't rational. Kaffeine, amarok, anything else that used xine complained that I didn't have the ability to decode mp3s. (and SOME (but not all) video formats. And for some reason, when I changed my output settings back and forth, it started working again. (started on alsa, switched to esd, then back to alsa). So, clearly, the problem is irrational and the error messages didn't help at all. (I had been using this setup perfectly for weeks before this happened).   This kind of unexplainable crap is so damn annoying... but at least it works.

I've been using ubuntu edgy for a little while now, I normally listen to my music with Amarok using xine.
Today, when I went to play mp3s - it tells me that it's unable to play because it can't find a 'demux' 

xine: couldn't find demux for >random.mp3<
xine: found input plugin : file input plugin
xine: demuxer failed to start
xine: found demuxer plugin: ASF demux plugin
xine: found input plugin : file input plugin
xine: demuxer failed to start
xine: found demuxer plugin: ASF demux plugin
xine: found input plugin : file input plugin

I certainly didn't uninstall anything, and just yesterday everything worked great.
So, the first thing I tried was removing all packages related to xine and codecs - and reinstalling them, no effect.

I can't figure out where it's looking for the plugins, if I knew, I could probably just find them and put them there (if they are infact even missing).

I'm really baffled, and I looked around and this problem has happened a lot - but nobody has had a solution. 

I'm really concerned about software breaking like this. Most windows apps don't even break this randomly.

---

### Post by ashdezign on 2008-04-12
Amarok just did the same thing to me. Changing out put settings seems to make no difference. Amarok played fine for the last few months then, over the last couple of days Amarok would freeze up when I tried to play a mp3. If I killed Amarok and restarted it it would play fine. Then today it fails completely with this error message:

[B]No suitable demux plugin. This often means that the file format is not supported.

[/B]I haven't removed any packages and have no idea why it suddenly fails. And I cannot get it to play mp3's at all.

I am running Kubuntu 7.10

**UPDATE**

Found this link: [http://ubuntuforums.org/archive/index.php/t-252505.html](http://ubuntuforums.org/archive/index.php/t-252505.html)

Solves the problem but doesn't explain why it might have happened/ been prevented.

---


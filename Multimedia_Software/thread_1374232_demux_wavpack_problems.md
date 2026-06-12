---
title: "demux wavpack problems"
date: 2010-01-06
forum: Multimedia Software
---

### Post by ender8282 on 2010-01-06
I am having problems streaming audio.  The stream in question is: [http://streaming.azpm.org/kuaz128.mp3.m3u](http://streaming.azpm.org/kuaz128.mp3.m3u)
When I launch kaffeine or amarok from the terminal and try to play the stream I see the error: 
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't suported yet.
Before I upgraded from 9.04 to 9.10 I was able to play this stream without problems.  I have installed the medibuntu package and most of the codecs that come with it.  I have already searched for an answer and nothing seems particularly relevant.  What do I need to do to be able to play this stream?
Thanks in advance

---

### Post by Objekt on 2010-01-06
We're in the same situation, though by different paths.  I noticed this "demux wavpack" error when trying to play DVDs in Kaffeine, either from a *.iso image of a DVD, or from a physical DVD in my optical drive.

Like you, I have all the Medibuntu and Ubuntu restricted extras stuff installed.  I know I did it right, because DVD and .mp3 playback works just fine in other applications, such as VLC Media Player.

I posted about this problem in the Kaffeine forums several days ago, but there is no response yet.

In another thread on these forums, someone suggested installing Xine as a possible fix for Kaffeine refusing to play DVDs.  I don't know whether that'd work here, because I haven't had a chance to try it on my machine yet (I'm posting this away from home).  I thought Xine would already be there as a necessary component of Kaffeine, but who knows?  I'll try it some time this week & post whether it fixes the problem.  If so, it might work for you, too.

---

### Post by ender8282 on 2010-01-06
When I try to install xine it tells me that:
Package xine is not available, gut is reffered to by another package...
Your comment about things working in VLC was helpful though.  I am able to play my stream with VLC so at the moment at least I have a work around.

---

### Post by mc4man on 2010-01-06
```
sudo apt-get install xine-ui
```

Don't use kubuntu so obviously not helpful to say the stream plays fine in amarok here (karmic, gnome

---

### Post by Objekt on 2010-01-06
Ugh.  I think Kaffeine 1.0-pre2 is just broken.  I haven't tried playing proprietary-format audio files (*.mp3 and such) with it, but I wouldn't be surprised if it balked at those as well.

I haven't tried Kaffeine 1.0-pre2 under Kubuntu 9.10, or Ubuntu 9.10 using KDE.  It might work fine in those cases.  Most KDE-native apps work in Ubuntu without actually requiring you to use the K desktop environment, but perhaps Kaffeine is an exception.

---

### Post by ender8282 on 2010-01-06
> **mc4man said:**
> ```
sudo apt-get install xine-ui
```

Don't use kubuntu so obviously not helpful to say the stream plays fine in amarok here (karmic, gnome

Well that does help a little.  If you get things to work in gnome it tells me that is has to do with the configuration of my system (either because of upgrading or because of KDE) not with some larger problem.  Xine-ui was installed, and playing the stream with the xine player gives me the error:
There is no demuxer plugin available to handle 'STREAM'.  Usually this means that the file format was not recognized.

---

### Post by mc4man on 2010-01-06
I would guess that in kubuntu what you'd need is provided by libxine1-ffmpeg which I'd assume is installed.

Can you playback a .mp3 audio file with any xine based player?

(if you don't have any then open your station in vlc and click the 'record' button on vlc (view -> advanced controls), you'll get a vlc_record....mp3 in home folder.

If you can't play .mp3 in xine players maybe look in home for .xine folder, and delete the file catalog.cache inside (~/.xine/catalog.cache in ubuntu-gnome

You could also try (if not already) saving your link to file and try loading the .m3u directly into your player

Other than these don't know - hard to presume how things work in kubuntu/kde from here

---

### Post by Objekt on 2010-01-06
> **mc4man said:**
> ```
sudo apt-get install xine-ui
```

Don't use kubuntu so obviously not helpful to say the stream plays fine in amarok here (karmic, gnome

That command seems to have partly fixed Kaffeine for me.  It will now play DVD *.iso's.

However, the "next/previous chapter" buttons are broken.  They simply stop playing of the DVD.  These could just be problems with this particular version of Kaffeine.  The Kaffeine devs seem to have eliminated the "Jump to DVD Menu" feature.  Oh well, at least it plays after a fashion.

---

### Post by ender8282 on 2010-01-07
Getting rid of ~/.xine/catalog.cache did the trick.  Everything works now.  I can now play the stream in question in and I can now play mp3s as well.

---

### Post by naderra on 2011-07-05
2011 and your solution is still applicable. Amarok had stopped streaming ... Thanx.

---


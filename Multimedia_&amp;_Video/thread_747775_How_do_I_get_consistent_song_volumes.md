---
title: "How do I get consistent song volumes?"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by geek_Man on 2008-04-06
Hello everyone, I had a question about getting the volumes of all my songs to about the same. I have ripped a ton of CD's of songs I had gotten from the iTunes store. When I first started doing that, song volumes weren't a problem cause they were all the same (I used the soundcheck feature in iTunes). I have since gotten a bunch of original CD's that, when ripped, are louder than the burned-then-ripped songs. SO! I was wondering if Rhythmbox or any other app or utility could get the volumes the same (or at least fake it). As always, help is much appreciated!

---

### Post by insineratehymn on 2008-04-06
Yup.
mp3Gain

Tutorial?
[http://www.linux.com/articles/59957](http://www.linux.com/articles/59957)

Basically says you can add or subtract dB's, and you can put it into find and do your entire collection all at once.

Sourceforge site: [http://mp3gain.sourceforge.net/](http://mp3gain.sourceforge.net/)

Have fun. :)

---

### Post by geek_Man on 2008-04-06
Hey man, thanks! I'll have to try that when I have time, but I think that's what I was looking for.

---

### Post by geek_Man on 2008-04-06
......Hm, it looks like mp3gain only works on mp3's. All my files are OGG's and FLAC's. Any other ideas?

---

### Post by insineratehymn on 2008-04-07
Tryin to mess with me, huh?

Ok. Research:
[http://ubuntuforums.org/showthread.php?t=498583](http://ubuntuforums.org/showthread.php?t=498583)
[http://mediamonkey.com/](http://mediamonkey.com/)
[http://en.wikipedia.org/wiki/Replay_Gain](http://en.wikipedia.org/wiki/Replay_Gain)
[http://en.wikipedia.org/wiki/Foobar2000](http://en.wikipedia.org/wiki/Foobar2000)
[http://www.rarewares.org/others.php](http://www.rarewares.org/others.php)

The breakdown:

Although ReplayGain's proposal (Link #3) has been widely adopted by lots of media players (Link #3), including Amarok, Audacious, MediaMonkey (Link #2), Aqualung, and lots of others, it varies by which media player you are currently using on how well it implements the standard. The actual conversion is **not** done through actually manipulating the file, but by merely manipulating the metadata of said file (Link #3). Having said that, using a utility that modifies the metadata creates a lossless volume leveling effect because the actual data has never been modified, just the data about the data (Link #3). So, what? I want to do it to FLAC and Ogg? Well, you have options. Foobar2000 (Link #4) says it will do Ogg, FLAC, and Ape's. If you clicked on link #4, you would see that foobar2000 is actually a **media player**, not a **volume leveler**; in fact... the only standalone volume levelizer I've been able to find is mp3Gain, which by its own name says **I only work with MP3's.** 

So, my suggestion? Get a new media player. I don't know which one you are using, but it obviously doesn't respect ReplayGain's standards for equal volume levelizing.

EDIT:

Or you can convert everything to MP3, use MP3 gain, then convert it back to Flac/Ogg. But you don't want to do that, do you?

---

### Post by vanadium on 2008-04-07
Many media players under Linux do support replaygain tags properly. It is only how to apply them that is a bit cryptic and different for different file formats. For ogg, you use "vorbisgain". For flac, you use "metaflac".

vorbisgain -a *.ogg

will analyze all ogg files in the current directory and apply both track gain and album gain (the -a option). You should use the -a option only if all audio files are indeed belonging to the same album.

metaflac --add-replay-gain *.flac will do the same for all flacs in the current directory. If the flacs in the current directory are from different albums, then you would better use

for f in *.flac ;  do metaflac --add-replay-gain "$f" ; done

and then the added album gain will be the same as the track gain. Otherwise, the album gain you store would be nonsensical.

---


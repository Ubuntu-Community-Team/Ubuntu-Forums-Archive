---
title: "ReplayGain with ID3v2.3"
date: 2012-11-07
forum: Multimedia Software
---

### Post by nuk28 on 2012-11-07
I am trying to get ReplayGain data for my music library. It would seem easy enough at first glance, but it isn't. I am trying to use mp3gain (specifically, mp3gain -k -s i -s r *.mp3) to do it, but it always writes id3v2.4 tags. This is not acceptable, as I am planning to use it with my Sansa Fuze, which only supports id3v2.3 tags (and maybe some lower versions, too, but I don't care about those). When I used Windows, I just used foobar2000, which did a very good job. It would be nice if I could a native linux app, though. Plus, I tried mp3gain on some files already scanned with foobar2000, and it gave a slightly different value for gain. 

The other problem with mp3gain is that it writes new tags and leaves the old tags alone, so if you happen to scan the same file twice, it has duplicate data. Granted, this is not technically a problem, but I'm a bit of a perfectionist so that is not at all ideal. 

I also tried Ex Falso, but I cannot find a way to make that program use id3v2.3 either. MP3 Diags will convert tags to id3v2.3, but it seems like it does a bunch of other things, too, that I don't particularly want it to do. 

Anyone have any suggestions on how to mostly automatically update my music library tags? I have something like 4000 tracks, so I would rather not do something by hand.

---

### Post by sydbat on 2012-11-07
Perhaps this could help?

[http://mp3gain.sourceforge.net/faq.php](http://mp3gain.sourceforge.net/faq.php)

---

### Post by nuk28 on 2012-11-16
> **sydbat said:**
> Perhaps this could help?

[http://mp3gain.sourceforge.net/faq.php](http://mp3gain.sourceforge.net/faq.php)

No, that wasn't particularly helpful. I did discover some interesting things with some more research, though. According to [http://www.anythingbutipod.com/forum/showthread.php?t=41988](http://www.anythingbutipod.com/forum/showthread.php?t=41988), the Sansa Fuze does support ID3v2.4. Then I started wondering why I didn't already have 2.4 tags. I guess it must be because I was still using WMP, which doesn't support 2.4 tags at all. Since I still use Windows occasionally, I decided that I still don't really want to use 2.4 tags. 

I also discovered that using the '-s i' option for mp3gain corrupts some album art (I would assume it's only some, but I only tested it on one album - all the art in that album was corrupted). So I decided that it is better to use the default option, i.e. '-s a'. After a bit more digging, I discovered that [MP3Tag runs very well in Wine]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3019") and can [convert tags]("http://forums.mp3tag.de/index.php?showtopic=978#entry5136") from one format to another fairly simply.

After all this, my solution is as follows:

Install [MP3 Diags]("sudo apt-get install mp3diags"). In the "Settings" dialog, under the "Other" tab, change the Normalizer field to "mp3gain -k -p -t -s a -s r" (no quotes). This runs mp3gain, but writes tags to APE so that the album art isn't corrupted. 

Install MP3Tag via Wine. Under Tools -> Options -> Tags -> Mpeg, select Read: ID3v1 and ID3v2, Write: ID3v2->ID3v2.3 UTF-16 (since some of my files contain unicode characters), and Remove: ID3v1 and APE. Note: It would intuitively seem that you should allow Read: APE, but for whatever reason if that box is checked and the music file has APE tags, MP3Tag ignores the data in all other tags. I.e., it reads the file as having no information about Artist, Album, etc.

In any case, after this, select the files that contain APE and ID3 tags, Ctrl-X, then Ctrl-V. This deletes the APE tags and writes them to ID3v2.3. 

And that is, I think, the solution to all my problems. Not super-elegant, but at least it seems to work without too much hassle beyond the initial setup. 

[](/a24)

---

### Post by nuk28 on 2012-11-23
OK, I lied. I guess the method above doesn't work at all, because MP3Tag can't read both the APE tags and ID3v2 tags at the same time, so when copying and pasting, it deletes either all the artist/album/track/etc. info or all the ReplayGain info. 

I resorted to running foobar2000 in Wine, and that seems like it works very well. I'm not sure that it writes the replaygain tags quite like ExFalso or other Ubuntu programs, but I am pretty sure that it's standards-compliant. It works on my Sansa Fuze at least, which says something. And I'm thinking that the reason I thought ReplayGain wasn't working in Banshee is because ReplayGain is only specified for certain types of files. I have .wma, .wav, and several other formats that don't support those tags in a standard way. My Fuze apparently reads ReplayGain info created in Windows in .wma files, but it doesn't surprise me too much that Banshee doesn't read them. From now on, I am always going to rip in FLAC and convert to ogg or MP3 on my MP3 player.

---


---
title: "MP3 organizer/database/manager"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by LilYoda on 2007-02-17
Hello guys.

Can someone recommend me a MP3 manager for Ubuntu?  Tried Amarok, Prokyon, banshee, etc...  but they are mostly focused at playing music, it seems

I am looking for an **organizer** that makes managing a large collection easily.  I was using Mediamonkey on windows, not sure if you've seen it, but that's basically that type of functionnality I'm looking for...  Main function I'm looking for is to be able to retag by drag & dropping tracks from one category to the other...  For exemple, select all files tagged as "Alternrock" in genre, and drag them to "Alternative Rock"...

Any software out there that does this?  I wanted to try Lsong and Yammi, but they don't seem to want to run without KDE :/

---

### Post by nolageek on 2007-02-18
I'm looking for something along these lines, but FOR KDE.  I have about 7000+ songs and I'm always downloading more...  I'm trying to find software that will manage the audio file system, much like iTunes does.  I use an external HD and couldn't even get Banshee to be able to use it.  Amarok and Songbird seem to just 'monitor' directories. I edited some tags (artist, song names, album titles) and when I looked in the directories themselves nothing had changed. LSongs, Yammi and Listen seem to be promising, but LSOngs and Yammi don't seem to be still developed.

Anyone have any good suggestions? Does this Exhaile have a website?  I can't find ANYTHING out about it.

---

### Post by Soarer on 2007-02-18
Exaile has a web site: [http://www.exaile.org/trac](http://www.exaile.org/trac).

I think the extra 'h' was leading you astray :)

---

### Post by nolageek on 2007-02-18
That seems to be the problem.  Anyone know a good player that handles the file-system aspect so my directory stay neat and tidy?

---

### Post by koshari on 2007-02-18
use easytag to manage the tags , keep the files in "a/artist/album/01 - song.mp3 " organization.
and then use amarok to play . the beuty of amarok is it uses a database to sort the songs in view , and the accuracies of the database depend on the validity of the tags.

also use mp3gain to keep all your songs at 89Db so you loose the volume adjust woes when you play on dynamic play.

easytag will take care of all your file renaming bases on any combination you like.

---

### Post by nolageek on 2007-02-19
I'll check easy tag out.  I just hate having a million utilities to manage things.  I use my external HD for my audio and I use it across several computers... so I'm always adding new tracks to it...  it's a pain when I add say, 600 new tracks to it and update the tags but they're still sitting in some random directory instead of in the correct artist/album directory.  This is the ONLY reason I still use iTunes.

---

### Post by LilYoda on 2007-02-19
> **nolageek said:**
> I'll check easy tag out. 

Already did.  It's still very cumbersome...  There's no way to tag via drag & drop, for exemple...  Haven't found a way to quickly select all tracks from a specific genre, or a specific year, for exemple.
Does anyone know of a music organizer that works with drag and drop?  Like select a track, and drop on a genre, and bam, the genre is added to the track...  I tried madman, but it keeps crashing after a while...

Regarding Amarok, I find it very annoying that:
1) depending if you're in the context or collection tab, then clicking a music track doesn't do the same thing.
2) you can't rate a song by just right clicking it and having a menu to set a specific rating...
Amarok sucks at tagging btw, I tried yesterday, and if you have a large number of tracks, it's not even worth trying..  To many operations to just retag the contents of an album correctly.

But if you're just looking for a player, then yes, Amarok is great.  That context feature is really cool...

I'll give exaile a try...

---

### Post by LilYoda on 2007-02-23
I tested cowbell, quodlibet, and more others, still none that can support drag & drop tagging... or another way of easily retagging/managing

So I am still using Mediamonkey, in a vmware machine running XP...

If anyone knows of an organizer supporting drag and drop tagging, I'd really love to know

---

### Post by urukrama on 2007-02-23
Have you tried gmusicbrowser?

[http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html)

According to the site it is  'an open-source jukebox for large collections of mp3/ogg/flac files'

I've used it in the past, and quite liked the way you could really play with the GUI/layout and give it a very different look, but decided to drop it in the end for Exaile/QuodLibet. I don't have that many files, so I can't really say if it does handle that many quite well.

---

### Post by LilYoda on 2007-09-07
THREAD NECROMANCY!!!! :):):)

I think I found a good candidate as the ultimate MP3 manager/tagger...  I've been testing it for a couple of days, and it seems that
 - it can handle large collections easily
 - has a GOOD musicbrainz integration, so it can retag your files if they have been done incorrectly.  The integration is done cleverly, meaning if there is an incorrect Musicbrainz detection, it is easy to correct it (unlike other tools like Picard)
 - has a spreadsheet type of interface, you can copy and paste anything from anywhere to anywhere.  So copying the album art from one file to 10 others is as simple as Ctrl+C, select 10 fields to be tagged, Ctrl+V
 - runs on Linux, MacOs and Window.  Kinda cool that you could learn only one application no matter if you're tagging at home or work etc...
 - it's only £10 to license the full version.

URL is: [http://www.jthink.net/jaikoz/jsp/startup.jsp](http://www.jthink.net/jaikoz/jsp/startup.jsp)
I think it's worth a try if you're looking for a good MP3 manager/tagger

For the other features like smart playlists, or syncing files to your USB device, etc..., then you can use Amarok.  You just have to remember to tag in Jaikoz and not in Amarok, since Amarok doesn't sync its internal data with the ID3 tags.

---

### Post by flamboyant on 2007-10-27
> **LilYoda said:**
> ... Amarok doesn't sync its internal data with the ID3 tags.

excuse me, but what "internal data" are you talking about? do you mean it's possible in Amarok to edit track info in its database for files stored on read-only media [cd, dvd, etc]? if yes, i would be happy to know how

---

### Post by LilYoda on 2007-10-29
> **flamboyant said:**
> excuse me, but what "internal data" are you talking about? do you mean it's possible in Amarok to edit track info in its database for files stored on read-only media [cd, dvd, etc]? if yes, i would be happy to know how

That's not really what I meant.  I'm not sure if you could edit info on a track that is imported from a CD or DVD.  You can always try with right-click -> properties

What I meant was that if you edit an artist name or a track rating in amarok, it isn't updated in the ID3 tag in the file.

I have started writing small PHP scripts to do this function, but I'm far from finished.

---

### Post by flamboyant on 2007-10-29
> **LilYoda said:**
> That's not really what I meant.  I'm not sure if you could edit info on a track that is imported from a CD or DVD.  You can always try with right-click -> properties

What I meant was that if you edit an artist name or a track rating in amarok, it isn't updated in the ID3 tag in the file.

I have started writing small PHP scripts to do this function, but I'm far from finished.

as far as i remember, i was not able to edit tags of tracks from optical discs, but could do this with those from hard disk. as my music collection is mostly stored on discs, i dismissed amarok and now use prokyon3.

however, judging from your words, amarok always uses its database for editing and never writes to tags. that's contrary to my experience, but maybe i read the manual not thoroughly enough :)

---

### Post by LilYoda on 2008-02-09
FInally found a good organizer and tagger.  Jaikoz: [http://www.jthink.net/jaikoz/jsp/download/start.jsp](http://www.jthink.net/jaikoz/jsp/download/start.jsp)
I tried it for a bit, and finally bought it.  It's worth the $30 or so for the full license.

Quick tips on it, you should first analyze all the digital fingerprints of your files.  I have 5000 MP3s, it took a night for my AMD Athlon XP 3000 to do that (although the files were on an NFS share, so that might have slowed down the whole process)

Then,
 - go on each artist
 - use the auto correct
 - then auto-tag from music brainz
 - if a track was categorized in a wrong album, click on it, then "manual tag from music brainz" and select the correct album
 - then cluster CD, to make sure all files belonging to the same CD are using the same musicbrainz release
 - then rename the files according to the rules you defined in the options.  For me it's "Album Artist"/"Year - Album name"/"Artist - Album name - Track number - Title".  Settings are %H%Z%F - %B in the "Rename Folder from tags" preferences, and %A - %B - %D - %C in the "Rename File from Tags" preferences

It took me about a week of work in the evenings to correctly re-tag all 5000 files, using about 2 hours every evening, and 4 or 5 hours saturday and sunday.  But now it's done, and all players will have the correct name, release year, track name & number, artist and cover art.

Then it's time for MUZIK :guitar:

---

### Post by bamboo.7 on 2008-05-18
Dupe Music Matcher ([http://sourceforge.net/project/showfiles.php?group_id=148450](http://sourceforge.net/project/showfiles.php?group_id=148450)) Its a pretty nice little program. There is a GTK interface. You can also use it in a Terminal. Python Script.

---


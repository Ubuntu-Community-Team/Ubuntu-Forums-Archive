---
title: "Music File Sorter"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by toupeiro on 2007-07-29
Ok, here is the dilemma..

I have a music collection that I've been growing since 1994.  75% of this collection was created via programs like soundforge and various other ripping tools or conversion tools where I used source media (CD's, LP's Cassettes, and even 8-Track.)  The other 25 percent is downloaded material that was live and never resold, or a better digital download of a song I could not clean up off the original media with soundforge.

The ID3 tags on this collection are hit and miss, but most of the artist-song.extension naming is accurate.

I just don't believe I will ever have the time it would take to do 100% of sorting this collection myself, so I am looking for an application for linux that will:

1. Scan entire directory structure
2. identify partially completed ID3 tags, and fill in missing gaps from online database
3. once ID3 tag is filled in, move file into a new directory, create a directory for the artist, a directory for the album, write the file with a standard naming convention.
4. leave files it cannot verify the ID3 tag of from the filled in information or from the filename alone in its original file location.

From that point, I would become step 5 in manually verifying those songs that the application couldn't.

So far, I've played with "not to an extreme extent"

* AmaroK
* Tag Tool
* Banshee
* Cowbell
* Easytag
* GmusicBrowser
* Kyamo

and given each of these apps 5-10 minutes, none of them seemed as though they could do all four (or even the first three) steps indicated above.  I would probably be ecstatic with the first two if it could somehow give me a file list, or sort the files it was able to complete versus the ones it couldn't.

Cowbell looked the most promising until I tried to tag a full directory of music, and it memory leaked through all my physical and virtual ram and fell flat on its face and died.

If anyone has a recommendation for me to try, I would be most appreciative!

Thanks in advance!

---

### Post by bbzbryce on 2007-07-29
> **toupeiro said:**
> If anyone has a recommendation for me to try, I would be most appreciative!

I recommend Picard from MusicBrainz. It's not 100% automatic but it gives you whole album control and will place in folders however you wish.

[http://musicbrainz.org/doc/PicardTagger](http://musicbrainz.org/doc/PicardTagger)

I had problems with the picard package in the repos, but I was able to get their Picard-QT app to run without problems.

[http://musicbrainz.org/doc/PicardQt](http://musicbrainz.org/doc/PicardQt)

---


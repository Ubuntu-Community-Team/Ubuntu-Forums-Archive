---
title: "Clementine misses many music files in importing"
date: 2013-06-04
forum: Multimedia Software
---

### Post by monkeybrain2012 on 2013-06-04
Hi I use guayadeque as my music manager, but out of curiosity I am checking out clementine. I have a small music collection of about 6 G in ~/Music. When clementine scans my music folder it misses many files. They do show up in the "Files" panel in Music, but appending a song in Music which is missing from the library to the playlist has no effect. Rescaning library still missed these songs.Tried this in 12.04 and 13.04, the results were the same.

The formats are .ogg or mp3. guayadeque imports and plays all these files with no issue. I read in a forum where someone mentioned in passing that clementine doesn't play files with no metadata attached, is this true? Is there a way to work around this?

Thanks.

P.S. I am happy with guayadeque, just that I have multiple Ubuntu installations I don't mind trying something different.

---

### Post by SeijiSensei on 2013-06-05
If it's missing .mp3 files, make sure you installed kubuntu-restricted-extras.

I usually rip everything to FLAC, which Clementine has no problem with.

---

### Post by monkeybrain2012 on 2013-06-05
It is not kubuntu,it is Ubuntu and restricted-extras is installed Flac is ok, as are some mp3 and ogg, but for others clementine doesn't seem to see them (well they do show up in the Files tab but cannot import them to library or add them to playlist)

---

### Post by monkeybrain2012 on 2013-06-07
Ok, tried Amarok and the songs imported and played with no problem. I think clementine is a fork of Amarok?  So to recap, there are some songs that somehow clementine does not see when scanning my music library and while they show up under "File", right clicking and adding them to playlist has no effect. Other music managers such as Amarok and  guayadeque handle them just fine.

---

### Post by monkeybrain2012 on 2013-06-11
Bump!

---

### Post by SeijiSensei on 2013-06-11
Have you asked about this here: [http://code.google.com/p/clementine-player/](http://code.google.com/p/clementine-player/)

---

### Post by monkeybrain2012 on 2013-06-22
I have found a pattern. All these files that Clementine fails to recognize have ogg containers and flac codecs. Right clicking one and go to Properties > Audio  it typically looks like the first screenshot. These files are visible in the Files tab in Clementine though not imported into the Library and if you go to the Files tab and right click them and choose "edit track information" Clementine opens an editing window with all options greyed out (second screen shot) and all the information is shown as "unknown".

Any insight would be appreciated.

---


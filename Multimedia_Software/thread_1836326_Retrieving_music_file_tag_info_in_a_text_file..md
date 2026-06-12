---
title: "Retrieving music file tag info in a text file."
date: 2011-08-30
forum: Multimedia Software
---

### Post by cscj01 on 2011-08-30
I am creating jewel case inserts for a lot of CDs.  I would like to put the song title, artist, and playing time on the insert.  Every application I have looked at (puddletag, easytag, brasero, exaile, rhythmbox, quod libet, etc.) can create play lists but that output cannot be customized by choosing the tag information in the file.  Is there a way to do what I want without writing code to access the tag info?

---

### Post by nothingspecial on 2011-08-31
> **cscj01 said:**
> Is there a way to do what I want without writing code to access the tag info?

I can't think of one so here is some 'code'

```
soxi *.mp3 |  awk '/^Title|^Artist|^Duration/' | sed 's/ = .*$//g'
Duration       : 00:06:50.80
Title=Devil Eyes
Artist=Tim Buckley
Duration       : 00:06:32.78
Title=Get on Top
Artist=Tim Buckley
Duration       : 00:06:57.20
Title=Hong Kong Bar
Artist=Tim Buckley
Duration       : 00:04:20.31
Title=Make It Right
Artist=Tim Buckley
Duration       : 00:04:52.21
Title=Move with Me
Artist=Tim Buckley
Duration       : 00:03:21.98
Title=Nighthawkin'
Artist=Tim Buckley
Duration       : 00:06:47.83
Title=Sweet Surrender
Artist=Tim Buckley

```

---

### Post by cscj01 on 2011-08-31
Thanks for your response.  I did not know of the soxi command.  However, I think your code must be peculiar to mp3 files.  My files are all flac files.  When I ran your command exactly as given, some of the information was missing for some of the songs.  I suppose this is because some of the ID3 tag fields are empty.

I changed the command to the following```
soxi *.flac |  awk '/^Title|^Artist|^Duration/^Comment' | sed 's/ = .*$//g'
```and got all the information I wanted and a lot more besides.  Perhaps this is because flac files use a vorbis comment for their metadata, and I am seeing the vorbis comment tags as well as the ID3 tag information?


Also, if I substitute TITLE for Title, I get some of the titles I didn't get earlier, but some I did get, I no longer get.  Since I have additional tags that are in a vorbis comment but are not valid ID3 tags, I suppose I need to have only the vorbis comment and not the ID3 tags.

Is there a safe (without losing tag data) way I can make sure all the vorbis fields are populated and then remove the ID3 Tags other than brute force?  As examples, I have song titles in Title or in TITLE, but not both, artist in Artist or ARTIST, but not both, etc.

---

### Post by nothingspecial on 2011-08-31
It should be scriptable, but I haven't time now, the tools needed would be id3v2 and the vorbis tagger that I can't recall the name of.

That awk command
```

awk '/^Title|^Artist|^Duration/'
``` simply prints out the lines that start with those words. So if you just run ```
soxi *.flac
``` you will see everything available. Just add the lines to the awk bit that you want to see. So to catch Title and TITLE
```

soxi *.flac | awk '/^Title|^Artist|^Duration|^TITLE/' | sed 's/ = .*$//g'
```

The sed bit just removes the cruft fromn the end of the duration line.

---

### Post by cscj01 on 2011-09-15
I have one other question.  When using the command```
soxi *.flac |  awk '/^track|^title|^artist|^Duration/' | sed 's/ = .*$//g'
```and I have a tag with an & in it, that seems to stop the awk command for that file.  So, for example, if the fields are returned in the order of Duration, artist, title, track, which they are, and if the artist is something like "Johnny & the Hurricanes", the awk command for that file returns the Duration value but no other.  It picks up with the next file.

If I use```
soxi *.flac
```all the information is returned.

So how do I deal with embedded &s in the fields I am returning?

---

### Post by cscj01 on 2011-10-27
Bump

---

### Post by qyot27 on 2011-10-27
An easier solution would probably be to use [MediaInfo](http://mediainfo.sourceforge.net/en/Download) with a custom template.  If all you want are the Track, Title, Artist, and Duration, then that can be easily done.

```
sudo add-apt-repository ppa:shiki/mediainfo
sudo apt-get update
sudo apt-get install mediainfo
```

The template file (save it somewhere and with a name you'll remember):
```
General;%Track/Position%\n%Title%\n%Performer%\n%Duration/String3%\n
```

And finally:
```
mediainfo --inform=file:///path/to/template.txt filename.flac
```

To show what the output looks like:
```
mediainfo --inform=file://template.txt "The Verve Pipe - The Freshmen.flac"
7
The Freshmen
The Verve Pipe
00:04:30.293
```
Or, instead of using new lines (\n) in the template, you could use tab characters and have the information all on one line.

MediaInfo has a ton of other parameters that can be used to gather all sorts of information.  Use the --info-parameter option to have it list them all (or better, have it dump the listing out to a file and then read through it in gedit or something).

---


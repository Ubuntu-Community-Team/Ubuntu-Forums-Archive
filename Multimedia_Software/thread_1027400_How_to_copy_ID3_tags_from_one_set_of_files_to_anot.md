---
title: "How to copy ID3 tags from one set of files to another?"
date: 2009-01-01
forum: Multimedia Software
---

### Post by tawmas on 2009-01-01
Hello!

A relevant part of my music collection is made of AAC files I ripped from CDs long time ago, using iTunes on Windows (ugh!), with some OGG files ripped more recently. I want to move forward to lossless (and open) formats, i.e. FLAC.

But, while I'm ready to re-rip all my music from the original CDs, I'm not so ready to undergo the pain to manually tag all that music once more. I'd really like to be able to copy the tags from the old files to the new files, instead.

I looked at the feaures of Rythmbox, Banshee and Exfalso, but couldn't find anything useful to the purpose. I googled for "copy ID3 tags", "move ID3 tags", and some more variations, but found nothing helpful.

I believe there's no single tool that can do the trick for me. I'm willful to use a set of tools (preferably in a scriptable way, but manually is probably still easier than entering all that data) or some other workaround, but I'm unable to find one all on my own.

I'd be really grateful if someone can please nudge me to the right direction or share a tip.

---

### Post by jimbo99 on 2009-01-01
I do not think I've ever heard that request before. Unusual but you never know. The key to ripping those is to use a program to look up the album to automatically fill the id3 tag info. Ripperx is a crude program but it works. 

Id3 tags (version 1.x) are just small pieces of text appended to the end of the mp3. Version 2.x are much more sophisticated and cumbersome. 

You would need a program that matches the files by name which would be difficult unless you already tagged them. Sort of a catch 22. 

If you don't want to use ripperx and the program you use to rip them doesn't have cddb support then use Amarok 1.x to assist in retagging. Add one tagged file then the non tagged from your new rips and copy the tag info using features of the playlist itself. Even so naming the files will still be tedious. And figuring out how to mass tag in amarok is going to take some effort.

---

### Post by tawmas on 2009-01-01
Thanks for your reply.

I don't know Ripper X (I've seen it mentioned in these forums today for the first time), but the ripper I use (Gnome's default Sound-Juicer) does support CDDB. Problem is, we're talking about classical music, which means the track information available through CDDB, for the most part, ranges from inexistent to useless crap. I don't know if this is the rule for all classical music, but it is true for most of my albums.

Unfortunately, I did most of my tagging in iTunes, which doesn't provide (or didn't provide at the time, don't know if anything changed, but I don't believe it) any means to contribute back to CDDB.

So, the only way I can benefit from CDDB is if I get to export to CDDB the tags from the existing files. I don't know if it can be done, but I'd do that happily, as it would also help others, I think.

A little more googling also revealed the existence of a command line utility named id3cp that copies ID3 tags from one file to another, which seems to be available in Jaunty through the libid3-3.8.3-dev package.

This is also worth investigating. If this works as advertised, a possible workflow would be:

[LIST=1]
[*]Rip to FLAC
[*]Use Exfalso mass renaming to give silly names to the old and new files (like track 1, track 2 etc.)
[*]use id3cp to copy the ID3 tags
[*]Use Exfalso mass renaming to rename the new files according to the tags
[*]Get rid of the old files :-)
[/LIST]

Tedious, but probably less so than retyping all the titles by hand.

I'd still prefer to export my tags to CDDB if at all doable.

---

### Post by my_key on 2009-01-01
Can't you use [musicbrainz]("http://en.wikipedia.org/wiki/MusicBrainz") to add all the files to the musicbrainz database (they have seperate programs to do this so you don't have to use itunes)? And then re-rip with sound juicer which supports musicbrainz.

---

### Post by my_key on 2009-01-01
Edit: the info I tried to give in this post is no longer applicable. Use musicbraiz picard instead.

---

### Post by tawmas on 2009-01-01
> **my_key said:**
> Can't you use [musicbrainz]("http://en.wikipedia.org/wiki/MusicBrainz") to add all the files to the musicbrainz database (they have seperate programs to do this so you don't have to use itunes)? And then re-rip with sound juicer which supports musicbrainz.

That looks like a good idea. I didn't know about musicbrainz other than Sound Juicer keeps telling me that my CDs aren't found there.

I downloaded Picard and I had a pleasant surprise. The CDs aren't there, but the tracks are, and the metadata looks quite good too! So I could probably just re-rip with the crappy tags from CDDB and then do a mass retagging through Picard...

---

### Post by my_key on 2009-01-02
There's also a way to upload your own tags to musicbrainz, so then you're sure it has all the right tags. Maybe it'll even include the cd name, that way you're settled even when using soundjuicer. It's been a while since I've used it, but check into that upload feature: [http://musicbrainz.org/doc/HowToAddDiscIDs](http://musicbrainz.org/doc/HowToAddDiscIDs)

---

### Post by Papabonk on 2009-02-07
You might want to take a look at Jaikoz Audio Tagger (also found on musicbrainz). If acoustic ID does not do it for you, try the following (This is how I worked around my tag issue): I put both tagged and untagged files in same folder, activated view pane, sorted by playing time under view audio. The tracks line up in the same order in the tag editor window as well. Then it's a matter of copy and paste the info. (Drag and drop works...) Shareware version saves 20 files at a time, needs restart for next 20. Still a bit of "mouse work" but no re-typing. Hope this helps...

---

### Post by x33a on 2009-02-07
i use mp3tag under wine and using it i can simply select a file (or any number of files), and select copy tags, then select untagged files or wrongly tagged files and select paste tags on those files. every part of the tag including the album art gets copied like this.

---

### Post by Papabonk on 2009-02-07
Then again, issue might have been resolved by now...Sorry, just looked at the posting date.

---

### Post by tawmas on 2009-02-08
> **Papabonk said:**
> Then again, issue might have been resolved by now...Sorry, just looked at the posting date.

Well, I used Picard to handle the largest chunk of problem CDs (all 88 othem), but I still have more music to reimport. Suggestions are always welcome.

---

### Post by flapane on 2009-12-09
Well, you can use id3cp, as AAC DOESN'T USE id3 but closed source mp4 tags.
I am looking for a SIMILAR solution, as I reripped my collection, and want to stick from mp3 to aac.
I am trying to set up a shell script that reads id3 data and write it into aac files.

---


---
title: "id3(v1?) Tag problem"
date: 2009-10-31
forum: Multimedia Software
---

### Post by ackey on 2009-10-31
I decided to clean up my mp3 tags - rhythmbox has known issues if multiple tags are on a file.  Some are fixed, and some I can't.  I've tried a bunch of tricks and now I'm out of ideas.  I've already run batch script to kill id3v1 tags and APE tags.

I have a file that I've used exfalso and easytag to remove the tags (except name and track number). I look in rhythmbox and it still has genre/artist/album.

In terminal I see:
```
$ id3v2 -l Boomerang\ Love.mp3 
Boomerang Love.mp3: No ID3 tag
$ eyeD3 Boomerang\ Love.mp3 

Boomerang Love.mp3	[ 4.87 MB ]
-------------------------------------------------------------------------------
Time: 05:19	MPEG1, Layer III	[ 128 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
ID3 v2.4:
title: Boomerang Love		artist: 
album: 		year: None
track: 7		
$ eyeD3 -1 Boomerang\ Love.mp3 

Boomerang Love.mp3	[ 4.87 MB ]
-------------------------------------------------------------------------------
Time: 05:19	MPEG1, Layer III	[ 128 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
No ID3 v1.x tag found!
```

Now, the last one is the strangest since the behaviour mimics an id3v1 being present.  If I check the end:

```
$ strings Boomerang\ Love.mp3 | tail
^!	,
m2>j
_@i<
f@Y]
`A*HZ 
TAGBoomerang Love
Jimmy Buffett
Off To See The Lizard
APETAGEX
APETAGEX

```

Yep, that looks like an id3v1 tag, and since there is no genre bit it would show up as "other".  If I try to change the metadata in rhythmbox eyeD3 will recognize it as the id3v2.4 data, but then rhythmbox starts showing the data from the end of the file - except sometimes it will not change one of the fields.

In Summary:
It looks like some files have id3v1 tags
These files confuse rhythmbox
No (other) program will recognize that the tag is there to get rid of it

Suggestions or ideas?  I can post the whole file here if it would help.  There are variations on this problem in many other files, but the pattern seems to be that rhythmbox won't let me edit properties if anything appears at the end.

I'm using ubuntu 9.10 on a custom desktop.  Rhythmbox version is 0.12.5

---


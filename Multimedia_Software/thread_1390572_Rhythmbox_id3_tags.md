---
title: "Rhythmbox id3 tags"
date: 2010-01-25
forum: Multimedia Software
---

### Post by linusr on 2010-01-25
Few of songs added to rhythmbox have phantom tags :confused:

8 songs but it's annoying...

tried editing using easy tag
tried removing tags using eyeD3

but every add songs back to library,get added with old tags

is there any cache?

---

### Post by UnrealMiniMe on 2010-01-25
Heh...I'm familiar with this problem, but I haven't found any easy solutions yet, so fixing it can be a bit painful.  The issue here is that your "problem files" have some legacy tags somewhere in them, and Rhythmbox is reading them instead of the tags you're wanting it to read (which are probably ID3v2.3 or ID3v2.4).  In my experience, the offending tags have typically been APE tags, old ID3 tags, or Quicktime movie tags (yes, you read that right, and I'm still talking about mp3 files ;)).

My first suggestion is to resave your problem files using Musicbrainz Picard, while having its options set to remove APE tags.  My second suggestion is to play around in VBRFix and try to remove the extraneous tags using that.  (The repositories have the command line version, but [here's the GUI version]("http://home.gna.org/vbrfix/")...you'll have to compile it yourself though, since there's no package.  The above link has several versions available that were released in 2009, but apparently there was an older version (perhaps a branch?) somewhere that had some bugs in it.  Some guy made a patched up Windows version in 2008 that fixed the bugs present in that older version, and I'm not sure if they were fixed for the QT releases above or not.  Here's the relevant thread, and in any case, be careful with your files:  [http://www.hydrogenaudio.org/forums/index.php?showtopic=67076](http://www.hydrogenaudio.org/forums/index.php?showtopic=67076))

I've had mixed luck with both of the above methods.  When all else fails, I've literally gone into my mp3 files with the GHex hex editor and manually removed the offending tags. ;)  If it comes to that, you'll be able to locate them in the file by searching for a text phrase from the "wrong" tags.  AFAIK, Rhythmbox displays the last set of tags read in by GStreamer, so the offending tags will be located after the correct ones in the file.  You might want to be careful not to accidentally cut into and corrupt mp3 data frames (which typically start with the bytes FF FB), but even if you do, you probably won't hear any audio artifacts, since the frames are so short.  You can always use VBRFix again to remove corrupt frames, too.  In any case, I suggest creating backup files before playing around in a hex editor.

I made a few post about this issue on another forum about a year ago, so I'll link to the appropriate page in case you find any of the information helpful:
[http://ocremix.org/forums/showthread.php?t=20433&page=5](http://ocremix.org/forums/showthread.php?t=20433&page=5)

(EDIT:  I should mention that I made this whole post under the assumption you're dealing with mp3 files.  If your problem files are ogg's or m4a's, I'm not sure how much of the above is still applicable.)

---

### Post by linusr on 2010-01-25
Many Thanks @UnrealMiniMe

APE tags were the problem...

Used GHex, at the end of file I could see APETAGEX and ID3 tags were at the beginning of the file..

deleting contents within APETAGEX solved the problem :)

Really hope rhythmbox gets better ID3 tag support

---

### Post by UnrealMiniMe on 2010-01-25
> **linusr said:**
> Many Thanks @UnrealMiniMe

APE tags were the problem...

Used GHex, at the end of file I could see APETAGEX and ID3 tags were at the beginning of the file..

deleting contents within APETAGEX solved the problem :)

Really hope rhythmbox gets better ID3 tag support

Glad to help! :)  You're right though about ID3 tag support...I think the problem might be in GStreamer, but in any case it would be nice for Rhythmbox/GStreamer to give ID3v2 tags priority by default.

---

### Post by Richard85 on 2010-06-25
I downloaded musicbrainz picard because I'm having this same issue with rhythmbox/amarok/exaile but for whatever reason I cannot write tags in musicbrainz.
 I changed the settings to remove apetags, then I load in the songs, and when I try to save, nothing happens. Am I missing something?
 Any help would be much appreciated!

---

### Post by cenyongh on 2011-02-04
i get the same problem, and i write a python script to recursively remove the APE tag from the mp3 file inside the dir i specified in the python code's 'BASE_DIR' value, and this seem can help to solve the problem.

---

### Post by nealmcb on 2012-08-08
Thanks for the cleanup_mp3tag.py python program, cenyongh - good idea.  A warning though - it seems to just truncate the file after the first place it finds "APETAGEX".  That won't work if there are other good tags after that, or if an earlier comment or tag has that text in it, or even if by chance the mp3 data happens to match that string, which I presume is possible in a binary file like that.  So do back things up an check the files carefully afterwards.  Better to add some more logic to know the length of the tag, or how to find the next tag that isn't APE, etc.

---


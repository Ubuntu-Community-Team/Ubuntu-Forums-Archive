---
title: "mp3splt performer tags from cue"
date: 2009-05-17
forum: Multimedia Software
---

### Post by PlaneTeeR on 2009-05-17
Hello,

I'm using mp3splt to split my radio shows with the cue option (-c). But since i have downloaded the newest version (so not the one from the ubuntu-repository) i have a problem with the tags.

mp3splt puts the cd-artist in the mp3-files, but for each song i have a different artist. How can I manage to do this. In the man pages there's no option for this. See the example below.

Thanks

Example cue file: 

PERFORMER "Tiësto"

TITLE "Club Life 111 (2009-05-15) (Hour 1) [TALiON]"

FILE "01-tiesto_-_club_life_111-cable-05-15-2009-talion.mp3" MP3

  TRACK 01 AUDIO

    PERFORMER "Serge Devant featuring Hadley"

    TITLE "Addicted"

    INDEX 01 00:00:00

The first MP3 gets Tiësto as artist, while it should be "Serge Devan...."

---

### Post by optimix on 2009-05-20
Hello :)

What version are you using ?

Type 
```
mp3splt -v
```

Also, please post the complete output of your command.

---

### Post by ukblacknight on 2010-07-25
Hey, sorry for bringing back an old thread, but did you ever solve this?  I'm trying to do the same thing, mp3splt keeps writing "VA" as the track artist, even though the .cue file has separate artists for each track.

---

### Post by optimix on 2010-07-25
ukblacknight, can you send me a sample cue file, what you want to obtain and what you actually obtain ? If you don't want to post it here, send it to me at [email]io_fx@yahoo.fr[/email]

Here is what I have using my latest development version on the first posted sample :


$ ./mp3splt -q -c test.cue songs/La_Verue__Today.mp3 -d output
 Processing file 'songs/La_Verue__Today.mp3' ...
 reading informations from CUE file test.cue ...

  Artist: Tiësto
  Album: Club Life 111 (2009-05-15) (Hour 1) [TALiON]
  Tracks: 1

 cue file processed
 info: file matches the plugin 'mp3 (libmad)'
 info: found Xing or Info header. Switching to frame mode...
 info: MPEG 1 Layer 3 - 44100 Hz - Joint Stereo - FRAME MODE - Total time: 4m.05s
 info: starting normal split
   File "output/Serge Devant featuring Hadley - 1 - Addicted.mp3" created
 Processed 9402 frames - Sync errors: 0
 file split (EOF)

---

### Post by ukblacknight on 2010-07-25
That was a quick reply! :D

The sample .cue file is listed below:

```
PERFORMER "VA"
TITLE "Trance Nation__Mixed By Andy Moor-2CD"
FILE "02-va-trance_nation__mixed_by_andy_moor__disc2.mp3" MP3
  TRACK 15 AUDIO
    TITLE "Closer"
    PERFORMER "Susana Feat. Omnia & The Blizzard"
    INDEX 01 00:00:00
  TRACK 16 AUDIO
    TITLE "She Moves"
    PERFORMER "Andy Moor Feat. Carrie Skipper"
    INDEX 01 07:12:51
  TRACK 17 AUDIO
    TITLE "Live Forever"
    PERFORMER "Lange Feat. Emma Hewitt"
    INDEX 01 13:59:48
  TRACK 18 AUDIO
    TITLE "Sique"
    PERFORMER "Mike Shiver Vs Fandy"
    INDEX 01 19:51:69
  TRACK 19 AUDIO
    TITLE "Blackboard"
    PERFORMER "Mark Eteson"
    INDEX 01 23:43:05
  TRACK 20 AUDIO
    TITLE "Staring At The Sea (Masoud Remix)"
    PERFORMER "DJ Eco Presents Pacheco"
    INDEX 01 28:12:51
  TRACK 21 AUDIO
    TITLE "Monzen (Stoneface & Terminal Remix)"
    PERFORMER "Yenn"
    INDEX 01 33:13:46
  TRACK 22 AUDIO
    TITLE "Far Away (Ronski Speed Remix)"
    PERFORMER "Nitrous Oxide Feat. Aneym"
    INDEX 01 37:00:00
  TRACK 23 AUDIO
    TITLE "Angel (Mark Eteson & Ben Nicky Remix)"
    PERFORMER "Guiseppe Ottaviani Feat. Faith"
    INDEX 01 42:39:19
  TRACK 24 AUDIO
    TITLE "Sun In The Winter"
    PERFORMER "Max Graham Feat. Neev Kennedy"
    INDEX 01 47:07:41
  TRACK 25 AUDIO
    TITLE "Arctic Kiss (Andy Blueman Remix)"
    PERFORMER "Motion Child And Will Holland feat Tiff Lacey"
    INDEX 01 52:03:61
  TRACK 26 AUDIO
    TITLE "People (Rafael Frost Remix)"
    PERFORMER "DJ Eco"
    INDEX 01 57:27:72
  TRACK 27 AUDIO
    TITLE "Remember Me"
    PERFORMER "Ben Preston Feat. Susie"
    INDEX 01 63:10:71
  TRACK 28 AUDIO
    TITLE "Sapphire"
    PERFORMER "Ben Gold"
    INDEX 01 68:18:65
  TRACK 29 AUDIO
    TITLE "Flashback"
    PERFORMER "Rafael Frost"
    INDEX 01 72:58:63
```

Is what's happening, is that each track is being given an Artist tag of "VA", which is the CD Performer, rather than the value of the Track Performer.  So, for Track 15, the split file looks like this at present:

**Artist:** VA
**Title:** Closer

However, I'm after it being:

**Artist:** Susana Feat. Omnia & The Blizzard
**Title:** Closer

Thanks!

---

### Post by optimix on 2010-07-25
It works as you expect with my development version.
Unfortunately, Debian and Ubuntu packages are a bit old.

Can you try uninstalling libmp3splt*, mp3splt and mp3splt-gtk of your Ubuntu packages and install:
 - either the latest release: [http://mp3splt.sourceforge.net/mp3splt_page/downloads.php](http://mp3splt.sourceforge.net/mp3splt_page/downloads.php)
 - either the testing development version: [http://ioalex.net/testing_downloads/](http://ioalex.net/testing_downloads/)

-- 
Alex

---

### Post by ukblacknight on 2010-07-25
Brilliant!  That's done it!  Thanks very much!

---

### Post by optimix on 2010-07-25
Cool.
Please repost here and/or mail me if you have any other issues.
-- 
Alex

---

### Post by Jerommel on 2011-03-31
[COLOR=SlateGray]Damn, damn, damn...
I used to install and run mp3splt with no problems, but now (10.04) I can't seem to get it working AT ALL.
I'm probably doing something wrong, but the installer tells me that it's already installed...
WTF.... I don't get it...
I need it again !

I miss my casstte tapes.... (nâh, not really...)

[COLOR=Black]De-installed all bits, reinstalled the complete thing from the software center.
Imagine my surprise.[/COLOR]
[/COLOR]

---

### Post by optimix on 2011-04-03
Try uninstalling all the packages starting with "libmp3splt" and "mp3splt" before re-installing.

---

